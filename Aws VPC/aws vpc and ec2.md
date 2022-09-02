### Problem:
Using AWS CLI to create a VPC and 2 Subnets, One Subnet should be public and other should private,
create network security group for each subnet and provision an EC2 Instance

### Instruction:
Before solving the problem we assume that you already configuer your aws cli in your local machine and are already login to your account. Follow the below steps to
solve the problem.

1. Create a **VPC** with a 10.0.0.0/24 CIDR block using the following **create-vpc** command. 
   ```
   aws ec2 create-vpc --cidr-block 10.0.0.0/24 --query Vpc.VpcId --output text
   ```
   
   
