:original_name: sfs_01_0026.html

.. _sfs_01_0026:

Unmount a File System
=====================

If a file system is no longer used and needs to be deleted, you are advised to unmount the file system and then delete it.

Prerequisites
-------------

Before unmounting a file system, stop the process and read/write operations.

Linux OS
--------

#. Log in to the management console using a cloud account.

   a. Log in to the management console and select a region and a project.
   b. Under **Computing**, click **Elastic Cloud Server** to go to the ECS console.

#. Log in to the ECS.

#. Run the following command:

   **umount** *Local path*

   *Local path*: An ECS local directory where the file system is mounted, for example, **/local_path**.

   .. note::

      Before running the **umount** command, stop all read and write operations related to the file system and exit from the local path. Or, the unmounting will fail.

Windows OS
----------

#. Log in to the management console using a cloud account.

   a. Log in to the management console and select a region and a project.
   b. Under **Computing**, click **Elastic Cloud Server** to go to the ECS console.

#. Log in to the ECS.

#. Right-click the file system to be unmounted and choose **Disconnect**.


   .. figure:: /_static/images/en-us_image_0000001268123369.png
      :alt: **Figure 1** Unmounting

      **Figure 1** Unmounting

#. If the file system disappears from the network location, it has been unmounted.
