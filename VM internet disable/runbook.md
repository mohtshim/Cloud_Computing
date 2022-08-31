# **Overview:**

This runbook shows that how we can disable internet in the azure virtual machine.

# **Architecture:**

![image](https://user-images.githubusercontent.com/46097990/187653467-4bc2f462-6a77-4d5e-9a6e-3d9b3b68f340.png)

# **Instruction:**

The steps to disable the internet connection in the azure virtual
machine is as follows.

1.  Log in to your azure portal and create a network security group and
    set the following outbound rules for it.\
    *Source: Any\
    Source Port Ranges: \*\
    Destination: Any\
    Service: Custom\
    Destination port ranges: 8080\
    Protocol: Any\
    Action: Deny\
    Name: Denyinternet*\
    Click on **Add** and you will have followed outbound security rule.\
    ![](media/image2.png){width="6.5in" height="0.25in"}

2.  If you have an already network security group associated with your
    azure machine, then skip step 1 and make changes in the existing
    security group and add outbound rule to it and then you are good to
    go. If not follow the next steps

3.  Assign your VM to newly created security group \
    go to your VM -\> Change the NSG to new one.

4.  Now for the test connectivity if your VM is windows then\
    Restart the VM \> Go to RDP \> Open Internet Explorer \> Try
    [www.bing.com](http://www.bing.com)\
    If you are on Linux then\
    Restart the VM \> Go to CMD \> run command ping -c 3 google.com
