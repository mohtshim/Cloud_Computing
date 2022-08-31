**Problem:**

Create a VPC and 2 subnets, one subnet should be public and other should
be private, create network security group for each subnet and only allow
port 22 (AWS)

**Instruction:**

1.  Open your **aws** account on your browser and search the **VPC** in
    the search bar and click on it.\
    ![](media/image1.png){width="1.7819958442694663in"
    height="1.295997375328084in"}

2.  Click on the **Your VPCs** from the left side and a new interface
    will open. After that click on the **Create VPC**\
    ![](media/image2.png){width="1.4377001312335957in"
    height="0.4375612423447069in"}

    Choose the following options\
    1. Resource to create: VPC only\
    2. Name tag: *yourname*\
    3. Ipv4 CIDR: *choose that CIDR you want to give to your subnet\
    4.* No IPv6\
    Apply tags but not necessary here.\
    ![](media/image3.png){width="4.720757874015748in"
    height="3.708519247594051in"}

    Click on your **Create VPC** and you have your first VPC created with
    the IPv4 CIDR which you give. Now in **Your VPC** option you have your
    VPC\
    ![](media/image4.png){width="6.5in" height="0.44513888888888886in"}

3.  Now click on **Subnets** from the left side and click on the
    **Create subnet**\
    ![](media/image5.png){width="1.4377001312335957in"
    height="0.35421587926509185in"}

    Now choose the **VPC** as your VPC which we created in the previous
    steps. Under the subnet setting give the subnet the following things\
    1. Subnet name\
    2. Availability zone\
    3. IPv4 CIDR block\
    ![](media/image6.png){width="4.700429790026247in"
    height="2.494341644794401in"}\
    You need to create 2 subnets in which one will be public, and one will
    be private. You can divide your VPC IPv4 into 2 parts for your 2 subnets
    for example, if you create a VPC with CIDR block 10.0.0.0/24, it
    supports 256 IP addresses. You can break this CIDR block into two
    subnets, each supporting 128 IP addresses. One subnet uses CIDR block
    10.0.0.0/25 (for addresses 10.0.0.0 - 10.0.0.127) and the other uses
    CIDR block 10.0.0.128/25 (for addresses 10.0.0.128 - 10.0.0.255).Now in
    the **Subnets** section you will have your 2 subnets created\
    ![Graphical user interface, application Description automatically
    generated](media/image7.png){width="5.477265966754156in"
    height="1.2674956255468066in"}

4.  Now under the **Security** click on **Security group** and click on
    **create security group\
    **![](media/image8.png){width="2.0940419947506563in"
    height="0.3854702537182852in"}**\
    **Enter the following details\
    1. Security group name\
    2. Description\
    3. VPC\
    Add the inbound rule to allow only port 22\
    ![Graphical user interface, application Description automatically
    generated](media/image9.png){width="6.5in"
    height="1.4430555555555555in"}\
    Click on **create security group.** Create another security group
    for another subnet which is private but for that inbound rules will
    be different as we don't want the source to be anywhere.\
    ![Graphical user interface, application Description automatically
    generated](media/image10.png){width="6.5in"
    height="1.4444444444444444in"}\
    Now we have 2 security group for our 2 subnets.\
    ![Graphical user interface, text, application, email Description
    automatically generated](media/image11.png){width="6.5in"
    height="1.8298611111111112in"}

    Now whenever the instance will be created in the private or public
    subnets we can associate the security group to each of them and in that
    way only port 22 will be allowed for the inbound communication.
