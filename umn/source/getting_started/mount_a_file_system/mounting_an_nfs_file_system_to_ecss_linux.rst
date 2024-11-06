:original_name: sfs_01_1001.html

.. _sfs_01_1001:

Mounting an NFS File System to ECSs (Linux)
===========================================

After creating a file system, you need to mount the file system to servers so that they can share the file system.

In this section, ECSs are used as example servers. Operations on BMSs and containers (CCE) are the same as those on ECSs.

General purpose file systems cannot be mounted to 32-bit Linux servers.

Prerequisites
-------------

-  You have checked the type of the operating system on each ECS. Different operating systems use different commands to install the NFS client.
-  You have created a file system and have obtained the mount point of the file system.
-  At least one ECS that belongs to the same VPC as the file system exists.
-  The IP address of the DNS server for resolving the domain names of the file systems has been configured on the ECS. SFS Turbo file systems do not require domain name resolution.

Constraints
-----------

.. note::

   This constraint only applies to local paths (mount points) and does not affect other files or directories.

Metadata of the local paths (mount points) cannot be modified. Specifically, the following operations cannot be performed on the local paths' metadata:

**- touch**: Update file access time and modification time.

**- rm**: Delete files or directories.

**- cp**: Replicate files or directories.

**- mv**: Move files or directories.

**- rename**: Rename files or directories.

**- chmod**:Modify permissions on files or directories.

**- chown**: Change file or directory owners.

**- chgrp**: Change file or directory groups.

**- ln**: Create hard links.

**- link**: Create hard links.

**- unlink**: Delete hard links.

The **atime**, **ctime**, and **mtime** attributes of a local path (root directory of the mount point) are the current time. So each time the root directory attribute is queried, the current time of the server is returned.

Procedure
---------

#. Log in to the management console using a cloud account.

   a. Log in to the management console and select a region and a project.
   b. Under **Computing**, click **Elastic Cloud Server** to go to the ECS console.

#. Log in to the ECS as user **root**.

   .. note::

      If you log in to the ECS as a non-root user, see :ref:`Mounting a File System to a Linux ECS as a Non-root User <sfs_01_0100>`.

#. Install the NFS client.

   a. **Install the NFS client.**

      #. Run the following command to check whether the NFS software package is installed.

         -  In CentOS, Red Hat, Oracle Enterprise Linux, SUSE, EulerOS, Fedora, or OpenSUSE:

            **rpm -qa|grep nfs**

         -  In Debian or Ubuntu:

            **dpkg -l nfs-common**

         If a command output similar to the following is displayed, the NFS software package has been installed and you can go to :ref:`4 <sfs_01_1001__li6090605610251>`. If no such command output is displayed, go to :ref:`b <sfs_01_1001__li1895373549>`.

         -  In CentOS, Red Hat, EulerOS, Fedora, or Oracle Enterprise Linux:

            .. code-block::

               libnfsidmap
               nfs-utils

         -  In SUSE or OpenSUSE:

            .. code-block::

               nfsidmap
               nfs-client

         -  In Debian or Ubuntu:

            .. code-block::

               nfs-common

      #. .. _sfs_01_1001__li1895373549:

         Run the following command to install the NFS software package.

         .. note::

            The following commands require that ECSs be connected to the Internet. Or, the installation will fail. Installing NFS clients requires enabling effective software repositories. Installing NFS clients will fail if no software repository is enabled or the ECS does not have any software repository. If installing NFS clients fails, refer to :ref:`Enabling or Adding a Software Repository <sfs_01_0027>`.

         -  In CentOS, Red Hat, EulerOS, Fedora, or Oracle Enterprise Linux:

            **sudo yum -y install nfs-utils**

         -  In Debian or Ubuntu:

            **sudo apt-get install nfs-common**

         -  In SUSE or OpenSUSE:

            **zypper install nfs-client**

#. .. _sfs_01_1001__li6090605610251:

   Run the following command to check whether the domain name in the file system mount point can be resolved. SFS Turbo file systems do not require domain name resolution. Skip this step and directly mount the file system.

   **nslookup** *File system domain name*

   .. note::

      -  A file system domain name is just a part of the mount point, for example, **sfs-nas1.example.com**. You can obtain a file system domain name from the mount point of a file system. In this step, you are not supposed to enter the entire mount point but only the domain name.
      -  If the **nslookup** command cannot be used, install the **bind-utils** software package by running the **yum install bind-utils** command.

   -  If the domain name can be resolved, go to :ref:`5 <sfs_01_1001__li4945457518115>`.
   -  If the domain name cannot be resolved, configure the DNS server IP address and then mount the file system. For details, see :ref:`Configuring DNS <sfs_01_0038>`.

#. .. _sfs_01_1001__li4945457518115:

   Run the following command to create a local path for mounting the file system:

   **mkdir** *Local path*

   .. note::

      If there is any resource, such as a disk, already mounted on the local path, create a new path. (NFS clients do not refuse repeated mounts. If there are repeated mounts, information of the last successful mount is displayed.)

#. Run the following command to mount the file system to the ECS that belongs to the same VPC as the file system. Currently, the file system can be mounted to Linux ECSs using NFSv3 only.

   :ref:`Table 1 <sfs_01_1001__table199544014035>` describes the variables.

   To mount an SFS Capacity-Oriented file system, run the following command: **mount -t nfs -o vers=3,timeo=600,noresvport,nolock** *Mount point* *Local path*

   To mount an SFS Turbo file system, run the following command: **mount -t nfs -o vers=3,timeo=600,noresvport,nolock,tcp** *Mount point* *Local path*

   To mount a general purpose file system, run the following command: **mount -t nfs -o vers=3,timeo=600,nolock,proto=tcp** *Mount point* *Local path*

   .. important::

      General purpose file systems do not support the **noresvport** mount option.

      After an ECS where file systems have been mounted restarts, it loses the file system mount information. You can configure automatic mount in the **fstab** file to ensure that an ECS automatically mounts file systems when it restarts. For details, see :ref:`Mounting a File System Automatically <sfs_01_0025>`.

   .. _sfs_01_1001__table199544014035:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================================================================================================================================================================================+
      | vers                              | File system version. Only NFSv3 is supported currently, so the value is fixed to **3**.                                                                                                                                                                                                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | timeo                             | Waiting time before the NFS client retransmits a request. The unit is 0.1 second. The recommended value is **600**.                                                                                                                                                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | noresvport                        | Whether the NFS client uses a new TCP port when a network connection is re-established.                                                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                           |
      |                                   | It is strongly recommended you use the **noresvport** option, which ensures that your file system maintains uninterrupted availability after a network reconnection or recovery.                                                                                                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | lock/nolock                       | Whether to lock files on the server using the NLM protocol. If **nolock** is selected, the lock is valid for applications on one host. For applications on another host, the lock is invalid. The recommended value is **nolock**. If this parameter is not specified, **lock** is selected by default. In this case, other servers cannot write data to the file system. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | proto                             | Protocol used by NFS clients to send requests to the server. Both UDP and TCP protocols can be used.                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                           |
      |                                   | UDP is currently not supported by general purpose file systems. If you are using general purpose file systems, set this option to **tcp**, that is, **proto=tcp**.                                                                                                                                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *Mount point*                     | The format for an SFS Capacity-Oriented file system is *File system domain name*:/*Path*, for example, **example.com:/share-**\ *xxx*. The format for an SFS Turbo file system is *File system IP address*:/, for example, **192.168.0.0:/**.                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                           |
      |                                   | :ref:`Figure 1 <sfs_01_1001__fig929579017114>` shows an example.                                                                                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                           |
      |                                   |    -  *x* is a digit or letter.                                                                                                                                                                                                                                                                                                                                           |
      |                                   |    -  If the mount point is too long to display completely, you can adjust the column width.                                                                                                                                                                                                                                                                              |
      |                                   |    -  Hover the mouse over the mount point to display the complete **mount** command.                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *Local path*                      | Local path on the ECS, used to mount the file system, for example, **/local_path**.                                                                                                                                                                                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _sfs_01_1001__fig929579017114:

   .. figure:: /_static/images/en-us_image_0251318230.png
      :alt: **Figure 1** Mount point

      **Figure 1** Mount point

   For more mounting parameters for performance optimization during file system mounting, see :ref:`Table 2 <sfs_01_1001__table372185017537>`. Use commas (,) to separate parameters. The following command is an example:

   **mount -t nfs -o vers=3,timeo=600,nolock,rsize=1048576,wsize=1048576,hard,retrans=3,noresvport,ro,async,noatime,nodiratime** *Mount point* *Local path*

   .. _sfs_01_1001__table372185017537:

   .. table:: **Table 2** Parameters for file system mounting

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | rsize                             | Maximum number of bytes that can be read from the server each time. The actual data is less than or equal to the value of this parameter. The value of **rsize** must be a positive integer that is a multiple of **1024**. If the entered value is smaller than **1024**, the value is automatically set to **4096**. If the entered value is greater than **1048576**, the value is automatically set to **1048576**. By default, the setting is performed after the negotiation between the server and the client.  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | You are advised to set this parameter to the maximum value **1048576**.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | wsize                             | Maximum number of bytes that can be written to the server each time. The actual data is less than or equal to the value of this parameter. The value of **wsize** must be a positive integer that is a multiple of **1024**. If the entered value is smaller than **1024**, the value is automatically set to **4096**. If the entered value is greater than **1048576**, the value is automatically set to **1048576**. By default, the setting is performed after the negotiation between the server and the client. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | You are advised to set this parameter to the maximum value **1048576**.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | soft/hard                         | **soft** indicates that a file system is mounted in soft mount mode. In this mode, if an NFS request times out, the client returns an error to the invoking program. **hard** indicates that a file system is mounted in hard mount mode. In this mode, if the NFS request times out, the client continues to request until the request is successful.                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | The default value is **hard**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | retrans                           | Number of retransmission times before the client returns an error. Recommended value: **1**                                                                                                                                                                                                                                                                                                                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ro/rw                             | -  **ro**: indicates that the file system is mounted as read-only.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | -  **rw**: indicates that the file system is mounted as read/write.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | The default value is **rw**. If this parameter is not specified, the file system will be mounted as read/write.                                                                                                                                                                                                                                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | noresvport                        | Whether the NFS client uses a new TCP port when a network connection is re-established.                                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | It is strongly recommended you use the **noresvport** option, which ensures that your file system maintains uninterrupted availability after a network reconnection or recovery.                                                                                                                                                                                                                                                                                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | sync/async                        | **sync** indicates that data is written to the server immediately. **async** indicates that data is first written to the cache before being written to the server.                                                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | Synchronous write requires that an NFS server returns a success message only after all data is written to the server, which brings long latency. The recommended value is **async**.                                                                                                                                                                                                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | noatime                           | If you do not need to record the file access time, set this parameter. This prevents overheads caused by access time modification during frequent access.                                                                                                                                                                                                                                                                                                                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | nodiratime                        | If you do not need to record the directory access time, set this parameter. This prevents overheads caused by access time modification during frequent access.                                                                                                                                                                                                                                                                                                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      You are advised to use the default values for the parameters without usage recommendations.

#. Run the following command to view the mounted file system:

   **mount -l**

   If the command output contains the following information, the file system has been mounted.

   .. code-block::

      Mount point on /local_path type nfs (rw,vers=3,timeo=600,nolock,addr=)

#. After the file system is mounted successfully, access the file system on the ECSs to read or write data.

   If the mounting fails or times out, rectify the fault by referring to :ref:`Troubleshooting <sfs_01_0056>`.

   .. note::

      The maximum size of a file that can be written to an SFS Capacity-Oriented file system is 240 TB.

      The maximum size of a file that can be written to an SFS Turbo file system is 32 TB, and that for an SFS Turbo Enhanced file system is 320 TB.
