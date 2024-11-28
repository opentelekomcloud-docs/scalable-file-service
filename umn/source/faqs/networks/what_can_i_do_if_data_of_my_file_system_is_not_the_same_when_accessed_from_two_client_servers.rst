:original_name: sfs_01_0082.html

.. _sfs_01_0082:

What Can I Do If Data of My File System Is Not the Same When Accessed from Two Client Servers?
==============================================================================================

Symptom
-------

A file system was mounted to two servers. There was a delay in synchronizing files from one server to another. However, there was no delay when files were uploaded to a server.

Fault Diagnosis
---------------

Add **noac, lookupcache=none** to the mount command.

The **noac** option disables file attribute caching and forces write synchronization. By default, an NFS client's file attribute information is cached using the **ac** option to improve performance, and the client checks file attribute information periodically and updates it if there are any changes. Within the cache validity period, the client does not check whether file attribute information on the server is changed. By default, the value of this option is **ac**. Set it to **noac**.

The **lookupcache** option is related to directory entry caching, and the value can be **all**, **none**, **pos**, or **positive**. With **lookupcache=none**, the client neither trust the positive nor negative lookup results. In this way, lookup caching is disabled.

Solution
--------

#. Unmount the file system if it has been mounted. To unmount a file system, see :ref:`Unmount a File System <sfs_01_0026>`.

#. Complete the preparations before mounting the file system. For details, see :ref:`Mounting an NFS File System to ECSs (Linux) <sfs_01_1001>`.

#. Mount the file system.

   .. code-block::

      mount -t nfs -o vers=3,timeo=600,noac,lookupcache=none,noresvport,nolock Shared path Local path
