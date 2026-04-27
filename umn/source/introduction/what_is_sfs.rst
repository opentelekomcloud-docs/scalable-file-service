:original_name: en-us_topic_0034428718.html

.. _en-us_topic_0034428718:

What Is SFS?
============

Overview
--------

Scalable File Service (SFS) provides scalable, high-performance NAS file storage. With SFS, you can enjoy shared file access spanning multiple Elastic Cloud Servers (ECSs), Bare Metal Servers (BMSs), and containers created on Cloud Container Engine (CCE), as shown in :ref:`Figure 1 <en-us_topic_0034428718__fig1762807410259>`.

.. _en-us_topic_0034428718__fig1762807410259:

.. figure:: /_static/images/en-us_image_0259710043.png
   :alt: **Figure 1** Accessing SFS

   **Figure 1** Accessing SFS

Compared with traditional shared file storage, SFS has the following advantages:

-  File sharing

   Cloud servers in multiple availability zones (AZs) of the same region can access the same file system concurrently and share files.

-  Elastic scaling

   Storage can be scaled up or down on demand to dynamically adapt to service changes without interrupting applications. You can complete resizing with a few clicks.

-  Superior performance

   File system performance increases as capacity grows. SFS can support rapid service growth while ensuring a high data durability.

   The background storage system supports HDD and SSD storage media. It adopts a distributed architecture and uses full redundant design for modules, eliminating single-node faults.

-  Seamless integration

   SFS supports Network File System (NFS), through which a broad range of applications can read data from and write data to the file system.

-  Easy operation

   On an intuitive graphical user interface (GUI), you can create and manage file systems with ease.

Accessing SFS
-------------

You can access SFS on the console or through APIs by sending HTTPS requests.

-  APIs

   Use APIs if you need to integrate SFS into a third-party system for secondary development. For detailed operations, see `Scalable File Service API Reference <https://docs.otc.t-systems.com/en-us/api/sfs/sfs_02_0001.html>`__.

-  Console

   Use the console if you prefer a web-based UI to perform operations.
