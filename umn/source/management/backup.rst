:original_name: sfs_01_0044.html

.. _sfs_01_0044:

Backup
======

You can only back up SFS Turbo file systems using CBR while you cannot back up SFS Capacity-Oriented and general purpose file systems.

Scenarios
---------

A backup is a complete copy of an SFS Turbo file system at a specific time and it records all configuration data and service data at that time.

For example, if a file system is faulty or encounters a logical error (for example, mis-deletion, hacker attacks, and virus infection), you can use data backups to restore data quickly.

Creating a File System Backup
-----------------------------

Ensure that the target file system is available. Or, the backup task cannot start. This procedure describes how to manually create a file system backup.

.. note::

   If any modification is made to a file system during the backup, inconsistencies may occur. For example, there may be duplicate or deleted data, or data discrepancies. Such a modification includes a write, rename, move or delete. To ensure backup data consistency, you are advised to stop the applications or programs that use the file system during the backup, or schedule the backup at off-peak hours.

#. Log in to CBR Console.

#. In the navigation pane on the left, choose **SFS Turbo Backups**.

#. Create a backup vault by referring to section "Creating an SFS Turbo Backup Vault" and then create a backup by referring to section "Creating an SFS Turbo Backup" in the *Cloud Backup and Recovery User Guide*.

#. The system automatically backs up the file system.

   You can view the backup creation status on the **Backups** tab page. When the **Status** of the backup changes to **Available**, the backup has been created.

#. If the file system becomes faulty or an error occurred, you can restore the backup data to a new file system. For details, see :ref:`Using a Backup to Create a File System <sfs_01_0044__section1629635834112>`.

.. _sfs_01_0044__section1629635834112:

Using a Backup to Create a File System
--------------------------------------

In case of a virus attack, accidental deletion, or software or hardware fault, you can use an SFS Turbo file system backup to create a new file system. Data on the new file system is the same as that in the backup.

#. Log in to CBR Console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner and select your desired region and project.
   c. Choose **Storage** > **Cloud Backup and Recovery** > **SFS Turbo Backups**.

#. Click the **Backups** tab and locate the desired backup.

#. If the status of the target backup is **Available**, click **Create File System** in the **Operation** column of the backup.

#. Set the file system parameters. See :ref:`Figure 1 <sfs_01_0044__fig126043518315>`.

   .. _sfs_01_0044__fig126043518315:

   .. figure:: /_static/images/en-us_image_0000001357615949.png
      :alt: **Figure 1** Create File System

      **Figure 1** Create File System

   .. note::

      -  For detailed parameter descriptions, see table "Parameter description" under :ref:`Table 3 <en-us_topic_0034428727__table724582213143>`.

#. Click **Next**.

#. Go back to the file system list and check whether the file system is successfully created.

   You will see the file system status change as follows: **Creating**, **Available**, **Restoring**, **Available**. You may not notice the **Restoring** status because Instant Restore is supported and the restoration speed is very fast. After the file system status has changed from **Creating** to **Available**, the file system is successfully created. After the status has changed from **Restoring** to **Available**, backup data has been successfully restored to the created file system.

.. |image1| image:: /_static/images/en-us_image_0000001304536416.png
