:original_name: sfs_01_0081.html

.. _sfs_01_0081:

Does the Security Group of a VPC Affect SFS?
============================================

A security group is a collection of access control rules for ECSs that have the same security protection requirements and are mutually trusted in a VPC. After a security group is created, you can create different access rules for the security group to protect the ECSs that are added to this security group. The default security group rule allows all outgoing data packets. ECSs in a security group can access each other without the need to add rules. The system creates a security group for each cloud account by default. Users can also create custom security groups by themselves.

After an SFS Turbo file system is created, the system automatically enables the security group port required by the NFS protocol in the SFS Turbo file system. This ensures that the SFS Turbo file system can be accessed by your ECS and prevents file system mounting failures. The inbound ports required by the NFS protocol are ports 111, 2049, 2051, 2052, and 20048. If you need to change the enabled ports, choose **Access Control** > **Security Groups** of the VPC console and locate the target security group.

You are advised to use an independent security group for an SFS Turbo instance to isolate it from service nodes.

You need to add inbound and outbound rules for the security group of an SFS Capacity-Oriented file system. For details, see section "Adding a Security Group Rule" in the *Virtual Private Cloud User Guide*. In an SFS Capacity-Oriented file system, the inbound ports required by the NFS protocol are ports 111, 2049, 2051, and 2052. The inbound port required by the DNS server is port 53.

**Example Value**
-----------------

-  Inbound rule

   +-----------+-------------+------------+-------------------+--------------------------+-----------------------------------------------------------------------------------------------+
   | Direction | Protocol    | Port Range | Source IP Address |                          | Description                                                                                   |
   +===========+=============+============+===================+==========================+===============================================================================================+
   | Inbound   | TCP and UDP | 111        | IP Address        | 0.0.0.0/0 (configurable) | One port corresponds to one access rule. You need to add information to the ports one by one. |
   +-----------+-------------+------------+-------------------+--------------------------+-----------------------------------------------------------------------------------------------+

-  Outbound rule

   +-----------+-------------+------------+-------------------+--------------------------+-----------------------------------------------------------------------------------------------+
   | Direction | Protocol    | Port Range | Source IP Address |                          | Description                                                                                   |
   +===========+=============+============+===================+==========================+===============================================================================================+
   | Outbound  | TCP and UDP | 111        | IP Address        | 0.0.0.0/0 (configurable) | One port corresponds to one access rule. You need to add information to the ports one by one. |
   +-----------+-------------+------------+-------------------+--------------------------+-----------------------------------------------------------------------------------------------+

   .. note::

      The bidirectional access rule must be configured for port **111**. The inbound rule can be set to the front-end service IP range of SFS. You can obtain it by running the following command: **ping** *File system domain name or IP address* or **dig** *File system domain name or IP address*.

      For ports **2049**, **2050**, **2051**, and **2052**, only the outbound rule needs to be added, which is the same as the outbound rule of port **111**.
