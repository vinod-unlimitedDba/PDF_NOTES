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
