:original_name: sfs_01_0047.html

.. _sfs_01_0047:

SFS Metrics
===========

General purpose file systems do not support monitoring. The monitoring metrics described in this section apply only to SFS Capacity-Oriented file systems.

Function
--------

This section describes metrics reported by Scalable File Service (SFS) as well as their namespaces and dimensions. You can use the console or APIs provided by Cloud Eye to query the metrics generated for SFS.

Namespace
---------

SYS.SFS

Metrics
-------

.. table:: **Table 1** SFS metrics

   +-----------------+--------------------------+-----------------------------------------------------------------------+---------------+------------------+------------------------------+
   | Metric ID       | Metric Name              | Description                                                           | Value Range   | Monitored Object | Monitoring Period (Raw Data) |
   +=================+==========================+=======================================================================+===============+==================+==============================+
   | read_bandwidth  | Read Bandwidth           | Read bandwidth of a file system within a monitoring period            | >= 0 bytes/s  | SFS file system  | 4 minutes                    |
   |                 |                          |                                                                       |               |                  |                              |
   |                 |                          | Unit: byte/s                                                          |               |                  |                              |
   +-----------------+--------------------------+-----------------------------------------------------------------------+---------------+------------------+------------------------------+
   | write_bandwidth | Write Bandwidth          | Write bandwidth of a file system within a monitoring period           | >= 0 bytes/s  | SFS file system  | 4 minutes                    |
   |                 |                          |                                                                       |               |                  |                              |
   |                 |                          | Unit: byte/s                                                          |               |                  |                              |
   +-----------------+--------------------------+-----------------------------------------------------------------------+---------------+------------------+------------------------------+
   | rw_bandwidth    | Read and Write Bandwidth | Read and write bandwidth of a file system within a monitoring period  | >= 0 bytes/s  | SFS file system  | 4 minutes                    |
   |                 |                          |                                                                       |               |                  |                              |
   |                 |                          | Unit: byte/s                                                          |               |                  |                              |
   +-----------------+--------------------------+-----------------------------------------------------------------------+---------------+------------------+------------------------------+
   | read_ops        | Read OPS                 | Read operations of a file system within a monitoring period           | >= 0 counts/s | SFS file system  | 4 minutes                    |
   |                 |                          |                                                                       |               |                  |                              |
   |                 |                          | Unit: count/s                                                         |               |                  |                              |
   +-----------------+--------------------------+-----------------------------------------------------------------------+---------------+------------------+------------------------------+
   | write_ops       | Write OPS                | Write operations of a file system within a monitoring period          | >= 0 counts/s | SFS file system  | 4 minutes                    |
   |                 |                          |                                                                       |               |                  |                              |
   |                 |                          | Unit: count/s                                                         |               |                  |                              |
   +-----------------+--------------------------+-----------------------------------------------------------------------+---------------+------------------+------------------------------+
   | rw_ops          | Read Write OPS           | Read and write operations of a file system within a monitoring period | >= 0 counts/s | SFS file system  | 4 minutes                    |
   |                 |                          |                                                                       |               |                  |                              |
   |                 |                          | Unit: count/s                                                         |               |                  |                              |
   +-----------------+--------------------------+-----------------------------------------------------------------------+---------------+------------------+------------------------------+
   | used_capicity   | Used Capacity            | Used capacity of a file system within a monitoring period             | >= 0 bytes    | SFS file system  | 4 minutes                    |
   |                 |                          |                                                                       |               |                  |                              |
   |                 |                          | Unit: byte                                                            |               |                  |                              |
   +-----------------+--------------------------+-----------------------------------------------------------------------+---------------+------------------+------------------------------+

Dimension
---------

======== ===============
Key      Value
======== ===============
share_id SFS file system
======== ===============

Viewing Monitoring Statistics
-----------------------------

#. Log in to the management console.

#. Choose **Management & Deployment** > **Cloud Eye** > **Cloud Service Monitoring** > **Scalable File Service**. In the file system list, click **View Metric** in the **Operation** column of the desired file system.

#. View the SFS file system monitoring data by metric or monitored duration.

   :ref:`Figure 1 <sfs_01_0047__fig4460418173118>` shows the monitoring graphs. For more information about Cloud Eye, see the *Cloud Eye User Guide*.

   .. _sfs_01_0047__fig4460418173118:

   .. figure:: /_static/images/en-us_image_0251362180.png
      :alt: **Figure 1** Monitoring graphs

      **Figure 1** Monitoring graphs
