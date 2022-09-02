## Problem:
Using AWS CLI to create a VPC and 2 Subnets, One Subnet should be public and other should private,
create network security group for each subnet and provision an EC2 Instance

## Instruction:
Before solving the problem we assume that you already configuer your aws cli in your local machine and are already login to your account. Follow the below steps to
solve the problem.
### Step 1: Create a VPC and two subnets
Create a **VPC** with a 10.0.0.0/24 CIDR block using the following **create-vpc** command. 
```
aws ec2 create-vpc --cidr-block 10.0.0.0/24 --query Vpc.VpcId --output text
```
![image](https://user-images.githubusercontent.com/46097990/188067507-d2711722-6b76-4cbd-a156-0fce33047233.png)

This command return a **VPC-ID**. Using the VPC ID from the previous step, create a subnet with a 10.0.0.0/25 CIDR block using the following create-subnet command.
```
aws ec2 create-subnet --vpc-id <VPC-ID> --cidr-block 10.0.0.0/25
```
![image](https://user-images.githubusercontent.com/46097990/188067413-c6d867c2-d924-4599-ad00-270b739607c5.png)

You can divide your VPC IPv4 into 2 parts for your 2 subnets for example, if you create a VPC with CIDR block 10.0.0.0/24, it supports 256 IP addresses. You can break this CIDR block into two subnets, each supporting 128 IP addresses. One subnet uses CIDR block 10.0.0.0/25 (for addresses 10.0.0.0 - 10.0.0.127) and the other uses CIDR block 10.0.0.128/25 (for addresses 10.0.0.128 - 10.0.0.255).

Create a second subnet in your VPC with a 10.0.0.128/25 CIDR block.
```
aws ec2 create-subnet --vpc-id vpc-008d4acb14fa0ea91 --cidr-block 10.0.0.128/25
```
![image](https://user-images.githubusercontent.com/46097990/188068698-6b13796b-7448-46f2-9033-ecb5001a6989.png)

### Step 2: Make your Subnet Public
After you've created the VPC and subnets, you can make one of the subnets a public subnet by attaching an internet gateway to your VPC, creating a custom route table, and configuring routing for the subnet to the internet gateway.
Create the internet gateway using the following command 
```
aws ec2 create-internet-gateway --query InternetGateway.InternetGatewayId --output text
```
![image](https://user-images.githubusercontent.com/46097990/188071332-aa76f8cc-82fa-4200-ab7d-dcdd4cec6104.png)

Using the ID from the previous step, attach the internet gateway to your VPC using the following attach-internet-gateway command.
```
aws ec2 attach-internet-gateway --vpc-id <VPC-ID> --internet-gateway-id <IGW-ID>
```
Create a custom route table for your VPC using the following create-route-table command.
```
aws ec2 create-route-table --vpc-id <VPC-ID> --query RouteTable.RouteTableId --output text
```
![image](https://user-images.githubusercontent.com/46097990/188072080-5963802a-32fc-4c01-b0c8-8fb5b7aeec7d.png)

Create a route in the route table that points all traffic (0.0.0.0/0) to the internet gateway using the following create-route command.
```
aws ec2 create-route --route-table-id <Route-ID> --destination-cidr-block 0.0.0.0/0 --gateway-id <IGW-ID>
```
![image](https://user-images.githubusercontent.com/46097990/188072578-24d8a714-61f5-4920-9c69-bc5303807baf.png)


   
