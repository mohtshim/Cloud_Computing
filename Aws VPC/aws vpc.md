**Problem:**

Create a VPC and 2 subnets, one subnet should be public and other should be private, create network security group for each subnet and only allow port 22 (AWS)

**Instruction:**

1. Open your **aws** account on your browser and search the **VPC** in the search bar and click on it.
 ![](RackMultipart20220831-1-4p4opo_html_83f7f2946db9b972.png)
2. Click on the **Your VPCs** from the left side and a new interface will open. After that click on the **Create VPC**
 ![](RackMultipart20220831-1-4p4opo_html_211c091f3b4f2aea.png)

Choose the following options
 1. Resource to create: VPC only
 2. Name tag: _yourname_
 3. Ipv4 CIDR: _choose that CIDR you want to give to your subnet
 4._ No IPv6
 Apply tags but not necessary here.
 ![](RackMultipart20220831-1-4p4opo_html_68da5085266927f6.png)

Click on your **Create VPC** and you have your first VPC created with the IPv4 CIDR which you give. Now in **Your VPC** option you have your VPC
 ![](RackMultipart20220831-1-4p4opo_html_5625e5deb9302ac5.png)

1. Now click on **Subnets** from the left side and click on the **Create subnet**
 ![](RackMultipart20220831-1-4p4opo_html_ee66f84a86cddd5b.png)

Now choose the **VPC** as your VPC which we created in the previous steps. Under the subnet setting give the subnet the following things
 1. Subnet name
 2. Availability zone
 3. IPv4 CIDR block
 ![](RackMultipart20220831-1-4p4opo_html_5010d31e0cc9287b.png)
 You need to create 2 subnets in which one will be public, and one will be private. You can divide your VPC IPv4 into 2 parts for your 2 subnets for example, if you create a VPC with CIDR block 10.0.0.0/24, it supports 256 IP addresses. You can break this CIDR block into two subnets, each supporting 128 IP addresses. One subnet uses CIDR block 10.0.0.0/25 (for addresses 10.0.0.0 - 10.0.0.127) and the other uses CIDR block 10.0.0.128/25 (for addresses 10.0.0.128 - 10.0.0.255).Now in the **Subnets** section you will have your 2 subnets created
 ![](RackMultipart20220831-1-4p4opo_html_41908e3fbd285236.png)

1. Now under the **Security** click on **Security group** and click on **create security group**
 ![](RackMultipart20220831-1-4p4opo_html_4b88331abbfc7523.png)
Enter the following details
 1. Security group name
 2. Description
 3. VPC
 Add the inbound rule to allow only port 22
 ![](RackMultipart20220831-1-4p4opo_html_2dfb7a3916abbb82.png)
 Click on **create security group.** Create another security group for another subnet which is private but for that inbound rules will be different as we don't want the source to be anywhere.
 ![](RackMultipart20220831-1-4p4opo_html_74982c8338b1d024.png)
 Now we have 2 security group for our 2 subnets.
 ![](RackMultipart20220831-1-4p4opo_html_38817b818448119c.png)

Now whenever the instance will be created in the private or public subnets we can associate the security group to each of them and in that way only port 22 will be allowed for the inbound communication.