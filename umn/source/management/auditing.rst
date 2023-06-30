:original_name: sfs_01_0050.html

.. _sfs_01_0050:

Auditing
========

Scenarios
---------

Cloud Trace Service (CTS) records operations of SFS resources, facilitating query, audit, and backtracking.

Prerequisites
-------------

You have enabled CTS and the tracker is normal. For details about how to enable CTS, see section "Enabling CTS" in the *Cloud Trace Service User Guide.*

Operations
----------

.. table:: **Table 1** SFS operations traced by CTS

   ============================== ============= ===============
   Operation                      Resource Type Trace
   ============================== ============= ===============
   Creating a shared file system  sfs           createShare
   Modifying a shared file system sfs           updateShareInfo
   Deleting a shared file system  sfs           deleteShare
   Adding a share access rule     sfs           addShareACL
   Deleting a share access rule   sfs           deleteShareACL
   Expanding a shared file system sfs           extendShare
   Shrinking a shared file system sfs           shrinkShare
   ============================== ============= ===============

.. _sfs_01_0050__table11412122812424:

.. table:: **Table 2** SFS Turbo operations traced by CTS

   ====================== ============= ===========
   Operation              Resource Type Trace
   ====================== ============= ===========
   Creating a file system sfs_turbo     createShare
   Deleting a file system sfs_turbo     deleteShare
   ====================== ============= ===========

Querying Traces
---------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and project.

#. Choose **Management & Deployment** > **Cloud Trace Service**.

   The **Cloud Trace Service** page is displayed.

#. In the navigation pane on the left, choose **Trace List**.

#. On the trace list page, set **Trace Source**, **Resource Type**, and **Search By**, and click **Query** to query the specified traces.

   For details about other operations, see section "Querying Real-Time Traces" in the *Cloud Trace Service User Guide*.

Disabling or Enabling a Tracker
-------------------------------

This section describes how to disable an existing tracker on the CTS console. After the tracker is disabled, the system will stop recording operations, but you can still view existing operation records.

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and project.

#. Choose **Management & Deployment** > **Cloud Trace Service**.

   The **Cloud Trace Service** page is displayed.

#. Click **Trackers** in the left pane.

#. Click **Disable** on the right of the tracker information.

#. Click **Yes**.

#. After the tracker is disabled, the available operation changes from **Disable** to **Enable**. To enable the tracker again, click **Enable** and then click **Yes**. The system will start recording operations again.

.. |image1| image:: /_static/images/en-us_image_0000001567316929.jpg
.. |image2| image:: /_static/images/en-us_image_0000001567316929.jpg
