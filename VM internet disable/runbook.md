# Contents {#contents .TOC-Heading}

[Overview: [2](#overview)](#overview)

[Architecture: [2](#architecture)](#architecture)

[Instruction: [2](#instruction)](#instruction)

#  

# 

# 

# 

# 

# 

# 

# 

# 

# 

# 

# 

# 

# 

# 

# **Overview:**

In this runbook we will see that how we can disable the internet
connection in the azure virtual machine.

# **Architecture:**

![](media/image1.png){width="6.5in" height="3.8381944444444445in"}

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

3.  Assign your VM to newly created security group\
    go to your VM -\> Change the NSG to new one.

4.  Now for the test connectivity if your VM is windows then\
    Restart the VM \> Go to RDP \> Open Internet Explorer \> Try
    [www.bing.com](http://www.bing.com)\
    If you are on Linux then\
    Restart the VM \> Go to CMD \> run command ping -c 3 google.com
