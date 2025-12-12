:original_name: sfs_03_0038.html

.. _sfs_03_0038:

Migrating Data from SFS Capacity-Oriented to SFS Turbo Using fpart
==================================================================

Solution Overview
-----------------

This section describes how to use fpart to migrate data from SFS Capacity-Oriented to SFS Turbo. The migration aims to efficiently and securely migrate data while ensuring data integrity and consistency. The entire process includes a full migration (no impact on services), a first incremental migration (no impact on services), unmounting the SFS Capacity-Oriented file system (services are interrupted), a second incremental migration (services are interrupted), and changing the mount point (services are interrupted).

Constraints
-----------

-  This solution is only applicable for the data migration using Linux ECSs.
-  The Linux ECS, SFS Capacity-Oriented file system, and SFS Turbo file system must be in the same VPC.
-  This solution is not applicable for SFS Capacity-Oriented file systems using CIFS or those mounted on Windows clients.
-  If the SFS Turbo file system is used by a CCE cluster, the CCE cluster must be upgraded to version 1.15+, and the everest add-on version must be later than 1.1.13.

Solution Architecture
---------------------


.. figure:: /_static/images/en-us_image_0000002381131769.png
   :alt: **Figure 1** Process of migrating data from SFS Capacity-Oriented to SFS Turbo using fpart

   **Figure 1** Process of migrating data from SFS Capacity-Oriented to SFS Turbo using fpart

Preparations
------------

#. Create an SFS Turbo file system in the VPC where the SFS Capacity-Oriented file system resides. If no VPC is available, create one in the same region and then create the SFS Turbo file system. For how to create an SFS Turbo file system, see :ref:`Creating an SFS Turbo File System <en-us_topic_0034428727__section761663912242>`. For details about how to create a VPC, see section "Creating a VPC with a Subnet" in the *Virtual Private Cloud User Guide*.

#. If a Linux ECS is available, skip this step. If not, buy a Linux ECS. You are advised to buy an ECS with 8 or 16 vCPUs. This ECS must be in the VPC where the SFS Capacity-Oriented and SFS Turbo file systems belong and can communicate with the file systems.

#. Install fpart on the Linux ECS.

   .. code-block::

      yum -y install fpart rsync

#. Create two local mount points on the Linux ECS.

   .. code-block::

      mkdir /mnt/src

   .. code-block::

      mkdir /mnt/dst

#. Obtain the mount points of the SFS Capacity-Oriented and SFS Turbo file systems from the console. Then, mount the file systems on the created local mount points (**/mnt/src** and **/mnt/dst**).

   .. code-block::

      mount -t nfs -o vers=3,timeo=600,nolock <mount-point-of-the-SFS-Capacity-Oriented-file-system> /mnt/src

   .. code-block::

      mount -t nfs -o vers=3,timeo=600,nolock <mount-point-of-the-SFS-Turbo-file-system> /mnt/dst

#. If the mount fails, install the required tool package by referring to section "Mounting an NFS File System to ECSs (Linux)" in the *Scalable File Service Getting Started*.

Procedure
---------

#. Full migration: Migrate all files from the SFS Capacity-Oriented file system to the SFS Turbo file system.

   a. Log in to the ECS using VNC and run the following command to synchronize data:

      .. code-block::

         fpsync -n 500 -f 500 -o "-lptgoDvu --numeric-ids" -v /mnt/src/ /mnt/dst/

      .. note::

         -  **n**: the number of parallel copy threads
         -  **f**: the number of files each thread can copy
         -  **o**: the rsync configuration option
         -  **v**: the output detailed logs
         -  If there are a large number of files, you can run the command concurrently for the subdirectories in **/mnt/src**.
         -  You can adjust the **n** and **f** options based on the file and directory structure.

   b. The default run log files are stored in **/tmp/fpsync**, under which **log** stores task run logs, **parts** stores file partition logs, **queue** stores execution configurations, and **work** stores the copy commands. You can check the task running status based on these logs.

#. First incremental migration: Synchronize the incremental data generated after the full migration to the SFS Turbo file system.

   .. code-block::

      fpsync -n 500 -f 500 -o "-lptgoDvu --numeric-ids" -v /mnt/src/ /mnt/dst/

   .. important::

      Take note of the start time and end time of this operation. This period is approximately equal to how long customer services need to be stopped in the following steps.

#. Unmounting the SFS Capacity-Oriented file system: To prevent new data from being written to the file system, before synchronizing the incremental data, stop the service application that uses the source file system on all ECSs and containers.

   .. caution::

      -  Ensure that the SFS Capacity-Oriented file system is unmounted from all service ECSs (or cloud containers). Otherwise, after the migration, data in the SFS Turbo file system may be inconsistent with that in the SFS Capacity-Oriented file system.
      -  Do not unmount the SFS Capacity-Oriented file system from the ECS that you use to perform the migration.
      -  The operations vary in ECS and CCE scenarios. Refer to the operations based on your scenario.
      -  Ensure that services are stopped when you perform this step.

   **ECS scenario:**

   a. Log in to each service ECS that mounts the SFS Capacity-Oriented file system.

   b. Unmount the SFS Capacity-Oriented file system.

      .. code-block::

         umount -f <local-mount-point>

#. Second incremental migration: Synchronize the incremental data generated after the first incremental migration to the SFS Turbo file system. After the synchronization, data in the SFS Turbo file system will be the same as that in the SFS Capacity-Oriented file system.

   .. code-block::

      fpsync -n 500 -f 500 -o "-lptgoDvu --numeric-ids" -v /mnt/src/ /mnt/dst/

   .. caution::

      -  Check that data in the SFS Turbo file system is the same as that in the SFS Capacity-Oriented file system.
      -  Ensure that services are stopped when you perform this step.

#. Mounting the SFS Turbo file system: Switch the service to the SFS Turbo file system by mounting all service ECSs (or cloud containers) to the SFS Turbo file system.

   **ECS scenario:**

   a. Log in to the service ECS and run the following command to unmount the SFS Capacity-Oriented file system:

      .. code-block::

         umount -f <local-mount-point>

   b. Mount the SFS Turbo file system.

      .. code-block::

         mount -t nfs -o vers=3,nolock <mount-point-of-the-SFS-Turbo-file-system>

   .. caution::

      -  Ensure that the mount parameters and directories are correct. Or, services may be affected.

#. The customer restores services and checks whether services are normal.

#. After observing the services for a period of time, the customer can release the SFS Capacity-Oriented file system resources to prevent unintended charges.
