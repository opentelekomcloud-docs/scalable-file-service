:original_name: sfs_01_0100.html

.. _sfs_01_0100:

Mounting a File System to a Linux ECS as a Non-root User
========================================================

Scenarios
---------

By default, a Linux ECS allows only the **root** user to use the **mount** command to mount file systems, but you can grant the permissions of user **root** to other users. Then, such users can use the **mount** command to mount the file systems. The following describes how to mount a file system to a Linux ECS as a common user. EulerOS is used in this example.

Prerequisites
-------------

-  A non-**root** user has been created on the ECS.
-  A file system has been created and can be mounted to the ECS as **root**.
-  The mount point of the file system has been obtained.

Procedure
---------

#. Log in to the ECS as user **root**.

#. Assign the permissions of user **root** to the non-**root** user.

   a. Run the **chmod 777 /etc/sudoers** command to change the **sudoers** file to be editable.

   b. Use the **which** command to view the **mount** and **umount** command paths.


      .. figure:: /_static/images/en-us_image_0000001331394458.png
         :alt: **Figure 1** Viewing command paths

         **Figure 1** Viewing command paths

   c. Run the **vi /etc/sudoers** command to edit the **sudoers** file.

   d. Add a common user under the **root** account. In this example, user **Mike** is added.


      .. figure:: /_static/images/en-us_image_0153998681.png
         :alt: **Figure 2** Adding a user

         **Figure 2** Adding a user

   e. Press **Esc**, input **:wq**, and press **Enter** to save and exit.

   f. Run the **chmod 440 /etc/sudoers** command to change the **sudoers** file to be read-only.

#. Log in to the ECS as user **Mike**.

#. Run the following command to mount the file system. For details about the mounting parameters, see :ref:`Table 1 <sfs_01_0100__table0741121164416>`.

   **sudo mount -t nfs -o vers=3,timeo=600,noresvport,nolock** *Mount point* *Local path*

   .. _sfs_01_0100__table0741121164416:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+-------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                               |
      +===================================+===========================================================================================+
      | Mount Point                       | .. note::                                                                                 |
      |                                   |                                                                                           |
      |                                   |    *x* is a digit or letter.                                                              |
      |                                   |                                                                                           |
      |                                   |    If the mount point is too long to display completely, you can adjust the column width. |
      +-----------------------------------+-------------------------------------------------------------------------------------------+
      | *Local path*                      | A local directory on the ECS used to mount the file system, for example, **/local_path**. |
      +-----------------------------------+-------------------------------------------------------------------------------------------+

#. Run the following command to view the mounted file system:

   **mount -l**

   If the command output contains the following information, the file system has been mounted.

   .. code-block::

      example.com:/share-xxx on /local_path type nfs (rw,vers=3,timeo=600,nolock,addr=)
