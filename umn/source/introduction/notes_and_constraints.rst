:original_name: sfs_01_0011.html

.. _sfs_01_0011:

Notes and Constraints
=====================

General
-------

-  SFS supports the NFSv3 protocol only. The default export options are **rw**, **no_root_squash**, **no_all_squash**, and **sync**.
-  Currently, SFS does not support replication.
-  Currently, SFS does not support cross-region access.
-  SFS Capacity-Oriented is not suitable for file storage scenarios requiring low latency and high IOPS, such as database services, website building, and code storage.

SFS Capacity-Oriented
---------------------

-  SFS Capacity-Oriented can be accessed only on the intranet and used only on the cloud.

-  Only NFSv3 is supported (NFSv4 is not supported).
-  A maximum of 10,000 compute nodes can be mounted to and access a single file system at the same time.
-  The maximum capacity of a single file system is 2 PB, and that of a single file is 240 TB.
-  Multi-VPC access is supported. You can add a maximum of 20 VPCs for one file system and create a maximum of 400 ACL rules for all added VPCs.

General Purpose File System
---------------------------

-  Only the NFSv3 protocol is supported (NFSv4 is not supported).

-  General purpose file systems do not support file system encryption.

-  General purpose file systems can only be accessed over the intranet.

-  A single directory can contain a maximum of 30 million files.

-  General purpose file systems cannot be mounted to 32-bit Linux ECSs.

-  The name of a general purpose file system must be globally unique. It cannot be the same as any existing general purpose file system name or one created by any other user. And it cannot be changed after the file system is created.

-  If a general purpose file system is deleted, you can create a new file system with the same name as the deleted one 30 minutes after that file system has been deleted.

-  General purpose file systems cannot be mounted to Windows ECSs.

-  Root directory permissions of general purpose file systems cannot be changed.

-  When General Purpose File System is used as the storage backend of CCE or CCI, you need to empty the in-use file systems before deleting any PVCs or PVs. If you directly delete the PVCs or PVs, the file systems may fail to be deleted. Check whether the file systems are deleted on the General Purpose File System console.

   Deleting PVCs or PVs takes some time. The billing ends until the corresponding file systems are deleted from the General Purpose File System console.

SFS Turbo
---------

-  Only the NFSv3 protocol is supported (NFSv4 is not supported).
-  A maximum of 500 compute nodes can be mounted to and access a single file system at the same time.
-  The maximum capacity of a single file system is 32 TB, and the maximum size of a single file allowed is 320 TB.
-  Maximum number of files supported by a single file system = Capacity/16. For example, the maximum number of files supported by a 500 GB file system is 32,768,000 (500 GB/16 KB = 500 x 1024 x 1024/16).
-  By default, a single directory can contain a maximum of 20 million files.

   .. note::

      If you need to execute the **ls**, **du**, **cp**, **chmod**, or **chown** command on a directory, you are advised to place no more than 500,000 files or subdirectories in that directory. Otherwise, requests may take long times as the NFS protocol sends a large number of requests to traverse directory files and requests are queueing up.

-  The maximum full path is 4,096 bytes, and the maximum file name length is 255 bytes.
-  The maximum soft link length is 1,024 bytes.
-  The maximum number of hard links is 255.
-  The maximum directory depth is 100 layers.
