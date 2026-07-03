

- IAM is a Eventual Consistency model

IAM is for 


# IAM CLI

### User Operations

##### List Users

```
aws iam list-users
```
##### Create User

```
aws create-user --user-name rishi
```

##### Get a user

gives `NoSuchEntity` error if no such user 

```
aws iam get-user --user-name rishi
```

##### Deleting a User

deletes user refuses deletion if: Access Keys exist, Policies attached, Login profile exists, MFA configured. gives `NoSuchEntity` error if no such user 

```
aws iam delete-user --user-name auditor
```



### Policy Operations

##### Create a Policy

A **policy** is a set of rules that defines permitted actions. When you attach that policy to a user, you grant them the specific permissions and access rights outlined by those rules.

a policy is just a json file 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowListBuckets",
      "Effect": "Allow",
      "Action": [
        "s3:ListAllMyBuckets"
      ],
      "Resource": "*"
    }
  ]
}
```

`Statement` is a list of permission rules
`sid` is statement identifier , can be any name containing only letters and numbers
`Effect` allowed values are `Allow` , `Deny`
`Action` refers to API operations being inlcuded
`Resources` meaning it all resources granted

```
aws iam create-policy `
    --policy-name S3ListBucketsPolicy `
    --policy-document file://allow-s3-list.json
```


##### Listing Policies

```
aws iam list-policies --scope Local
```

##### Attach Policy to User

```
aws iam attach-user-policy `
    --user-name rishi-dev `
    --policy-arn arn:aws:iam::000000000000:policy/S3ListBucketsPolicy
```

##### List User attached Policies

```
aws iam list-attached-user-policies `
    --user-name rishi-dev
```

##### Inspect the Policy

```
aws iam get-policy `
    --policy-arn arn:aws:iam::000000000000:policy/S3ListBucketsPolicy
```



### IAM Groups Operations

##### Creating a Group

Group gives advantage to add policies to a large amout of users rather manually attaching to everyone

```
aws iam create-group `
    --group-name Developers
```

##### Add User to Group
```
aws iam add-user-to-group `
    --group-name Developers `
    --user-name rishi-dev
```

##### Get a Group

```
aws iam get-group `
    --group-name Developers
```

##### Attach Existing Policy to Group

```
aws iam attach-group-policy `
    --group-name Developers `
    --policy-arn arn:aws:iam::000000000000:policy/S3ListBucketsPolicy
```

##### Inspect Group Membership

```
aws iam list-groups-for-user `
    --user-name rishi-dev
```

##### List Attached Group Policies
```
aws iam list-attached-group-policies `
    --group-name Developers
```

### Role Operations

##### Create the Role

`trust-policy.json`
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowAssumeRole",
      "Effect": "Allow",
      "Principal": {
        "AWS": "*"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

```
aws iam create-role `
    --role-name S3ReaderRole `
    --assume-role-policy-document file://trust-policy.json
```

##### List Roles

```
aws iam list-roles
```

##### Attach policy to Role

```
aws iam attach-role-policy `
    --role-name S3ReaderRole `
    --policy-arn arn:aws:iam::000000000000:policy/S3ListBucketsPolicy
```

##### Get policies attached to role

```
aws iam list-attached-role-policies `
    --role-name S3ReaderRole
```

##### Inspect Role

```
aws iam get-role `
    --role-name S3ReaderRole
```

##### Get temporary credentials using role 

STS - Security token service

```
aws sts assume-role `
    --role-arn arn:aws:iam::000000000000:role/S3ReaderRole `
    --role-session-name demo-session
```

