


its like renting computers in the cloud


# Play 1

trying to deploy a node server in EC2 instance

start the docker container with

```
docker run -d --name floci -p 4566:4566 -e FLOCI_SERVICES_EC2_ENABLED=true -e FLOCI_SERVICES_EC2_MOCK=false -e FLOCI_SERVICES_EC2_IMDS_PORT=9169 -e FLOCI_SERVICES_EC2_SSH_PORT_RANGE_START=2200 -e FLOCI_SERVICES_EC2_SSH_PORT_RANGE_END=2299 -v //var/run/docker.sock:/var/run/docker.sock --privileged ` floci/floci:latest
```




```
aws --endpoint-url=http://localhost:4566 ec2 create-security-group `
    --group-name my-app-sg `
    --description "Security group for Hello World app" 

aws --endpoint-url=http://localhost:4566 ec2 authorize-security-group-ingress `
    --group-id $SG_ID `
    --protocol tcp `
    --port 22 `
    --cidr 0.0.0.0/0

aws --endpoint-url=http://localhost:4566 ec2 authorize-security-group-ingress `
    --group-id $SG_ID `
    --protocol tcp `
    --port 3000 `
    --cidr 0.0.0.0/0

```

```

aws --endpoint-url=http://localhost:4566 ec2 create-key-pair `
    --key-name my-key
```

```

aws --endpoint-url=http://localhost:4566 ec2 run-instances `
    --image-id ami-12345678 `
    --instance-type t2.micro `
    --key-name my-key `
    --security-group-ids $SG_ID `
    --user-data file://userdata.sh `
    --count 1
    
```


```
aws --endpoint-url=http://localhost:4566 ec2 wait instance-running `
        --instance-ids i-d9f33dfcae2051cba
```

### Blocker 1: The Docker Daemon Can't Start Inside the EC2 Instance

- **What We Tried:** We logged into the EC2 instance (via `docker exec`) and ran `dockerd` or `systemctl start docker` to start the Docker service.
    
- **The Error:** `failed to mount overlay: operation not permitted` and `iptables: Permission denied`.
    
- **Why It Happened:**
    
    - By default, Docker containers are heavily restricted for security. They don't have permission to perform low-level system operations.
        
    - To run a Docker daemon, you need to mount filesystems (`overlay`), configure network rules (`iptables`), and create network interfaces. Our EC2 container lacked these "Linux capabilities" (`CAP_SYS_ADMIN`, `CAP_NET_ADMIN`).
        
    - Even though we started Floci with `--privileged`, **privilege is not hereditary**. The EC2 container Floci created was a _standard, unprivileged container_.
        
- **The Fix:** We **stopped trying to run a Docker daemon inside EC2**. Instead, we changed our approach.

---

### Blocker 2: The "Docker-Out-Of-Docker" Approach vs. "Docker-In-Docker"

- **What We Did:** Instead of fighting to run a Docker daemon _inside_ the EC2 container, we realized we don't need to. Our goal was just to run `docker build` and `docker run` commands _from_ the EC2 container.
    
- **The Solution (The Paradigm Shift):** We decided to use the **host's Docker daemon**.
    
    - We created a _new_ container to act as our EC2 instance (`ec2-working`).
        
    - When we created it, we used the flag `-v /var/run/docker.sock:/var/run/docker.sock`.
        
    - This **mounted the host's Docker socket** inside the EC2 container.
        
    - Now, any `docker` command executed inside the EC2 container is sent directly to the host's Docker daemon to be executed. This is called **Docker-Out-Of-Docker (DooD)**.
        
- **Why This Works:** The EC2 container is now just a _client_ sending commands to the host's already-running daemon. No new daemon needs to start.
    

---

### Blocker 3: The Docker Client Was Missing in the EC2 Container

- **What We Did:** After creating the new `ec2-working` container, we immediately tried `docker --version`.
    
- **The Error:** `exec: "docker": executable file not found in $PATH`.
    
- **Why It Happened:** The Amazon Linux 2023 image we used is a minimal base OS. It doesn't come with Docker pre-installed. The socket was mounted, but there was no "client" program (`docker` CLI) to talk to it.
    
- **The Fix:** We installed the Docker client inside the EC2 container using `docker exec ec2-working dnf install -y docker`.
    
    - This installed the CLI tool, which looks for `unix:///var/run/docker.sock` by default. Since we mounted the host's socket, the client was perfectly configured out of the box.
        

---

### Blocker 4: Port Conflicts (The "Already Allocated" Error)

- **What We Tried:** We ran `docker exec ec2-working docker run -d -p 3000:3000 --name my-app hello-app`.
    
- **The Error:** `Bind for 0.0.0.0:3000 failed: port is already allocated`.
    
- **Why It Happened:** We had a layered port mapping conflict. Earlier, when we created the `ec2-working` container, we exposed port 3000 to the host using `-p 3000:3000`. Port 3000 on your Windows machine was already being used by the `ec2-working` container itself.
    
- **The Fix:**
    
    - **Option A (The Clean Fix):** We recreated the `ec2-working` container _without_ exposing port 3000 to the host (`-p 2200:22` only). This freed up port 3000 on the host.
        
- **Why This Works:** The `ec2-working` container doesn't need to expose its own port 3000. It's just a "VM" acting as a middleman. The app container (`my-app`) is the one that needs to expose the port to the host.

---

### Understanding 1

- in our host machine we have docker client and docker daemon , we created a image inside it and installed docker in it , that means it will have a docker client and docker daemon inside it right. but we tried to use docker daemon of the host machine by mounting it , but while in a real ec2 instance remotely we will install docker in it and docker daemon will be in it then we dont have to mount anything it will use its dockerd itself
#### Architecture Comparison

###### 1 . Our Local Setup (Floci + Docker-Out-of-Docker)
```
┌─────────────────────────────────────────────────────────────────┐
│                    YOUR WINDOWS HOST                           │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │              HOST DOCKER DAEMON (Actual)                │   │
│  │  - Runs on Windows                                      │   │
│  │  - Creates ALL containers                               │   │
│  │  - Socket: /var/run/docker.sock                        │   │
│  └─────────────────────────────────────────────────────────┘   │
│                     ▲                                          │
│                     │ Socket Mounted! (-v)                     │
│                     │                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │         EC2 CONTAINER (Floci-emulated)                 │   │
│  │  ┌──────────────────────────────────────────────────┐  │   │
│  │  │  Docker Client (CLI) only!                       │  │   │
│  │  │  - No Docker daemon running                      │  │   │
│  │  │  - Sends commands to HOST via socket            │  │   │
│  │  └──────────────────────────────────────────────────┘  │   │
│  └─────────────────────────────────────────────────────────┘   │
│                     │                                          │
│                     │ Commands executed by HOST Daemon        │
│                     ▼                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │         MY-APP CONTAINER (Running on HOST!)            │   │
│  │  - Created by host Docker                              │   │
│  └─────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

###### 2. Real AWS EC2 (The Correct Way)

```
┌─────────────────────────────────────────────────────────────────┐
│                    REAL AWS EC2 INSTANCE                       │
│                    (Running on AWS Hardware)                   │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │              EC2 DOCKER DAEMON (Local)                  │   │
│  │  - Runs directly on EC2                                 │   │
│  │  - Has full permissions (runs as root)                  │   │
│  │  - Socket: /var/run/docker.sock                        │   │
│  │  - Is the actual daemon!                               │   │
│  └─────────────────────────────────────────────────────────┘   │
│                     ▲                                          │
│                     │ Local Unix Socket                        │
│                     │                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │         EC2 DOCKER CLIENT                               │   │
│  │  - Installed with Docker package                         │   │
│  │  - Talks to local daemon via socket                     │   │
│  │  - No socket mounting needed!                           │   │
│  └─────────────────────────────────────────────────────────┘   │
│                     │                                          │
│                     │ docker run                              │
│                     ▼                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │         MY-APP CONTAINER (Running on EC2!)              │   │
│  │  - Created by EC2's own Docker daemon                   │   │
│  └─────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```


### Understanding 2

###### What We Tried (Failed)
```
┌─────────────────────────────────────────────────────────────────┐
│                    YOUR WINDOWS HOST                           │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │              HOST DOCKER DAEMON (ONE DAEMON)            │   │
│  │  - This is the ONLY Docker daemon                       │   │
│  │  - Manages ALL containers on the host                   │   │
│  │  - Tracks ALL port allocations!                         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                     ▲                                          │
│                     │ Socket mounted                           │
│                     │                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │         EC2 CONTAINER (floci-ec2-xxx)                  │   │
│  │  - Wants to expose PORT 3000                           │   │
│  │  - docker run -p 3000:3000                            │   │
│  │  - Sends command to HOST daemon                        │   │
│  │  - HOST daemon says: "PORT 3000 ALREADY ALLOCATED!"   │   │
│  │                                                         │   │
│  │  ┌──────────────────────────────────────────────────┐  │   │
│  │  │  But wait... EC2 itself already has PORT 3000   │  │   │
│  │  │  allocated? No, EC2 is just a container!        │  │   │
│  │  │  The HOST daemon sees the conflict! ❌          │  │   │
│  │  └──────────────────────────────────────────────────┘  │   │
│  └─────────────────────────────────────────────────────────┘   │
│                     │                                          │
│                     │ Can't allocate port 3000! ❌             │
│                     ▼                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │         MY-APP CONTAINER (Never created!)              │   │
│  │  - Failed to start because port 3000 was taken         │   │
│  └─────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

###### If EC2 had its OWN Docker daemon:

```
┌─────────────────────────────────────────────────────────────────┐
│                    YOUR WINDOWS HOST                           │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │          HOST DOCKER DAEMON (#1)                        │   │
│  │  - Manages EC2 container only                           │   │
│  │  - Port 2200:22 (SSH) mapping                           │   │
│  │  - Port 3000? No, that's managed by EC2's daemon!     │   │
│  └─────────────────────────────────────────────────────────┘   │
│                     │                                          │
│                     │ Creates EC2 container                    │
│                     ▼                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │         EC2 CONTAINER (Floci)                           │   │
│  │  ┌──────────────────────────────────────────────────┐  │   │
│  │  │      EC2 DOCKER DAEMON (#2 - INDEPENDENT!)      │  │   │
│  │  │  - Runs INSIDE the EC2 container                 │  │   │
│  │  │  - Has its OWN port space!                       │  │   │
│  │  │  - Manages app containers                        │  │   │
│  │  └──────────────────────────────────────────────────┘  │   │
│  │                     │                                   │   │
│  │                     │ docker run -p 3000:3000          │   │
│  │                     ▼                                   │   │
│  │  ┌──────────────────────────────────────────────────┐  │   │
│  │  │         MY-APP CONTAINER                         │  │   │
│  │  │  - Runs inside EC2                               │  │   │
│  │  │  - Port 3000 (internal) exposed                  │  │   │
│  │  │  - EC2's daemon manages this port                │  │   │
│  │  └──────────────────────────────────────────────────┘  │   │
│  └─────────────────────────────────────────────────────────┘   │
│                     │                                          │
│                     │ Need to expose EC2's port 3000 to host  │
│                     ▼                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │         HOST DOCKER DAEMON (#1)                        │   │
│  │  - Maps EC2 container port 3000 → Host port 3000     │   │
│  │  - This is a DIFFERENT mapping! ✅                    │   │
│  └─────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```


#### References

`create-security-group`

```
aws --endpoint-url=http://localhost:4566 ec2 create-security-group `
    --group-name my-app-sg `
    --description "Security group for Hello World app"
```

`authorize-security-group-ingress`

```
aws --endpoint-url=http://localhost:4566 ec2 authorize-security-group-ingress \
    --group-id sg-12345678 \
    --protocol tcp \
    --port 22 \
    --cidr 0.0.0.0/0
```


`create-key-pair`

```
aws --endpoint-url=http://localhost:4566 ec2 create-key-pair \
    --key-name my-key \
    --query 'KeyMaterial' \
    --output text > my-key.pem
```

`run-instances`

```
aws --endpoint-url=http://localhost:4566 ec2 run-instances \
    --image-id ami-12345678 \
    --instance-type t2.micro \
    --key-name my-key \
    --security-group-ids sg-12345678 \
    --user-data file://userdata.sh \
    --count 1
```


`describe-instances`

```
aws --endpoint-url=http://localhost:4566 ec2 describe-instances \
    --instance-ids i-abc123def456
```

``
`wait instance-running`

```
aws --endpoint-url=http://localhost:4566 ec2 wait instance-running \
    --instance-ids i-abc123def456
```

`terminate-instances`

```
aws --endpoint-url=http://localhost:4566 ec2 terminate-instances \
    --instance-ids i-abc123def456
```

`delete-security-group`

```
aws --endpoint-url=http://localhost:4566 ec2 delete-security-group \
    --group-id sg-12345678
```


# Play 2


create seperate security groups for web and ssh and allow 22 and 80 ports

Create UserData script for the instances
```

@'
#!/bin/bash
# Log everything
exec > /var/log/userdata.log 2>&1
set -x

echo "=== UserData started at $(date) ==="

# Install Python
yum update -y
yum install -y python3

mkdir -p /app
cat > /app/index.html << EOF
<html><body>
<h1>Hello from EC2!</h1>
<p>Hostname: \$(hostname)</p>
<p>Instance ID: \$(curl -s http://169.254.169.254/latest/meta-data/instance-id)</p>
</body></html>
EOF

cd /app
python3 -m http.server 80 &

echo "=== Web server started at $(date) ==="

tail -f /dev/null
'@ | Out-File -FilePath userdata.sh -Encoding ASCII
```

```
$userDataBase64 = [Convert]::ToBase64String([System.Text.Encoding]::UTF8.GetBytes((Get-Content -Path userdata.sh -Raw)))
```

```
@"
{
    "ImageId": "ami-12345678",
    "InstanceType": "t2.micro",
    "KeyName": "my-key",
    "SecurityGroupIds": ["$WEB_SG_ID", "$SSH_SG_ID"],
    "UserData": "$userDataBase64"
}
"@ | Out-File -FilePath launch-template.json -Encoding ASCII
```

```
$LAUNCH_TEMPLATE_ID = aws --endpoint-url=http://localhost:4566 ec2 create-launch-template `
    --launch-template-name my-app-template `
    --launch-template-data file://launch-template.json `
    --query 'LaunchTemplate.LaunchTemplateId' `
    --output text
```

```
$VPC_ID = aws --endpoint-url=http://localhost:4566 ec2 describe-vpcs --query 'Vpcs[0].VpcId' --output text
```

```
$SUBNET_ID1 = aws --endpoint-url=http://localhost:4566 ec2 describe-subnets --query 'Subnets[0].SubnetId' --output text
```

autoscaling group manages autoscaling

```
aws --endpoint-url=http://localhost:4566 autoscaling create-auto-scaling-group `
    --auto-scaling-group-name my-app-asg `
    --launch-template "LaunchTemplateId=$LAUNCH_TEMPLATE_ID" `
    --min-size 2 `
    --max-size 5 `
    --desired-capacity 2 `
    --availability-zones "us-east-1a" "us-east-1b"
    
```
	
```
$LB_ARN = aws --endpoint-url=http://localhost:4566 elbv2 create-load-balancer `
    --name my-app-lb `
    --subnets $SUBNET_ID1 $SUBNET_ID2  `
    --security-groups $LB_SG_ID `
    --query 'LoadBalancers[0].LoadBalancerArn' `
    --output text
```

```
aws --endpoint-url=http://localhost:4566 autoscaling attach-load-balancer-target-groups `
    --auto-scaling-group-name my-app-asg `
    --target-group-arns $TG_ARN
```

```
aws --endpoint-url=http://localhost:4566 autoscaling start-instance-refresh `
    --auto-scaling-group-name my-app-asg `
    --preferences "MinHealthyPercentage=50"
```

```
aws --endpoint-url=http://localhost:4566 elbv2 create-listener `
    --load-balancer-arn $LB_ARN `
    --protocol HTTP `
    --port 80 `
    --default-actions "Type=forward,TargetGroupArn=$TG_ARN"
```

```
aws --endpoint-url=http://localhost:4566 elbv2 describe-target-health --target-group-arn $TG_ARN
```


### Understanding 1

```
┌─────────────────────────────────────────────────────────────────┐
│                    YOUR USERS (Internet)                       │
│                     │                                          │
│                     ▼                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                 LOAD BALANCER (ELB)                     │   │
│  │  - One public entry point                               │   │
│  │  - Listens for traffic (Listener)                       │   │
│  │  - Distributes requests                                 │   │
│  └─────────────────────────────────────────────────────────┘   │
│                     │                                          │
│                     ▼                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                LISTENER                                 │   │
│  │  - "I listen on port 80 for HTTP"                      │   │
│  │  - "I forward traffic to Target Group XYZ"             │   │
│  └─────────────────────────────────────────────────────────┘   │
│                     │                                          │
│                     ▼                                          │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │               TARGET GROUP                              │   │
│  │  - "I manage a group of instances"                     │   │
│  │  - "I health check them"                               │   │
│  │  - "I tell Load Balancer which are healthy"            │   │
│  └─────────────────────────────────────────────────────────┘   │
│                     │                                          │
│          ┌──────────┼──────────┐                              │
│          ▼          ▼          ▼                              │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐                      │
│  │ EC2 #1   │ │ EC2 #2   │ │ EC2 #3   │                      │
│  │ Port 80  │ │ Port 80  │ │ Port 80  │                      │
│  └──────────┘ └──────────┘ └──────────┘                      │
└─────────────────────────────────────────────────────────────────┘
```



