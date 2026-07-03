


**Floci is an emulator to run AWS , Azure , GCP locally**

we should also learn how the services work provided by  AWS [[TODO  Services]]




```
docker run --rm --name floci -p 4566:4566 -e FLOCI_SERVICES_S3_ENABLED=true -e FLOCI_SERVICES_IAM_ENABLED=true -e FLOCI_SERVICES_IAM_ENFORCEMENT_ENABLED=true floci/floci:latest
```

`-e` used to set Env variables


```
aws iam create-group --group-name S3Admins  
aws iam create-group --group-name S3Developers  
aws iam create-group --group-name S3ReadOnly

aws iam create-user --user-name admin-user  
aws iam create-user --user-name developer-user  
aws iam create-user --user-name readonly-user

aws iam add-user-to-group --group-name S3Admins --user-name admin-user  
aws iam add-user-to-group --group-name S3Developers --user-name developer-user  
aws iam add-user-to-group --group-name S3ReadOnly --user-name readonly-user


aws iam create-policy --policy-name STSIdentityCheck --policy-document file://sts-self-check.json

aws iam attach-group-policy --group-name S3Admins --policy-arn $stsArn  
aws iam attach-group-policy --group-name S3Developers --policy-arn $stsArn  
aws iam attach-group-policy --group-name S3ReadOnly --policy-arn $stsArn


Write-Host ""  
Write-Host "================ ADMIN USER ================"  
aws iam create-access-key --user-name admin-user

Write-Host ""  
Write-Host "============== DEVELOPER USER =============="  
aws iam create-access-key --user-name developer-user

Write-Host ""  
Write-Host "============== READONLY USER =============="  
aws iam create-access-key --user-name readonly-user

Write-Host ""  
Write-Host "Bootstrap complete."  
Write-Host ""  
Write-Host "Next:"  
Write-Host "1. Copy AccessKeyId + SecretAccessKey values."  
Write-Host "2. Create AWS profiles."  
Write-Host "3. Continue S3 labs."
```

```
aws configure set aws_access_key_id ... --profile admin
aws configure set aws_secret_access_key ... --profile admin
```

```
aws configure set aws_access_key_id ... --profile developer
aws configure set aws_secret_access_key ... --profile developer
```

```
aws configure set aws_access_key_id ... --profile readonly
aws configure set aws_secret_access_key ... --profile readonly
```
