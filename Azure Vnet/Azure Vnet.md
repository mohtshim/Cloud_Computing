**Problem:**

 Create a VNET and 2 subnets, create one network security group per
subnet (Azure).

**Instruction:**

1.  Open your azure portal in your browser and search virtual network in
    the search bar and open it.\
    ![image](https://user-images.githubusercontent.com/46097990/187648963-8906e89d-0569-4706-81a7-b6acb711aabd.png)

2.  A new interface will open. Now click on the **create\
    **![image](https://user-images.githubusercontent.com/46097990/187649145-213846d5-9ced-41e2-bb16-7819481b7dd4.png)**\
    **In the basics tab enter **project details** and **instance
    details** of your own choice\
    !![image](https://user-images.githubusercontent.com/46097990/187649172-320e4bdd-66ff-42ed-aea9-5700ba08c59d.png)\
    click on next and enter the CIDR IP address. We can see here that we
    can make the subnets here so make 2 subnets here. Click on add
    subnets and a new tab will open on right side of the screen. Enter
    the subnet name and the subnet address. Repeat this process one more
    time. You can divide your VNet IPv4 into 2 parts for your 2 subnets
    for example, if you create a VNet with CIDR block 10.0.0.0/24, it
    supports 256 IP addresses. You can break this CIDR block into two
    subnets, each supporting 128 IP addresses. One subnet uses CIDR
    block 10.0.0.0/25 (for addresses 10.0.0.0 - 10.0.0.127) and the
    other uses CIDR block 10.0.0.128/25 (for addresses 10.0.0.128 -
    10.0.0.255). Now in the **Subnets** section you will have your 2
    subnets created\
    Your IP addresses part will be look like this\
    ![image](https://user-images.githubusercontent.com/46097990/187649239-2ff7ede3-fb34-4603-8db2-9c9e0e3d3a62.png)\
    Accept the defaults setting for the **security, tags options** and
    create the virtual network. After some time your virtual network
    will be deployed.

3.  Now to create the network security group search the **network
    security group** in the search bar\
    ![image](https://user-images.githubusercontent.com/46097990/187649294-f4a3890b-0dad-4726-b884-285d175d974c.png)\
    Click on **Create\
    **![image](https://user-images.githubusercontent.com/46097990/187649343-2780ee78-a89f-4399-8f18-08aba8cec37c.png)**\
    **In the basics tabs enter the **project and instance details** and
    click **next,** enter tags and click on **create**. Now you have
    your network security group for the subnet-1. Repeat the same
    process for the subnet-2. You will have a massage in your screen
    like this as follows.\
    ![image](https://user-images.githubusercontent.com/46097990/187649439-2d92199e-bf71-4331-829a-71f049d59801.png)

4.  Now to connect the network security group to your subnet. Go to your
    resource group -\> Virtual Network -\> Setting -\> subnet-1 -\> set
    the network security group.\
    ![image](https://user-images.githubusercontent.com/46097990/187649619-c4c28fad-e025-46d6-ba67-424b484abb53.png)\
    Repeat the same process for the subnet 2.
