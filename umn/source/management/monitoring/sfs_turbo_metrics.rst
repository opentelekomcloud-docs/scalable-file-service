:original_name: sfs_01_0048.html

.. _sfs_01_0048:

SFS Turbo Metrics
=================

Function
--------

This section describes the SFS metrics reported to Cloud Eye as well as their namespaces and dimensions. You can use the Cloud Eye console or APIs provided by Cloud Eye to query the SFS metrics and alarms.

.. note::

   Cloud Eye can monitor dimensions nested to a maximum depth of four levels (levels 0 to 3). 3 is the deepest level.

Namespace
---------

SYS.EFS

Metrics
-------

.. table:: **Table 1** SFS Turbo metrics

   +-----------------------+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+---------+-----------------+-----------------+------------------------------+
   | Metric ID             | Metric Name                       | Description                                                                                                                                                | Value Range | Unit    | Conversion Rule | Dimension       | Monitoring Period (Raw Data) |
   +=======================+===================================+============================================================================================================================================================+=============+=========+=================+=================+==============================+
   | client_connections    | File System Client Connections    | Number of client connections                                                                                                                               | >= 0        | count   | N/A             | efs_instance_id | 1 minute                     |
   |                       |                                   |                                                                                                                                                            |             |         |                 |                 |                              |
   |                       |                                   | .. note::                                                                                                                                                  |             |         |                 |                 |                              |
   |                       |                                   |                                                                                                                                                            |             |         |                 |                 |                              |
   |                       |                                   |    Only active client connections are counted.                                                                                                             |             |         |                 |                 |                              |
   |                       |                                   |                                                                                                                                                            |             |         |                 |                 |                              |
   |                       |                                   |    A network connection is automatically disconnected when the client has no I/Os for a long time and is automatically re-established when there are I/Os. |             |         |                 |                 |                              |
   +-----------------------+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+---------+-----------------+-----------------+------------------------------+
   | data_read_io_bytes    | Read Bandwidth                    | Data read I/O load                                                                                                                                         | >= 0        | bytes/s | 1024 (IEC)      | efs_instance_id | 1 minute                     |
   +-----------------------+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+---------+-----------------+-----------------+------------------------------+
   | data_write_io_bytes   | Write Bandwidth                   | Data write I/O load                                                                                                                                        | >= 0        | bytes/s | 1024 (IEC)      | efs_instance_id | 1 minute                     |
   +-----------------------+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+---------+-----------------+-----------------+------------------------------+
   | metadata_io_bytes     | Metadata Read and Write Bandwidth | Metadata read and write I/O load                                                                                                                           | >= 0        | bytes/s | 1024 (IEC)      | efs_instance_id | 1 minute                     |
   +-----------------------+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+---------+-----------------+-----------------+------------------------------+
   | total_io_bytes        | Total Bandwidth                   | Total I/O load                                                                                                                                             | >= 0        | bytes/s | 1024 (IEC)      | efs_instance_id | 1 minute                     |
   +-----------------------+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+---------+-----------------+-----------------+------------------------------+
   | iops                  | IOPS                              | I/O operations per unit time                                                                                                                               | >= 0        | count   | N/A             | efs_instance_id | 1 minute                     |
   +-----------------------+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+---------+-----------------+-----------------+------------------------------+
   | used_capacity         | Used Capacity                     | Used capacity of a file system                                                                                                                             | >= 0        | byte    | 1024 (IEC)      | efs_instance_id | 1 minute                     |
   +-----------------------+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+---------+-----------------+-----------------+------------------------------+
   | used_capacity_percent | Capacity Usage                    | Percentage of used capacity in the total capacity                                                                                                          | 0 - 100     | %       | N/A             | efs_instance_id | 1 minute                     |
   +-----------------------+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+---------+-----------------+-----------------+------------------------------+

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
   -  Method 2: Choose **Management & Deployment** > **Cloud Eye** > **Cloud Service Monitoring** > **Scalable File Service Turbo SFS Turbo**. In the file system list, click **View Metric** in the **Operation** column of the desired file system.

#. View the SFS Turbo file system monitoring data by metric or monitored duration.

   For more information about Cloud Eye, see the *Cloud Eye User Guide*.
