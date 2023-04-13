# Aws cli command
   
   >## To create key pair

            aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text > MyKeyPair.pem &&
    



  >## To Ec2 instance from cli
```
aws ec2 run-instances --image-id ami-0d81306eddc614a45 
--instance-type t2.micro 
--block-device-mappings "[{\"DeviceName\":\"/dev/sdf\",\"Ebs\":{\"VolumeSize\":10,\"DeleteOnTermination\":true}}]"   
--tag-specifications 'ResourceType=instance,Tags=[{Key=webserver,Value=production}]' 'ResourceType=volume,Tags=[{Key=cost-center,Value=cc123}]'  
--security-group-id sg-005d9f7ddba3dd075
--key-name keypair 
--user-data file://file_user_data.txt 
```

VPC creaion command
```
aws ec2 create-vpc 
--region  ap-south-1 
--cidr-block 10.0.0.0/16
--tag-specifications 'ResourceType=vpc,Tags=[{Key=Name,Value=my-vpc}]'
```


```
aws ec2 create-subnet 
--region ap-south-1 
--vpc-id vpc-0e5a772b4d5042d29 
--cidr-block 10.0.1.0/24 
--tag-specifications 'ResourceType=subnet,Tags=[{Key=Name,Value=my-subnet},{Key=env,Value=DB}]'
```
