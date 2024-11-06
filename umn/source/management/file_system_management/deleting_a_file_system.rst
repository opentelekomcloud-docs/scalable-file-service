:original_name: sfs_01_0347.html

.. _sfs_01_0347:

Deleting a File System
======================

Data in a deleted file system cannot be restored. Ensure that files in a file system have been properly stored or backed up before you delete the file system.

Prerequisites
-------------

The file system to be deleted has been unmounted. For details about how to unmount the file system, see :ref:`Unmount a File System <sfs_01_0026>`.

Procedure
---------

#. Log in to the SFS console.

#. In the file system list, locate the file system you want to delete and click **Delete** in the **Operation** column.

   If you want to delete more than one file system at a time, select the file systems, and then click **Delete** in the upper left part above the file system list. In the displayed dialog box, confirm the information and then click **OK**. Batch deletion is only supported for SFS Capacity-Oriented file systems.

#. In the displayed dialog box for an SFS Turbo file system, as shown in :ref:`Figure 1 <sfs_01_0347__fig10624128141112>`, confirm the information, enter **DELETE** in the text box, and click **OK**.

   In the displayed dialog box for an SFS Capacity-Oriented or a general purpose file system, confirm the information and click **OK**.

   .. note::

      Only **Available** and **Unavailable** file systems can be deleted.

   .. _sfs_01_0347__fig10624128141112:

   .. figure:: /_static/images/en-us_image_0000001921910840.png
      :alt: **Figure 1** Deleting an SFS Turbo file system

      **Figure 1** Deleting an SFS Turbo file system

#. Check that the file system disappears from the file system list.
