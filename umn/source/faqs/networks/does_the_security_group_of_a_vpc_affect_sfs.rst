:original_name: sfs_01_0081.html

.. _sfs_01_0081:

Does the Security Group of a VPC Affect SFS?
============================================

A security group is a collection of access control rules for servers that have the same security protection requirements and are mutually trusted in a VPC. After a security group is created, you can create different access rules for the security group to protect the servers that are added to this security group. The default security group rule allows all outgoing data packets. Servers in a security group can access each other without the need to add rules. The system creates a security group for each cloud account by default. Users can also create custom security groups by themselves.

After an SFS Turbo file system is created, the system automatically enables the security group port required by the NFS protocol. This ensures that the SFS Turbo file system can be accessed by your servers and prevents file system mounting failures. The inbound ports required by the NFS protocol are ports 111, 2049, 2051, 2052, and 20048. If you need to change the enabled ports, go to the VPC console, choose **Access Control** > **Security Groups**, locate the target security group, and change the ports.

You are advised to use an independent security group for an SFS Turbo file system to isolate it from service nodes.

You need to add inbound and outbound rules for the security group of an SFS Capacity-Oriented file system. For details, see section "Adding a Security Group Rule" in the *Virtual Private Cloud User Guide*. In an SFS Capacity-Oriented file system, the inbound ports required by the NFS protocol are ports 111, 2049, 2051, and 2052. The inbound port required by the DNS server is port 53.

Example Value
-------------

-  Inbound rule

   +-----------+-------------+------------+-------------------+---------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Direction | Protocol    | Port Range | Source IP Address |                                                               | Description                                                                                   |
   +===========+=============+============+===================+===============================================================+===============================================================================================+
   | Inbound   | TCP and UDP | 111        | IP Address        | 0.0.0.0/0 (All IP addresses are allowed. It can be modified.) | One port corresponds to one access rule. You need to add information to the ports one by one. |
   +-----------+-------------+------------+-------------------+---------------------------------------------------------------+-----------------------------------------------------------------------------------------------+

-  Outbound rule

   +-----------+-------------+------------+-------------------+---------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Direction | Protocol    | Port Range | Source IP Address |                                                               | Description                                                                                   |
   +===========+=============+============+===================+===============================================================+===============================================================================================+
   | Outbound  | TCP and UDP | 111        | IP Address        | 0.0.0.0/0 (All IP addresses are allowed. It can be modified.) | One port corresponds to one access rule. You need to add information to the ports one by one. |
   +-----------+-------------+------------+-------------------+---------------------------------------------------------------+-----------------------------------------------------------------------------------------------+

   .. note::

      Enter an IP address range using a mask. For example, enter **192.168.1.0/24**, and do not enter **192.168.1.0-192.168.1.255**. If the source IP address is 0.0.0.0/0, all IP addresses are allowed.

      The bidirectional access rule must be configured for port 111. The inbound rule can be set to the front-end service IP range of SFS. You can obtain it by running the following command: **ping** *File system domain name or IP address* or **dig** *File system domain name or IP address*.

      For ports 2049, 2050, 2051, and 2052, only the outbound rule needs to be added, which is the same as the outbound rule of port 111.

      For the NFS protocol, add an inbound rule to open the TCP&UDP port 111, TCP ports 2049, 2051, and 2052, and UDP&TCP port 20048.

      For the NFS protocol with UDP port 20048 not opened, the time required for mounting may become longer. In this case, you can use the **-o tcp** option in **mount** to avoid this issue.
