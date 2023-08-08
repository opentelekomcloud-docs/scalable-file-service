:original_name: sfs_01_0055.html

.. _sfs_01_0055:

Log Printing
============

Context
-------

SFS Turbo can provide multiple service nodes for shared log output directories, facilitating log collection and management of distributed applications. Features of such services are as follows:

-  A shared file system is mounted to multiple service hosts and logs are printed concurrently.
-  Large file size and small I/O: The size of a single log file is large, but the I/O of each log writing is small.
-  Write I/O intensive: Write I/O of small blocks is the major service.

Configuration Process
---------------------

#. Log in to SFS Console. Create an SFS Turbo file system to store the log files.
#. Log in to the server that functions as the compute node and mount the file system.
#. Configure the log directory to the shared file system. It is recommended that each host use different log files.
#. Start applications.

Prerequisites
-------------

-  A VPC has been created.
-  Servers that function as head nodes and compute nodes have been created, and have been assigned to the VPC.
-  SFS has been enabled.

Example Configuration
---------------------

#. Log in to SFS Console.

#. In the upper right corner of the page, click **Create File System**.

#. On the **Create File System** page, set parameters as instructed.

#. After the configuration is complete, click **Create Now**.

   To mount a file system to Linux ECSs, see :ref:`Mounting an NFS File System to ECSs (Linux) <en-us_topic_0034428728>`. To mount a file system to Windows ECSs, see :ref:`Mounting an NFS File System to ECSs (Windows) <en-us_topic_0105224109>`.

#. Configure the log directory to the shared file system. It is recommended that each host use different log files.

#. Start applications.
