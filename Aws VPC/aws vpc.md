**Problem:**

Create a VPC and 2 subnets, one subnet should be public and other should
be private, create network security group for each subnet and only allow
port 22 (AWS)

**Instruction:**

1.  Open your **aws** account on your browser and search the **VPC** in
    the search bar and click on it.\
    ![image](https://user-images.githubusercontent.com/46097990/187625036-0065184a-46d9-4e78-b3c9-dccf576faa09.png)

2.  Click on the **Your VPCs** from the left side and a new interface
    will open. After that click on the **Create VPC**\
    ![image](https://user-images.githubusercontent.com/46097990/187625218-8c45b2f0-bcc6-4896-96dc-4be5788e51f7.png)

    Choose the following options\
    1. Resource to create: VPC only
    2. Name tag: *yourname*
    3. Ipv4 CIDR: *choose that CIDR you want to give to your subnet
    4.* No IPv6
    Apply tags but not necessary here.\
    
    ![image](https://user-images.githubusercontent.com/46097990/187625251-203515d1-a535-437b-89a6-0f7485aa8622.png)

    Click on your **Create VPC** and you have your first VPC created with
    the IPv4 CIDR which you give. Now in **Your VPC** option you have your
    VPC\
    ![image](https://user-images.githubusercontent.com/46097990/187625317-850e75a7-7117-4b8b-890b-3371f9b16010.png)

3.  Now click on **Subnets** from the left side and click on the
    **Create subnet**\
    ![image](https://user-images.githubusercontent.com/46097990/187625363-661fa98f-2413-43b4-97f8-569d2b2c92a6.png)

    Now choose the **VPC** as your VPC which we created in the previous
    steps. Under the subnet setting give the subnet the following things\
    1. Subnet name
    2. Availability zone
    3. IPv4 CIDR block\
    
    ![image](https://user-images.githubusercontent.com/46097990/187625423-a6317327-bd34-47cc-bfa6-27f7391051c2.png)\
    
    You need to create 2 subnets in which one will be public, and one will
    be private. You can divide your VPC IPv4 into 2 parts for your 2 subnets
    for example, if you create a VPC with CIDR block 10.0.0.0/24, it
    supports 256 IP addresses. You can break this CIDR block into two
    subnets, each supporting 128 IP addresses. One subnet uses CIDR block
    10.0.0.0/25 (for addresses 10.0.0.0 - 10.0.0.127) and the other uses
    CIDR block 10.0.0.128/25 (for addresses 10.0.0.128 - 10.0.0.255).Now in
    the **Subnets** section you will have your 2 subnets created\
    ![image](https://user-images.githubusercontent.com/46097990/187625468-eb9215ee-f76e-4f15-81e4-bf45c2fdf9cf.png)

4.  Now under the **Security** click on **Security group** and click on
    **create security group**\
    ![image](https://user-images.githubusercontent.com/46097990/187625590-6c2b46d2-c08e-4b5c-856c-3b79836110da.png)\
    **Enter the following details**
    1. Security group name 
    2. Description 
    3. VPC 
    Add the inbound rule to allow only port 22\
    
    ![image](https://user-images.githubusercontent.com/46097990/187625952-99bb3bf4-0859-4b34-89de-57c78ed315c8.png)\
    
    Click on **create security group.** Create another security group
    for another subnet which is private but for that inbound rules will
    be different as we don't want the source to be anywhere.\
    ![image](https://user-images.githubusercontent.com/46097990/187625999-7c04a76b-c8e9-4f75-af8a-b00ad261068c.png)\
    Now we have 2 security group for our 2 subnets.\
    ![image](https://user-images.githubusercontent.com/46097990/187626046-668382e5-0caf-4c8c-ac7a-4fd5ce2ea08e.png)

    Now whenever the instance will be created in the private or public
    subnets we can associate the security group to each of them and in that
    way only port 22 will be allowed for the inbound communication.
