**Problem:**

 Create a VNET and 2 subnets, create one network security group per
subnet (Azure).

**Instruction:**

1.  Open your azure portal in your browser and search virtual network in
    the search bar and open it.\
    ![Graphical user interface, text, application, chat or text message
    Description automatically
    generated](media/image1.png){width="2.9024245406824147in"
    height="1.3650360892388451in"}

2.  A new interface will open. Now click on the **create\
    **![](media/image2.png){width="0.7501049868766404in"
    height="0.3646347331583552in"}**\
    **In the basics tab enter **project details** and **instance
    details** of your own choice\
    ![](media/image3.png){width="4.33704615048119in"
    height="1.3872976815398075in"}\
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
    ![](media/image4.png){width="4.290820209973753in"
    height="2.6918471128608923in"}\
    Accept the defaults setting for the **security, tags options** and
    create the virtual network. After some time your virtual network
    will be deployed.

3.  Now to create the network security group search the **network
    security group** in the search bar\
    ![](media/image5.png){width="5.073686570428697in"
    height="1.0608125546806648in"}\
    Click on **Create\
    **![](media/image6.png){width="0.718850612423447in"
    height="0.3125437445319335in"}**\
    **In the basics tabs enter the **project and instance details** and
    click **next,** enter tags and click on **create**. Now you have
    your network security group for the subnet-1. Repeat the same
    process for the subnet-2. You will have a massage in your screen
    like this as follows.\
    ![](media/image7.png){width="5.562945100612423in"
    height="0.8665365266841645in"}

4.  Now to connect the network security group to your subnet. Go to your
    resource group -\> Virtual Network -\> Setting -\> subnet-1 -\> set
    the network security group.\
    ![Graphical user interface, application Description automatically
    generated](media/image8.png){width="4.3829483814523185in"
    height="1.1202679352580927in"}\
    Repeat the same process for the subnet 2.
