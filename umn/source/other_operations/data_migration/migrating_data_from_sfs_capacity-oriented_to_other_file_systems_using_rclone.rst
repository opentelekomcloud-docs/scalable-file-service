:original_name: sfs_03_0036.html

.. _sfs_03_0036:

Migrating Data from SFS Capacity-Oriented to Other File Systems Using rclone
============================================================================

Solution Overview
-----------------

You can migrate data from SFS Capacity-Oriented to General-Purpose File System or SFS Turbo.

In this solution, a Linux ECS is used to connect the SFS Capacity-Oriented file system and the destination file system.

Constraints
-----------

-  Only Linux ECSs can be used for data migration.
-  The Linux ECS, SFS Capacity-Oriented file system, and destination file system must be in the same VPC. If the destination file system is a general-purpose file system, you need to configure a VPC endpoint.
-  Incremental migration is supported, so you can only migrate the changed data.

Prerequisites
-------------

-  You have created a Linux ECS.
-  You have created an SFS Capacity-Oriented file system and a destination file system and have obtained their mount points.

Procedure
---------

#. Log in to the ECS console.

#. Log in to the created Linux ECS, which can access both the SFS Capacity-Oriented and the destination file systems.

#. Mount the SFS Capacity-Oriented file system, which is *file system 1* in this example.

   .. code-block::

      mount -t nfs -o vers=3,timeo=600,noresvport,nolock <mount-point-of-file-system-1> /mnt/src

#. Mount the general-purpose file system or SFS Turbo file system, which is *file system 2* in this example.

   .. code-block::

      mount -t nfs -o vers=3,timeo=600,noresvport,nolock <mount-point-of-file-system-2> /mnt/dst

#. Install rclone on the Linux ECS.

   .. code-block::

      wget https://downloads.rclone.org/v1.53.4/rclone-v1.53.4-linux-amd64.zip --no-check-certificate
      unzip rclone-v1.53.4-linux-amd64.zip
      chmod 0755 ./rclone-*/rclone
      cp ./rclone-*/rclone /usr/bin/
      rm -rf ./rclone-*

   .. note::

      rclone does not retain the file permissions or owner group information on the source. Use rsync if you have such requirements.

#. Synchronize data to the destination file system.

   .. code-block::

      rclone copy /mnt/src /mnt/dst -P --transfers 32 --checkers 64 --links --create-empty-src-dirs

   .. note::

      The parameters are described as follows. Set **transfers** and **checkers** based on the system specifications.

      -  **/mnt/src**: source path
      -  **/mnt/dst**: destination path
      -  **--transfers**: number of files that can be transferred concurrently
      -  **--checkers**: number of local files that can be scanned concurrently
      -  **-P**: data copy progress
      -  **--links**: replicates the soft links from the source. They are saved as soft links in the destination.
      -  **--copy-links**: replicates the content of files to which the soft links point. They are saved as files rather than soft links in the destination.
      -  **--create-empty-src-dirs**: replicates the empty directories from the source to the destination.

   After data synchronization is complete, go to the destination file system to check whether data is migrated.

Verification
------------

#. Log in to the Linux ECS.

#. Check the file synchronization results on the destination server.

   .. code-block::

      cd /mnt/dst
      ls | wc -l

   If the data volume is the same as that on the source server, data is migrated successfully.
