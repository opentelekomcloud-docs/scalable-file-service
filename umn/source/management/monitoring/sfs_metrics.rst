:original_name: sfs_01_0047.html

.. _sfs_01_0047:

SFS Metrics
===========

General purpose file systems do not support monitoring. This section describes only the monitoring metrics of SFS Capacity-Oriented.

Function
--------

This section describes the SFS metrics reported to Cloud Eye as well as their namespaces and dimensions. You can use the Cloud Eye console or APIs provided by Cloud Eye to query the SFS metrics and alarms.

.. note::

   Cloud Eye can monitor dimensions nested to a maximum depth of four levels (levels 0 to 3). 3 is the deepest level.

Namespace
---------

SYS.SFS

Metrics
-------

.. table:: **Table 1** SFS metrics

   +-----------------+--------------------------+-----------------------------------------------------------------------+-------------+---------+-----------------+-----------+------------------------------+
   | Metric ID       | Metric Name              | Description                                                           | Value Range | Unit    | Conversion Rule | Dimension | Monitoring Period (Raw Data) |
   +=================+==========================+=======================================================================+=============+=========+=================+===========+==============================+
   | read_bandwidth  | Read Bandwidth           | Read bandwidth of a file system within a monitoring period            | >= 0        | bytes/s | 1024 (IEC)      | share_id  | 4 minutes                    |
   +-----------------+--------------------------+-----------------------------------------------------------------------+-------------+---------+-----------------+-----------+------------------------------+
   | write_bandwidth | Write Bandwidth          | Write bandwidth of a file system within a monitoring period           | >= 0        | bytes/s | 1024 (IEC)      | share_id  | 4 minutes                    |
   +-----------------+--------------------------+-----------------------------------------------------------------------+-------------+---------+-----------------+-----------+------------------------------+
   | rw_bandwidth    | Read and Write Bandwidth | Read and write bandwidth of a file system within a monitoring period  | >= 0        | bytes/s | 1024 (IEC)      | share_id  | 4 minutes                    |
   +-----------------+--------------------------+-----------------------------------------------------------------------+-------------+---------+-----------------+-----------+------------------------------+
   | read_ops        | Read OPS                 | Read operations of a file system within a monitoring period           | >= 0        | count/s | N/A             | share_id  | 4 minutes                    |
   +-----------------+--------------------------+-----------------------------------------------------------------------+-------------+---------+-----------------+-----------+------------------------------+
   | write_ops       | Write OPS                | Write operations of a file system within a monitoring period          | >= 0        | count/s | N/A             | share_id  | 4 minutes                    |
   +-----------------+--------------------------+-----------------------------------------------------------------------+-------------+---------+-----------------+-----------+------------------------------+
   | rw_ops          | Read Write OPS           | Read and write operations of a file system within a monitoring period | >= 0        | count/s | N/A             | share_id  | 4 minutes                    |
   +-----------------+--------------------------+-----------------------------------------------------------------------+-------------+---------+-----------------+-----------+------------------------------+
   | used_capicity   | Used Capacity            | Used capacity of a file system within a monitoring period             | >= 0        | bytes   | 1024 (IEC)      | share_id  | 4 minutes                    |
   +-----------------+--------------------------+-----------------------------------------------------------------------+-------------+---------+-----------------+-----------+------------------------------+

Dimension
---------

======== =====================
Key      Value
======== =====================
share_id SFS Capacity-Oriented
======== =====================

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
