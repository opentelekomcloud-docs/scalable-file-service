:original_name: sfs_01_0054.html

.. _sfs_01_0054:

Enterprise Website/App Background
=================================

Context
-------

For I/O-intensive website services, SFS Turbo can provide shared website source code directories and storage for multiple web servers, enabling low-latency and high-IOPS concurrent share access. Features of such services are as follows:

-  A large number of small files: Static website files need to be stored, including HTML files, JSON files, and static images.
-  Read I/O intensive: Scope of data reading is large, and data writing is relatively small.
-  Multiple web servers access an SFS Turbo background to achieve high availability of website services.

Configuration Process
---------------------

#. Sort out the website files.
#. Log in to the SFS console. Create an SFS Turbo file system to store the website files.
#. Log in to the server that functions as the compute node and mount the file system.
#. On the head node, upload the files to the file system.
#. Start the web server.

Prerequisites
-------------

-  A VPC has been created.
-  Servers that function as head nodes and compute nodes have been created, and have been assigned to the VPC.
-  SFS has been enabled.

Example Configuration
---------------------

#. Log in to the SFS console.

#. In the navigation pane on the left, choose **SFS Turbo** > **File Systems**. In the upper right corner of the page, click **Create File System**.

#. On the **Create File System** page, set parameters as instructed.

#. After the configuration is complete, click **Create Now**.

   To mount a file system to Linux ECSs, see :ref:`Mounting an NFS File System to ECSs (Linux) <sfs_01_1001>`. To mount a file system to Windows ECSs, see :ref:`Mounting an NFS File System to ECSs (Windows) <en-us_topic_0105224109>`.

#. Log in to the head node and upload the files to the file system.

#. Start the web server.
