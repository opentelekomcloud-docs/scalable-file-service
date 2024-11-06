:original_name: sfs_01_0080.html

.. _sfs_01_0080:

Can a File System Be Accessed Across VPCs?
==========================================

Yes.

-  Multi-VPC access can be configured for an SFS Capacity-Oriented or a general purpose file system so that ECSs in different VPCs can share the same file system, as long as the VPCs that the ECSs belong to are added to the VPC list of the file system or the ECS IP addresses are added as authorized IP addresses of the VPCs. For details, see :ref:`Configuring Multi-VPC Access <sfs_01_0036>`.
-  An SFS Turbo file system allows two or more VPCs in the same region to interconnect with each other through VPC peering connection. In this case, different VPCs are in the same network, and ECSs in these VPCs can share the same file system. For details about VPC peering connection, see section "VPC Peering Connection" in *Virtual Private Cloud User Guide*.
