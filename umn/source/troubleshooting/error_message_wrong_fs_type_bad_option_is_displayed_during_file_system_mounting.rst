:original_name: sfs_01_0062.html

.. _sfs_01_0062:

Error Message "wrong fs type, bad option" Is Displayed During File System Mounting
==================================================================================

Symptom
-------

The message "wrong fs type, bad option" is displayed when you run the **mount** command to mount a file system to an ECS running Linux.

Possible Causes
---------------

An NFS client is not installed on the Linux ECS. That is, the **nfs-utils** software package is not installed before you execute the **mount** command.

Fault Diagnosis
---------------

Install the required **nfs-utils** software package.

Solution
--------

#. Log in to the ECS and check whether the **nfs-utils** package is installed. Run the following command. If no command output is displayed, the package is not installed.

   .. code-block::

      rpm -qa|grep nfs


   .. figure:: /_static/images/en-us_image_0205874230.png
      :alt: **Figure 1** Checking whether the software package has been installed

      **Figure 1** Checking whether the software package has been installed

#. Run the following command to install the nfs-utils software package:

   .. code-block::

      yum -y install nfs-utils


   .. figure:: /_static/images/en-us_image_0205880095.png
      :alt: **Figure 2** Executing the installation command

      **Figure 2** Executing the installation command


   .. figure:: /_static/images/en-us_image_0205880066.png
      :alt: **Figure 3** Successful installation

      **Figure 3** Successful installation

#. Run the **mount** command again to mount the file system to the ECS.

   .. code-block::

      mount -t nfs -o vers=3,timeo=600,noresvport,nolock Mount point Local path

#. Run the following command to view the mounted file system:

   **mount -l**

   If the command output contains the following information, the file system is mounted successfully.

   .. code-block::

      example.com:/share-xxx on /local_path type nfs (rw,vers=3,timeo=600,nolock,addr=)
