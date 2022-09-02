## Problem:
Using AWS CLI to create a VPC and 2 Subnets, One Subnet should be public and other should private,
create network security group for each subnet and provision an EC2 Instance

## Instruction:
Before solving the problem we assume that you already configuer your aws cli in your local machine and are already login to your account. Follow the below steps to
solve the problem.
### Step 1: Create a VPC and two subnets
1. Create a **VPC** with a 10.0.0.0/24 CIDR block using the following **create-vpc** command. 
    ```
    aws ec2 create-vpc --cidr-block 10.0.0.0/24 --query Vpc.VpcId --output text
    ```
    ![image](https://user-images.githubusercontent.com/46097990/188067507-d2711722-6b76-4cbd-a156-0fce33047233.png)

2. This command return a **VPC-ID**. Using the VPC ID from the previous step, create a subnet with a 10.0.0.0/25 CIDR block using the following create-subnet command.
    ```
    aws ec2 create-subnet --vpc-id <VPC-ID> --cidr-block 10.0.0.0/25
    ```
    ![image](https://user-images.githubusercontent.com/46097990/188067413-c6d867c2-d924-4599-ad00-270b739607c5.png)

You can divide your VPC IPv4 into 2 parts for your 2 subnets for example, if you create a VPC with CIDR block 10.0.0.0/24, it supports 256 IP addresses. You can break this CIDR block into two subnets, each supporting 128 IP addresses. One subnet uses CIDR block 10.0.0.0/25 (for addresses 10.0.0.0 - 10.0.0.127) and the other uses CIDR block 10.0.0.128/25 (for addresses 10.0.0.128 - 10.0.0.255).

3. Create a second subnet in your VPC with a 10.0.0.128/25 CIDR block.
    ```
    aws ec2 create-subnet --vpc-id vpc-008d4acb14fa0ea91 --cidr-block 10.0.0.128/25
    ```
    ![image](https://user-images.githubusercontent.com/46097990/188068698-6b13796b-7448-46f2-9033-ecb5001a6989.png)

### Step 2: Make your Subnet Public
After you've created the VPC and subnets, you can make one of the subnets a public subnet by attaching an internet gateway to your VPC, creating a custom route table, and configuring routing for the subnet to the internet gateway.
1. Create the internet gateway using the following command 
    ```
    aws ec2 create-internet-gateway --query InternetGateway.InternetGatewayId --output text
    ```
    ![image](https://user-images.githubusercontent.com/46097990/188071332-aa76f8cc-82fa-4200-ab7d-dcdd4cec6104.png)

2. Using the ID from the previous step, attach the internet gateway to your VPC using the following attach-internet-gateway command.
    ```
    aws ec2 attach-internet-gateway --vpc-id <VPC-ID> --internet-gateway-id <IGW-ID>
    ```
3. Create a custom route table for your VPC using the following create-route-table command.
    ```
    aws ec2 create-route-table --vpc-id <VPC-ID> --query RouteTable.RouteTableId --output text
    ```
    ![image](https://user-images.githubusercontent.com/46097990/188072080-5963802a-32fc-4c01-b0c8-8fb5b7aeec7d.png)

4. Create a route in the route table that points all traffic (0.0.0.0/0) to the internet gateway using the following create-route command.
    ```
    aws ec2 create-route --route-table-id <Route-ID> --destination-cidr-block 0.0.0.0/0 --gateway-id <IGW-ID>
    ```
    ![image](https://user-images.githubusercontent.com/46097990/188072578-24d8a714-61f5-4920-9c69-bc5303807baf.png)

5. The route table is currently not associated with any subnet. You need to associate it with a subnet in your VPC so that traffic from that subnet is routed to the internet gateway. Use the following describe-subnets command to get the subnet IDs
    ```
    aws ec2 describe-subnets --filters "Name=vpc-id,Values=<VPC-ID>" --query "Subnets[*].{ID:SubnetId,CIDR:CidrBlock}"
    ```
    ![image](https://user-images.githubusercontent.com/46097990/188073286-f0b22b7d-6a18-4371-a1d8-a096f3cc02ba.png)

6. You can choose which subnet to associate with the custom route table, for example, subnet-0a6551ca0eecc92aa, and associate it using the associate-route-table command. This subnet is your public subnet.
    ```
    aws ec2 associate-route-table  --subnet-id <Subnet-ID> --route-table-id <Route-ID>
    ```
    ![image](https://user-images.githubusercontent.com/46097990/188074248-98ca0f40-5ebd-487f-83e9-19ffc86d555e.png)

### Step 3: Launch an instance in public subnet
**To launch and connect to an instance in your public subnet**
1. Create a key pair and use the --query option and the --output text option to pipe your private key directly into a file with the .pem extension.
    ```
    aws ec2 create-key-pair --key-name MyKeyPair --query "KeyMaterial" --output text > MyKeyPair.pem
    ```
2. In this example, you launch an Amazon Linux instance. If you use an SSH client on a Linux or Mac OS X operating system to connect to your instance, use the following command to set the permissions of your private key file so that only you can read it.
    ```
    chmod 400 MyKeyPair.pem
    ```

3. Create a security group in your VPC using the create-security-group command.
    ```
    aws ec2 create-security-group --group-name SSHAccess --description "Security group for SSH access" --vpc-id <VPC-ID>
    ```
    ![image](https://user-images.githubusercontent.com/46097990/188075664-a8d92cc3-b46e-4d38-b95d-1fa5c8e9dd4d.png)

4. Add a rule that allows SSH access from anywhere using the authorize-security-group-ingress command.
    ```
    aws ec2 authorize-security-group-ingress --group-id <SG-ID> --protocol tcp --port 22 --cidr 0.0.0.0/0
    ```
    ![image](https://user-images.githubusercontent.com/46097990/188075916-88331b31-d9dc-4fca-9196-e307f97d1ae1.png)

5. Launch an instance into your public subnet, using the security group and key pair you've created. In the output, take note of the instance ID for your instance.
    ```
    aws ec2 run-instances --image-id ami-a4827dc9 --count 1 --instance-type t2.micro --key-name MyKeyPair --security-group-ids sg-e1fb8c9a --subnet-id subnet-b46032ec
    ```
6. Your instance must be in the running state in order to connect to it. Use the following command to describe the state and IP address of your instance.
    ```
    aws ec2 describe-instances --instance-id i-0657a31236d2ae533 --query "Reservations[*].Instances[*].{State:State.Name,Address:PublicIpAddress}"
    ```
    ![image](https://user-images.githubusercontent.com/46097990/188081825-43a98370-5aac-4c84-8548-5d658549c860.png)
