:original_name: sfs_01_0048.html

.. _sfs_01_0048:

SFS Turbo Metrics
=================

Function
--------

This topic describes metrics reported by Elastic File Service (EFS) to Cloud Eye as well as their namespaces and dimensions. You can use the console or APIs provided by Cloud Eye to query the metrics generated for EFS.

Namespace
---------

SYS.EFS

Metrics
-------

+-----------------------+-----------------------------------+---------------------------------------------------+--------------+-----------------------+
| Metric                | Metric Name                       | Description                                       | Value Range  | Monitored Object      |
+=======================+===================================+===================================================+==============+=======================+
| client_connections    | Client Connections                | Number of client connections                      | >= 0         | SFS Turbo file system |
+-----------------------+-----------------------------------+---------------------------------------------------+--------------+-----------------------+
| data_read_io_bytes    | Read Bandwidth                    | Data read I/O load                                | >= 0 bytes/s | SFS Turbo file system |
|                       |                                   |                                                   |              |                       |
|                       |                                   | Unit: byte/s                                      |              |                       |
+-----------------------+-----------------------------------+---------------------------------------------------+--------------+-----------------------+
| data_write_io_bytes   | Write Bandwidth                   | Data write I/O load                               | >= 0 bytes/s | SFS Turbo file system |
|                       |                                   |                                                   |              |                       |
|                       |                                   | Unit: byte/s                                      |              |                       |
+-----------------------+-----------------------------------+---------------------------------------------------+--------------+-----------------------+
| metadata_io_bytes     | Metadata Read and Write Bandwidth | Metadata read and write I/O load                  | >= 0 bytes/s | SFS Turbo file system |
|                       |                                   |                                                   |              |                       |
|                       |                                   | Unit: byte/s                                      |              |                       |
+-----------------------+-----------------------------------+---------------------------------------------------+--------------+-----------------------+
| total_io_bytes        | Total Bandwidth                   | Total I/O load                                    | >= 0 bytes/s | SFS Turbo file system |
|                       |                                   |                                                   |              |                       |
|                       |                                   | Unit: byte/s                                      |              |                       |
+-----------------------+-----------------------------------+---------------------------------------------------+--------------+-----------------------+
| iops                  | IOPS                              | I/O operations per unit time                      | >= 0         | SFS Turbo file system |
+-----------------------+-----------------------------------+---------------------------------------------------+--------------+-----------------------+
| used_capacity         | Used Capacity                     | Used capacity of a file system                    | >= 0 bytes   | SFS Turbo file system |
|                       |                                   |                                                   |              |                       |
|                       |                                   | Unit: byte                                        |              |                       |
+-----------------------+-----------------------------------+---------------------------------------------------+--------------+-----------------------+
| used_capacity_percent | Capacity Usage                    | Percentage of used capacity in the total capacity | 0% to 100%   | SFS Turbo file system |
|                       |                                   |                                                   |              |                       |
|                       |                                   | Unit: Percent                                     |              |                       |
+-----------------------+-----------------------------------+---------------------------------------------------+--------------+-----------------------+

Dimension
---------

=============== ========
Key             Value
=============== ========
efs_instance_id Instance
=============== ========

Viewing Monitoring Statistics
-----------------------------

#. Log in to the management console.

#. View the monitoring graphs using either of the following methods.

   -  Method 1: Choose **Service List** > **Storage** > **Scalable File Service**. In the file system list, click **View Metric** in the **Operation** column of the target file system.
   -  Method 2: Choose **Management & Deployment** > **Cloud Eye** > **Cloud Service Monitoring** > **Elastic File Service**. In the file system list, click **View Metric** in the **Operation** column of the target file system.

#. View the SFS Turbo file system monitoring data by metric or monitored duration.

   For more information about Cloud Eye, see the *Cloud Eye User Guide*.
