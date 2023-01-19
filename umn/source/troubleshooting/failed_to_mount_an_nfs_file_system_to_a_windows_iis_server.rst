:original_name: sfs_01_0061.html

.. _sfs_01_0061:

Failed to Mount an NFS File System to a Windows IIS Server
==========================================================

Symptom
-------

When an NFS file system is mounted to a Windows IIS server, an error message is displayed, indicating that the path format is not supported, and the mounting fails.

Possible Causes
---------------

The physical path of the IIS Web server is incorrect.

Fault Diagnosis
---------------

Take troubleshooting measures based on possible causes.

Solution
--------

#. Log in to the ECS. The following operations use an ECS running Windows Server 2012 R2 as an example.

#. Click **Server Manager** in the lower left corner.

#. Choose **Tools** > **Internet Information Services (IIS) Manager**, expand **Sites**, and select the target website.

#. Click **Basic Settings** to check whether the **Physical path** is correct.

#. The correct physical path is that of the mount point with the colon (:) deleted.

   :ref:`Figure 1 <sfs_01_0061__fig047928192514>` shows the mount point of a file system. You need to enter the physical path **\\\\sfs-nas1.XXXXXXXXX.com\\share-396876e8**, as shown in :ref:`Figure 2 <sfs_01_0061__fig1734814414346>`.

   .. _sfs_01_0061__fig047928192514:

   .. figure:: /_static/images/en-us_image_0251367892.png
      :alt: **Figure 1** Mount point

      **Figure 1** Mount point

   .. _sfs_01_0061__fig1734814414346:

   .. figure:: /_static/images/en-us_image_0156988117.png
      :alt: **Figure 2** Physical path

      **Figure 2** Physical path
