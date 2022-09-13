## Problem:
Using Azure CLI to create a VNet and 2 Subnets, create network security group per subnet 

## Instruction:
Before starting we assume that you have azure cli installed in your local machine and have login into your account. Follow the given steps to solve the problem.

1. Create the virtual network using the following command
    ```
    az network vnet create -g resourcegroupname -n MyVnet --address-prefix 10.0.0.0/24
    ```
2. Before creating the subnets we need to create network security group for each subnets.
    ```
    az network nsg create -g MyResourceGroup -n NSG-Subnet-1 
    ```
    ```
    az network nsg create -g MyResourceGroup -n NSG-Subnet-2 
    ```
3. Now create the subnets using the following commands
    ```
    az network vnet subnet create -g MyResourceGroup --vnet-name MyVnet -n MySubnet --address-prefixes 10.0.0.0/-25 --network-security-group NSG-Subnet-1
    ```
    ```
    az network vnet subnet create -g MyResourceGroup --vnet-name MyVnet -n MySubnet --address-prefixes 10.0.0.128/25 --network-security-group NSG-Subnet-2
    ```
