:original_name: sfs_01_0011.html

.. _sfs_01_0011:

Restrictions and Limitations
============================

General
-------

-  SFS supports the NFSv3 protocol only. The default export options are **rw**, **no_root_squash**, **no_all_squash**, and **sync**.
-  To obtain better performance, you are advised to use the operating systems listed in :ref:`Supported Operating Systems <sfs_01_0014>`, which have passed the compatibility test.
-  Currently, SFS does not support replication.
-  Currently, SFS does not support cross-region access.
-  SFS Capacity-Oriented does not apply to file storage scenarios requiring low latency and high IOPS, such as database services, website building, and code storage.

SFS Capacity-Oriented
---------------------

-  SFS Capacity-Oriented can be accessed only on the intranet and used only on the cloud.

-  Currently, NFSv3 protocol is supported (NFSv4 is not supported).
-  A maximum of 10,000 compute nodes can be mounted to and access a single file system at the same time.
-  The maximum capacity of a single file system is 2 PB, and that of a single file is 240 TB.
-  Multi-VPC access is supported. You can add a maximum of 20 VPCs for one file system and create a maximum of 400 ACL rules for all added VPCs.

SFS Turbo
---------

-  Only the NFSv3 protocol is supported (NFSv4 is not supported).
-  A maximum of 500 compute nodes can be mounted to and access a single file system at the same time.
-  The maximum capacity of a single file system is 32 TB, and the maximum capacity of a single file is 16 TB.
-  Maximum number of files supported by a single file system = Capacity/16 KB. For example, the maximum number of files supported by a 500 GB file system is 32,768,000 (500 GB/16 KB = 500 x 1024 x 1024/16).
-  By default, a single directory contains a maximum of 2 million files.
-  The maximum full path is 1024 bytes, and the maximum file name length is 255 bytes.
-  The maximum soft link length is 1024 bytes.
-  The maximum number of hard links is 255.
-  The maximum directory depth is 100 layers.
