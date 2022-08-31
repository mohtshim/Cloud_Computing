**Problem: Difference between the network security group (nsg) and
network access control list (Nacl)**

**Network Security Group:**

A security group has some rules which allows the traffics to reach or
leave the resources which it is associated with. Network security group
has some properties which are as follows.

1.  They operate at the instance level. You must configure the security
    group for each of the instance if you want more security or you can
    initiate the one security group to many instances, but each instance
    can have only one security group each.

2.  They only allow the rules and don't deny any rules.

3.  They are stateful meaning return traffic is allowed.

4.  They evaluate all the rules before deciding whether to allow the
    traffic or not.

5.  They can be enabled when we are launching the instances.

**Network Access Control List:**

They are made up of the rules which either deny or allow access to the
computer environment. They have the following properties which are as
follows.

1.  They operate at the subnet level.

2.  They can allow or deny both.

3.  They are stateless meaning return traffic must be explicitly allowed
    by the rules.

4.  They process rules in order when deciding when to allow traffic.

5.  Once explicitly defined they can apply to all instances.
