:original_name: sfs_01_0111.html

.. _sfs_01_0111:

Does SFS Support Cross-Region Mounting?
=======================================

SFS Capacity-Oriented file systems cannot be mounted across regions. A file system can only be mounted to ECSs in the same region.

General purpose file systems can be mounted across AZs in the same region, but cannot be mounted across regions.

SFS Turbo file systems can be mounted across AZs in the same region, but cannot be mounted across regions. However, if you have used Cloud Connect to enable cross-region communication, SFS Turbo file system can be mounted across regions by specified IP address.
