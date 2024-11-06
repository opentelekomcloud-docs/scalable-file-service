:original_name: sfs_01_0053.html

.. _sfs_01_0053:

Media Processing
================

Context
-------

Media processing involves uploading, downloading, cataloging, transcoding, and archiving media materials, as well as storing, invoking, and managing audio and video data. Media processing has the following requirements on shared file systems:

-  Media materials feature a high video bit rate and a large scale. The capacity of file systems must be large and easy to be expanded.
-  Acquisition, editing, and synthesis of audio and video data require stable and low-latency file systems.
-  Concurrent editing requires file systems to deliver reliable and easy-to-use data sharing.
-  Video rendering and special effects need processing small files frequently. The file systems must offer high I/O performance.

SFS is a shared storage service based on file systems. It features high-speed data sharing, dynamic storage tiering, as well as on-demand, smooth, and online resizing. These outstanding features empower SFS to meet the demanding requirements of media processing on storage capacity, throughput, IOPS, and latency.

A TV channel has a large volume of audio and video materials to process. The work will be done on multiple editing workstations. The TV channel uses SFS to enable file sharing among the editing workstations. First, a file system is mounted to ECSs that function as upload workstations and editing workstations. Then raw materials are uploaded to the shared file system through the upload workstations. Then, the editing workstations concurrently edit the materials in the shared file system.

Configuration Process
---------------------

#. Organize the material files that are to be uploaded.
#. Log in to SFS Console. Create a file system to store the material files.
#. Log in to the ECSs that function as upload workstations and editing workstations, and mount the file system.
#. On the upload workstations, upload the material files to the file system.
#. On the editing stations, edit the material files.

Prerequisites
-------------

-  A VPC has been created.
-  ECSs that function as upload workstations and editing workstations have been created, and have been assigned to the VPC.
-  SFS has been enabled.

Example Configuration
---------------------

#. Log in to the SFS console.

#. In the upper right corner of the page, click **Create File System**.

#. On the **Create File System** page, set parameters as instructed.

#. After the configuration is complete, click **Create Now**.

   To mount a file system to Linux ECSs, see :ref:`Mounting an NFS File System to ECSs (Linux) <sfs_01_1001>`. To mount a file system to Windows ECSs, see :ref:`Mounting an NFS File System to ECSs (Windows) <en-us_topic_0105224109>`.

#. Log in to the upload workstations, and upload the material files to the file system.

#. Log in to the editing workstations, and edit the material files.
