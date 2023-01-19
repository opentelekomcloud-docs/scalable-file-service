:original_name: sfs_01_0034.html

.. _sfs_01_0034:

File System Management
======================

Viewing a File System
---------------------

You can search for file systems by file system name keyword or file system status, and view their basic information.

Procedure
---------

#. Log in to SFS Console.

#. In the file system list, view the file systems you have created. :ref:`Table 1 <sfs_01_0034__table37365828114557>` describes the parameters of each file system.

   .. _sfs_01_0034__table37365828114557:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================================================+
      | Name                              | Name of the file system, for example, **sfs-name-001**                                                                                                                                                                                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | Availability zone where the file system is located                                                                                                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Status                            | Possible values are **Available**, **Unavailable**, **Frozen**, **Creating**, **Deleting**, **Deletion error**, **Expanding**, **Expansion error**, **Capacity reducing**, **Capacity reduction error**, and **Capacity reduction failed**. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol Type                     | The NFS protocol is supported.                                                                                                                                                                                                              |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Available Capacity (GB)           | Available space of the file system for storing data                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                             |
      |                                   |    This information is refreshed every 15 minutes.                                                                                                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Maximum Capacity (GB)             | Maximum capacity of the file system                                                                                                                                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Encrypted                         | Encryption status of the created file system. The value can be **Yes** or **No**.                                                                                                                                                           |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Mount Address                     | File system mount point. The format is *File system domain name*\ **:/**\ *path* or *File system IP address*\ **:/**.                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                             |
      |                                   |    If the mount point is too long to display completely, you can adjust the column width.                                                                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                         | For an SFS Capacity-Oriented file system, operations include resizing, deletion, and monitoring indicator viewing.                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                             |
      |                                   | For an SFS Turbo file system, operations include capacity expansion, deletion, and monitoring indicator viewing.                                                                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click the name of a file system to view detailed information about the file system. See :ref:`Figure 1 <sfs_01_0034__fig964613241271>`.

   .. _sfs_01_0034__fig964613241271:

   .. figure:: /_static/images/en-us_image_0251346744.png
      :alt: **Figure 1** File system information

      **Figure 1** File system information

#. (Optional) Search for file systems by file system name keyword, key ID, or file system status.

   In the upper right corner of the page, click **Search by Tag** to query the file systems by tag.

   -  On the **Search by Tag** tab page that is displayed, enter a tag key and a tag value (must be among existing keys and values) and click **Search**.
   -  You can use more than one tag for a combination search. Each time after a key and a value are entered, click |image1|. The added tag search criteria are displayed under the text boxes. When more than one tag is added, they will be applied together for a combination search. A maximum of 10 tags can be added at one time.
   -  You can click **Reset** under the search criteria to reset.

Deleting a File System
----------------------

After a file system is deleted, data in it cannot be restored. To prevent data loss, before deleting a file system, ensure that files in it have been backed up.

Prerequisites
-------------

You have unmounted the file system to be deleted. For details about how to unmount the file system, see :ref:`Unmounting a File System <sfs_01_0026>`.


Procedure
---------

#. Log in to SFS Console.

#. In the file system list, click **Delete** in the row of the file system you want to delete. If you want to delete more than one file system at a time, select the file systems, and then click **Delete** in the upper left part of the file system list. In the dialog box that is displayed, confirm the information, enter **Delete** in the text box, and then click **Yes**. The batch deletion function can be used to delete SFS file systems only.

#. In the displayed dialog box, as shown in :ref:`Figure 2 <sfs_01_0034__fig51368710153938>`, confirm the information, and then click **Yes**.

   .. note::

      Only **Available** and **Unavailable** file systems can be deleted.

   .. _sfs_01_0034__fig51368710153938:

   .. figure:: /_static/images/en-us_image_0176685807.png
      :alt: **Figure 2** Deleting a file system

      **Figure 2** Deleting a file system

#. Check the file system list to confirm that the file system is deleted successfully.

.. |image1| image:: /_static/images/en-us_image_0111943266.png
