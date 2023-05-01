:original_name: en-us_topic_0034428718.html

.. _en-us_topic_0034428718:

What Is SFS?
============

Overview
--------

Scalable File Service (SFS) provides scalable, high-performance (NAS) file storage. With SFS, you can enjoy shared file access spanning multiple Elastic Cloud Servers (ECSs), Bare Metal Servers (BMSs), and containers created on Cloud Container Engine (CCE). See :ref:`Figure 1 <en-us_topic_0034428718__fig1762807410259>`.

.. _en-us_topic_0034428718__fig1762807410259:

.. figure:: /_static/images/en-us_image_0000001516236400.png
   :alt: **Figure 1** Accessing SFS

   **Figure 1** Accessing SFS

Compared with traditional file sharing storage, SFS has the following advantages:

-  File sharing

   Servers in multiple availability zones (AZs) of a same region can access the same file system concurrently and share files.

-  Elastic scaling

   Storage can be scaled up or down on demand to dynamically adapt to service changes without interrupting applications. You can complete resizing with a few clicks.

-  Superior performance

   The service enables file system performance to increase as capacity grows, and delivers a high data durability to support rapid service growth.

-  Seamless integration

   SFS supports Network File System (NFS). With this standard protocol, a broad range of mainstream applications can read and write data in the file system.

-  Easy operation

   In an intuitive graphical user interface (GUI), you can create and manage file systems with ease.

Accessing SFS
-------------

You can access SFS on the management console or via APIs by sending HTTPS requests.

-  APIs

   Use APIs if you need to integrate SFS into a third-party system for secondary development. For detailed operations, see `Scalable File Service API Reference <https://docs.otc.t-systems.com/en-us/api/sfs/sfs_02_0001.html>`__.

-  Management console

   Use the console if you prefer a web-based UI to perform operations.
