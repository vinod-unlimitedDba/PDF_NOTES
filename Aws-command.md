# Aws cli command
   
   >## To create key pair

            aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text > MyKeyPair.pem &&
    



  >## To create Ec2 instance from cli
```
aws ec2 run-instances --image-id ami-0d81306eddc614a45 
--instance-type t2.micro 
--block-device-mappings "[{\"DeviceName\":\"/dev/sdf\",\"Ebs\":{\"VolumeSize\":10,\"DeleteOnTermination\":true}}]"   
--tag-specifications 'ResourceType=instance,Tags=[{Key=webserver,Value=production}]' 'ResourceType=volume,Tags=[{Key=cost-center,Value=cc123}]'  
--security-group-id sg-005d9f7ddba3dd075
--key-name keypair 
--user-data file://file_user_data.txt 
```

VPC creation command
```
aws ec2 create-vpc 
--region  ap-south-1 
--cidr-block 10.0.0.0/16
--tag-specifications 'ResourceType=vpc,Tags=[{Key=Name,Value=my-vpc}]'
```

subnet
```
aws ec2 create-subnet 
--region ap-south-1 
--vpc-id vpc-0e5a772b4d5042d29 
--cidr-block 10.0.1.0/24 
--tag-specifications 'ResourceType=subnet,Tags=[{Key=Name,Value=my-subnet},{Key=env,Value=DB}]'
```

ElB
-----------


aws elbv2 create-load-balancer --name my-load-balancer --type application --subnets subnet-12345678 subnet-87654321 --security-groups sg-12345678 --region us-west-2

aws elbv2 create-target-group --name my-target-group --protocol HTTP --port 80 --vpc-id vpc-12345678 --region us-west-2

aws elbv2 register-targets --target-group-arn arn:aws:elasticloadbalancing:us-west-2:123456789012:targetgroup/my-target-group/1234567890abcdef --targets Id=i-0123456789abcdef0 Id=i-9876543210fedcba0 --region us-west-2

aws elbv2 create-listener --load-balancer-arn arn:aws:elasticloadbalancing:us-west-2:123456789012:loadbalancer/app/my-load-balancer/1234567890abcdef --protocol HTTP --port 80 --default-actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:us-west-2:123456789012:targetgroup/my-target-group/1234567890abcdef --region us-west-2



