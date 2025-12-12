:original_name: sfs_01_0055.html

.. _sfs_01_0055:

Log Printing
============

Context
-------

SFS Turbo can provide shared log output directories for multiple service nodes, facilitating log collection and management of distributed applications. Features of such services are as follows:

-  A shared file system is mounted to multiple service hosts and logs are printed concurrently.
-  Large file size and small I/O: The size of a single log file is large, but the I/O of each log writing is small.
-  Write I/O intensive: Write I/O of small blocks is the major service.

Configuration Process
---------------------

#. Log in to the SFS console. Create an SFS Turbo file system to store the log files.
#. Log in to the cloud server that functions as the compute node and mount the file system.
#. Configure the log directory to the shared file system. It is recommended that each host use different log files.
#. Start applications.

Prerequisites
-------------

-  A VPC has been created.
-  Cloud servers that function as the head node and compute node have been created and are in the created VPC.
-  SFS has been enabled.

Example Configuration
---------------------

#. Log in to the SFS console.

#. In the upper right corner of the page, click **Create File System**.

#. On the **Create File System** page, set parameters as instructed.

#. After the configuration is complete, click **Create Now**.

   To mount a file system to Linux ECSs, see :ref:`Mounting an NFS File System to ECSs (Linux) <en-us_topic_0034428728>`. To mount a file system to Windows ECSs, see :ref:`Mounting an NFS File System to ECSs (Windows) <en-us_topic_0105224109>`.

#. Configure the log directory to the shared file system. It is recommended that each host use different log files.

#. Start applications.
