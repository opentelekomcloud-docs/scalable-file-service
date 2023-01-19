:original_name: en-us_topic_0034428728.html

.. _en-us_topic_0034428728:

Mounting an NFS File System to ECSs (Linux)
===========================================

After creating a file system, you need to mount the file system to ECSs so that they can share the file system.

Operations on BMSs and containers (CCE) are the same as those on ECSs.

Prerequisites
-------------

-  You have checked the type of the operating system on each ECS. Different operating systems use different commands to install the NFS client.
-  You have created a file system and have obtained the mount point of the file system.
-  At least one ECS that belongs to the same VPC as the file system exists.
-  The IP address of the DNS server for resolving the domain names of the file systems has been configured on the ECS. SFS Turbo file systems do not require domain name resolution.

Procedure
---------

#. Log in to the management console using a cloud account.

   a. Log in to the management console and select a region and a project.
   b. Under **Computing**, click **Elastic Cloud Server** to switch to the ECS console.

#. Log in to the ECS as user **root**.

   .. note::

      If you log in to the ECS as a non-root user, see :ref:`Mounting a File System to an ECS Running Linux as a Non-root User <sfs_01_0100>`.

#. Install the NFS client.

   a. Run the following command to check whether the NFS software package is installed.

      -  On CentOS, Red Hat, Oracle Enterprise Linux, SUSE, EulerOS, Fedora, or OpenSUSE:

         **rpm -qa|grep nfs**

      -  On Debian or Ubuntu:

         **dpkg -l nfs-common**

      If a command output similar to the following is displayed, the NFS software package has been installed and you can go to :ref:`4 <en-us_topic_0034428728__li6090605610251>`. If nothing is displayed, go to :ref:`3.b <en-us_topic_0034428728__li4299938211109>`.

      -  On CentOS, Red Hat, EulerOS, Fedora, or Oracle Enterprise Linux:

         .. code-block::

            libnfsidmap
            nfs-utils

      -  On SUSE or OpenSUSE:

         .. code-block::

            nfsidmap
            nfs-client

      -  On Debian or Ubuntu:

         .. code-block::

            nfs-common

   b. .. _en-us_topic_0034428728__li4299938211109:

      Run the following command to install the NFS software package.

      .. note::

         The following commands require that ECSs be connected to the Internet. Otherwise, the installation will fail. Installing NFS clients requires enabling effective software repositories. Installing NFS clients will fail if no software repository is enabled or the ECS does not have any software repository. If installing NFS clients fails, refer to :ref:`Enabling or Adding a Software Repository <sfs_01_0027>`.

      -  On CentOS, Red Hat, EulerOS, Fedora, or Oracle Enterprise Linux:

         **sudo yum -y install nfs-utils**

      -  On Debian or Ubuntu:

         **sudo apt-get install nfs-common**

      -  On SUSE or OpenSUSE:

         **zypper install nfs-client**

#. .. _en-us_topic_0034428728__li6090605610251:

   Run the following command to check whether the domain name in the file system mount point can be resolved. SFS Turbo file systems do not require domain name resolution. You can skip this step and directly mount the file system.

   **nslookup** *File system domain name*

   .. note::

      -  A file system domain name is just a part of the mount point, for example, **sfs-nas1.**\ *xxxx*\ **.com**. You can obtain a file system domain name from the mount point of a file system. In this step, you are not supposed to enter the entire mount point but only the domain name.
      -  If the **nslookup** command cannot be used, install the **bind-utils** software package by running the **yum install bind-utils** command.

   -  If the domain name can be resolved, go to :ref:`5 <en-us_topic_0034428728__li4945457518115>`.
   -  If the domain name cannot be resolved, configure the DNS server IP address and then mount the file system. For details, see :ref:`Configuring DNS <sfs_01_0038>`.

#. .. _en-us_topic_0034428728__li4945457518115:

   Run the following command to create a local path for mounting the file system:

   **mkdir** *Local path*

   .. note::

      If there are resources, such as disks, already mounted on the local path, create a new path.

#. Run the following command to mount the file system to the ECS that belongs to the same VPC as the file system. Currently, the file system can be mounted to the ECS running Linux using NFS v3 only.

   :ref:`Table 1 <en-us_topic_0034428728__table199544014035>` describes the variables.

   **mount -t nfs -o vers=3,timeo=600,noresvport,nolock** *Mount point* *Local path*

   .. important::

      After an ECS where file systems have been mounted restarts, it loses the file system mount information. You can configure automatic mount in the **fstab** file to ensure that an ECS automatically mounts file systems when it restarts. For details, see :ref:`Mounting a File System Automatically <sfs_01_0025>`.

   .. _en-us_topic_0034428728__table199544014035:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================================================================================================================================================================================+
      | vers                              | File system version. Currently, only NFSv3 is supported, so the value is fixed to **3**.                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | timeo                             | Waiting time before the NFS client retransmits a request. The unit is 0.1 second. The recommended value is **600**.                                                                                                                                                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resvport/noresvport               | Whether the confidential source port is used for server connection. By default, **resvport** indicates that the confidential port is used, and **noresvport** indicates that the confidential port is not used. The kernel version is 2.6.28 or later.                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                           |
      |                                   | You are advised to set this parameter to **noresvport** so that a new TCP port can be used when the network is reconnected. This ensures that the connection is not interrupted when the network recovers from a fault.                                                                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | lock/nolock                       | Whether to lock files on the server using the NLM protocol. If **nolock** is selected, the lock is valid for applications on one host. For applications on another host, the lock is invalid. The recommended value is **nolock**. If this parameter is not specified, **lock** is selected by default. In this case, other servers cannot write data to the file system. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *Mount point*                     | The format for an SFS Capacity-Oriented file system is *File system domain name*:/*Path*, for example, **example.com:/share-**\ *xxx*. The format for an SFS Turbo file system is *File system IP address*:/, for example, **192.168.0.0:/**. See :ref:`Figure 1 <en-us_topic_0034428728__fig929579017114>`.                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                           |
      |                                   |    -  *x* is a digit or letter.                                                                                                                                                                                                                                                                                                                                           |
      |                                   |    -  If the mount point is too long to display completely, you can adjust the column width.                                                                                                                                                                                                                                                                              |
      |                                   |    -  Hover the mouse over the mount point to display the complete **mount** command.                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *Local path*                      | Local path on the ECS, used to mount the file system, for example, **/local_path**.                                                                                                                                                                                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0034428728__fig929579017114:

   .. figure:: /_static/images/en-us_image_0251318230.png
      :alt: **Figure 1** Mount point

      **Figure 1** Mount point

   For more mounting parameters for performance optimization during file system mounting, see :ref:`Table 2 <en-us_topic_0034428728__table372185017537>`. Use commas (,) to separate parameters. The following command is an example:

   **mount -t nfs -o vers=3,timeo=600,nolock,rsize=1048576,wsize=1048576,hard,retrans=3,noresvport,async,noatime,nodiratime** *Mount point* *Local path*

   .. _en-us_topic_0034428728__table372185017537:

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
      | retrans                           | Number of retransmission times before the client returns an error. The default value is **3**.                                                                                                                                                                                                                                                                                                                                                                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resvport/noresvport               | Whether the confidential source port is used for server connection. By default, **resvport** indicates that the confidential port is used, and **noresvport** indicates that the confidential port is not used. The kernel version is 2.6.28 or later.                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | You are advised to set this parameter to **noresvport** so that a new TCP port can be used when the network is reconnected. This ensures that the connection is not interrupted when the network recovers from a fault.                                                                                                                                                                                                                                                                                                |
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

   If the command output contains the following information, the file system is mounted successfully.

   .. code-block::

      Mount point on /local_path type nfs (rw,vers=3,timeo=600,nolock,addr=)

#. After the file system is mounted successfully, access the file system on the ECSs to read or write data.

   If the mounting fails or times out, rectify the fault by referring to :ref:`Troubleshooting <sfs_01_0056>`.

   .. note::

      The maximum size of a file that can be written is 240 TB.
