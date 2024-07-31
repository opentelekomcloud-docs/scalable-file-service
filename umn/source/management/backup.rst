:original_name: sfs_01_0044.html

.. _sfs_01_0044:

Backup
======

Only SFS Turbo file systems can be backed up using CBR while SFS Capacity-Oriented file systems cannot.

Scenarios
---------

A backup is a complete copy of an SFS Turbo file system at a specific time and it records all configuration data and service data at that time.

For example, if a file system is faulty or encounters a logical error (for example, mis-deletion, hacker attacks, and virus infection), you can use data backups to restore data quickly.

Creating a File System Backup
-----------------------------

Ensure that the target file system is available. Or, the backup task cannot start. This procedure describes how to manually create a file system backup.

#. Log in to CBR Console.

#. In the navigation pane on the left, choose **SFS Turbo Backups**.

#. Create a backup vault by following the instructions in section "Creating an SFS Turbo Backup Vault" in the *Cloud Backup and Recovery User Guide*. Then, create a backup by following the instructions in section "Creating an SFS Turbo Backup."

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

#. If the status of the target backup is **Available**, click **Create New File System** in the **Operation** column of the backup.

#. Set the file system parameters. See :ref:`Figure 1 <sfs_01_0044__fig126043518315>`.

   .. _sfs_01_0044__fig126043518315:

   .. figure:: /_static/images/en-us_image_0000001516396508.png
      :alt: **Figure 1** Create File System

      **Figure 1** Create File System

   .. note::

      -  For detailed parameter descriptions, see table "Parameter description" under :ref:`Creating an SFS Turbo File System <en-us_topic_0034428727__table724582213143>`.

#. Click **Next**.

#. Go back to the file system list and check whether the file system is successfully created.

   You will see the file system status change as follows: **Creating**, **Available**, **Restoring**, **Available**. You may not notice the **Restoring** status because Instant Restore is supported and the restoration speed is very fast. After the file system status has changed from **Creating** to **Available**, the file system is successfully created. After the status has changed from **Restoring** to **Available**, backup data has been successfully restored to the created file system.

.. |image1| image:: /_static/images/en-us_image_0000001516236528.png
