:original_name: sfs_01_0130.html

.. _sfs_01_0130:

How Is the SFS Turbo Capacity Quota Calculated?
===============================================

When the system calculates the used capacity quota of an SFS Turbo file system, the space used by the system disks on the background VMs are also included. You will not be billed for these spaces. They are only used for quota calculation.

Each file system has two background VMs, working in active/standby mode, and each VM uses a 50 GB system disk.

Example: For a 2,000 GB SFS Turbo file system, the used capacity quota is 2,100 GB (2,000 GB + 50 GB x 2).
