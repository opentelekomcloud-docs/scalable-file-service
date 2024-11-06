:original_name: sfs_01_0060.html

.. _sfs_01_0060:

Data Fails to Be Written into a File System Mounted to ECSs Running Different Types of Operating Systems
========================================================================================================

Symptom
-------

If a file system is mounted to a Linux ECS and a Windows ECS, on the Windows ECS, data cannot be written to the files created by the Linux ECS.

Possible Causes
---------------

A shared NFS file system belongs to the root user and cannot be modified. The write permission is granted to a user only when both the values of UID and GID of the user are **0**. You can check your UID using Windows commands. If the value of UID is, for example, **-2**, you do not have the write permission.

Fault Diagnosis
---------------

To address this problem, modify the registry and change both UID and GID values to **0** for NFS accesses from Windows.

Solution
--------

#. Choose **Start** > **Run** and enter **regedit** to open the registry.

#. Enter the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\ClientForNFS\\CurrentVersion\\Default** directory. :ref:`Figure 1 <sfs_01_0060__fig103481655182917>` shows an example of the directory.

   .. _sfs_01_0060__fig103481655182917:

   .. figure:: /_static/images/en-us_image_0123076280.png
      :alt: **Figure 1** Entering the directory

      **Figure 1** Entering the directory

#. Right-click the blank area and choose **New** > **DWORD Value** from the shortcut menu. Set **AnonymousUid** and **AnonymousGid** to **0**. :ref:`Figure 2 <sfs_01_0060__fig56963212379>` shows a successful operation.

   .. _sfs_01_0060__fig56963212379:

   .. figure:: /_static/images/en-us_image_0132187573.png
      :alt: **Figure 2** Adding values

      **Figure 2** Adding values

#. After modifying the registry, restart the server for the modification to take effect.
