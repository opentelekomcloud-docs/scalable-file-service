:original_name: sfs_01_0117.html

.. _sfs_01_0117:

Migrating Data Between File Systems
===================================

Solution Overview
-----------------

You can migrate data from an SFS Capacity-Oriented file system to an SFS Turbo file system or the other way around.

This solution creates a Linux ECS to connect an SFS Capacity-Oriented file system with an SFS Turbo file system.

Limitations and Constraints
---------------------------

-  Only Linux ECSs can be used to migrate data.
-  The Linux ECS, SFS Capacity-Oriented file system, and SFS Turbo file system must be in the same VPC.
-  Incremental migration is supported, so that only changed data is migrated.

Prerequisites
-------------

-  You have created a Linux ECS.
-  You have created an SFS Capacity-Oriented file system and an SFS Turbo file system and have obtained their mount points.

Procedure
---------

#. Log in to the ECS console.

#. Log in to the created Linux ECS that can access SFS Capacity-Oriented and SFS Turbo file systems.

#. Run the following command to mount file system 1 (either the SFS Capacity-Oriented or SFS Turbo file system). After that, you can access file system 1 on the Linux ECS.

   .. code-block::

      mount -t nfs -o vers=3,timeo=600,noresvport,nolock [Mount point of file system 1] /mnt/src

#. Run the following command to mount file system 2 (the other file system that you have not mounted in the previous step). After that, you can access file system 2 on the Linux ECS.

   .. code-block::

      mount -t nfs -o vers=3,timeo=600,noresvport,nolock [Mount point of file system 2] /mnt/dst

#. Run the following commands on the Linux ECS to install the rclone tool:

   .. code-block::

      wget https://downloads.rclone.org/v1.53.4/rclone-v1.53.4-linux-amd64.zip --no-check-certificate
      unzip rclone-v1.53.4-linux-amd64.zip
      chmod 0755 ./rclone-*/rclone
      cp ./rclone-*/rclone /usr/bin/
      rm -rf ./rclone-*

#. Run the following command to synchronize data:

   .. code-block::

      rclone copy /mnt/src /mnt/dst -P --transfers 32 --checkers 64

   .. note::

      Set **transfers** and **checkers** based on the system specifications. The parameters are described as follows:

      -  **transfers**: number of files that can be transferred concurrently
      -  **checkers**: number of files that can be scanned concurrently
      -  **P**: data copy progress

   After data synchronization is complete, go to the target file system to check whether data is migrated.

Verification
------------

#. Log in to the created Linux ECS.

#. Run the following commands on the destination server to verify file synchronization:

   .. code-block::

      cd /mnt/dst
      ls | wc -l

#. If the data volume is the same as that on the source server, the data is migrated successfully.
