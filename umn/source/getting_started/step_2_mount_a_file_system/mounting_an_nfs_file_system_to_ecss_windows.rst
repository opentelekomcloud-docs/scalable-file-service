:original_name: en-us_topic_0105224109.html

.. _en-us_topic_0105224109:

Mounting an NFS File System to ECSs (Windows)
=============================================

After creating a file system, you need to mount the file system to ECSs so that they can share the file system.

This section uses Windows Server 2012 as an example to describe how to mount an NFS file system. For other versions, perform the steps based on the actual situation.

Operations on BMSs and containers (CCE) are the same as those on ECSs.

Prerequisites
-------------

-  You have created a file system and have obtained the mount point of the file system.
-  At least one ECS that belongs to the same VPC as the file system exists.
-  The IP address of the DNS server for resolving the domain names of the file systems has been configured on the ECS. For details, see :ref:`Configuring DNS <sfs_01_0038>`. SFS Turbo file systems do not require domain name resolution.

Limitations and Constraints
---------------------------

Procedure
---------

#. Log in to the management console using a cloud account.

   a. Log in to the management console and select a region and a project.
   b. Under **Computing**, click **Elastic Cloud Server** to switch to the ECS console.

#. Go to the ECS console and log in to the ECS running Windows Server 2012.

#. Install the NFS client.

   a. Click **Server Manager** in the lower left corner. The **Server Manager** window is displayed, as shown in :ref:`Figure 1 <en-us_topic_0105224109__fig5988173610457>`.

      .. _en-us_topic_0105224109__fig5988173610457:

      .. figure:: /_static/images/en-us_image_0105365714.png
         :alt: **Figure 1** Server Manager

         **Figure 1** Server Manager

   b. Click **Add Roles and Features**. See :ref:`Figure 2 <en-us_topic_0105224109__fig598816362459>`.

      .. _en-us_topic_0105224109__fig598816362459:

      .. figure:: /_static/images/en-us_image_0105366557.png
         :alt: **Figure 2** Wizard for adding roles and features

         **Figure 2** Wizard for adding roles and features

   c. Click **Next** as prompted. On the **Server Roles** page, select **Server for NFS**, as shown in :ref:`Figure 3 <en-us_topic_0105224109__fig1998863615458>`.

      .. _en-us_topic_0105224109__fig1998863615458:

      .. figure:: /_static/images/en-us_image_0105369597.png
         :alt: **Figure 3** Selecting the server for NFS

         **Figure 3** Selecting the server for NFS

   d. Click **Next**. In the **Features** page, select **Client for NFS** and click **Next**, as shown in :ref:`Figure 4 <en-us_topic_0105224109__fig398666640>`. Confirm the settings and then click **Install**. If you install the NFS client for the first time, after the installation is complete, restart the client and log in to the ECS again as prompted.

      .. _en-us_topic_0105224109__fig398666640:

      .. figure:: /_static/images/en-us_image_0132330932.png
         :alt: **Figure 4** Selecting the NFS client

         **Figure 4** Selecting the NFS client

#. Modify the NFS transfer protocol.

   a. Choose **Control Panel > System and Security > Administrative Tools > Services for Network File System (NFS)**, as shown in :ref:`Figure 5 <en-us_topic_0105224109__fig773834418456>`.

      .. _en-us_topic_0105224109__fig773834418456:

      .. figure:: /_static/images/en-us_image_0105371941.png
         :alt: **Figure 5** Administrative tools

         **Figure 5** Administrative tools

   b. Right-click **Client for NFS**, choose **Properties**, change the transport protocol to **TCP**, and select **Use hard mounts**, as shown in :ref:`Figure 6 <en-us_topic_0105224109__fig47381445453>` and :ref:`Figure 7 <en-us_topic_0105224109__fig8738344144513>`.

      .. _en-us_topic_0105224109__fig47381445453:

      .. figure:: /_static/images/en-us_image_0105373154.png
         :alt: **Figure 6** Services for NFS

         **Figure 6** Services for NFS

      .. _en-us_topic_0105224109__fig8738344144513:

      .. figure:: /_static/images/en-us_image_0105374234.png
         :alt: **Figure 7** Client for NFS properties

         **Figure 7** Client for NFS properties

#. Check that the IP address of the DNS server for resolving the domain names of the file systems has been configured on the ECS before mounting the file system. For details, see :ref:`Configuring DNS <sfs_01_0038>`. SFS Turbo file systems do not require domain name resolution.

#. Run the following command in the Command Prompt of the Windows Server 2012 (**X** is the drive letter of the free disk). Select the ECS that belongs to the same VPC as the file system to mount the file system.

   For SFS Capacity-Oriented file systems: **mount -o nolock** *mount point* **X:**

   For SFS Turbo file systems: **mount -o nolock -o casesensitive=yes** *IP address*\ **:/!** **X:**

   .. note::

      -  Free drive letter of the disk: A drive letter that is not in use, such as driver letter E or X.
      -  The mount point of an SFS Turbo file system is the root directory. **Ensure that an English exclamation mark (!) is added to the mount point**, for example, **127.0.0.1:/!**.
      -  **casesensitive=yes** indicates that file names are case sensitive during file search. If this parameter is not added, the performance of creating files in a large directory will deteriorate.

   You can move the cursor to the mount point and click |image1| next to the mount point to copy the mount point. For details, see :ref:`Figure 8 <en-us_topic_0105224109__fig212663513297>`. If the information shown in :ref:`Figure 9 <en-us_topic_0105224109__fig13957194774517>` is displayed, the mounting is successful.

   .. _en-us_topic_0105224109__fig212663513297:

   .. figure:: /_static/images/en-us_image_0251323172.png
      :alt: **Figure 8** Mount point

      **Figure 8** Mount point

   .. _en-us_topic_0105224109__fig13957194774517:

   .. figure:: /_static/images/en-us_image_0105396156.png
      :alt: **Figure 9** Running the command

      **Figure 9** Running the command

#. After the file system is mounted successfully, you can view the mounted file system on the **This PC** window, as shown in :ref:`Figure 10 <en-us_topic_0105224109__fig1120010188467>`.

   If the mounting fails or times out, rectify the fault by referring to :ref:`Troubleshooting <sfs_01_0056>`.

   .. _en-us_topic_0105224109__fig1120010188467:

   .. figure:: /_static/images/en-us_image_0108360730.png
      :alt: **Figure 10** Successful mounting

      **Figure 10** Successful mounting

   .. note::

      To distinguish different file systems mounted on an ECS, you can rename file systems by right-clicking a file system and choose **Rename**.

Troubleshooting
---------------

If a file system is mounted to a Linux ECS and a Windows ECS, you cannot write data to the files created by the Linux ECS on the Windows ECS. To address this problem, you need to modify the registry and change both values of UID and GID of the Windows user accessing NFS to **0**. This section uses Windows Server 2012 as an example. Do as follows:

#. Choose **Start** > **Run** and enter **regedit** to open the registry.

#. Enter the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\ClientForNFS\\CurrentVersion\\Default** directory. See :ref:`Figure 11 <en-us_topic_0105224109__fig103481655182917>`.

   .. _en-us_topic_0105224109__fig103481655182917:

   .. figure:: /_static/images/en-us_image_0132187564.png
      :alt: **Figure 11** Entering the directory

      **Figure 11** Entering the directory

#. Right-click the blank area and choose **New** > **DWORD Value** from the shortcut menu. Set **AnonymousUid** and **AnonymousGid** to **0**. :ref:`Figure 12 <en-us_topic_0105224109__fig56963212379>` shows a successful operation.

   .. _en-us_topic_0105224109__fig56963212379:

   .. figure:: /_static/images/en-us_image_0132187573.png
      :alt: **Figure 12** Adding values

      **Figure 12** Adding values

#. After modifying the registry, restart the server for the modification to take effect.

.. |image1| image:: /_static/images/en-us_image_0110722360.png
