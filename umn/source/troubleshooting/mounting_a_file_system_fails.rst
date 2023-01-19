:original_name: sfs_01_0057.html

.. _sfs_01_0057:

Mounting a File System Fails
============================

Symptom
-------

When running the **mount** command to mount the file system to the ECSs, the message **access denied** is displayed.

Possible Causes
---------------

-  Cause 1: The file system has been deleted.
-  Cause 2: The ECS on which the **mount** command is executed and the mounted file system are not in the same VPC.
-  Cause 3: The mount point in the **mount** command is incorrect.
-  Cause 4: The IP address used for accessing SFS is a virtual IP address.
-  Cause 5: The DNS used for accessing the file system is incorrect.

Fault Diagnosis
---------------

Take troubleshooting measures based on possible causes.

Solution
--------

-  Cause 1: The file system has been deleted.

   Log in to the management console and check whether the file system has been deleted.

   -  If yes, create a file system or select an existing file system to mount. The ECS to which the file system is to be mounted must reside in the same VPC as the mounted file system.
   -  If no, go to Cause 2.

-  Cause 2: The ECS on which the **mount** command is executed and the mounted file system are not in the same VPC.

   Log in to the management console and check whether the ECS and the file system belong to the same VPC.

   -  If yes, go to Cause 3.
   -  If no, re-select the file system of the same VPC as the ECS.

-  Cause 3: The mount point in the **mount** command is incorrect.

   #. Log in to the management console and check whether the mount point is the same as the one in the **mount** command.
   #. If the mount point in the **mount** command is incorrectly entered, correct it and run the command again.

-  Cause 4: The IP address used for accessing SFS is a virtual IP address.

   Log in to the ECS, run the **ping** command and use the IP address of the ECS to access SFS. Check whether the service is reachable. See :ref:`Figure 1 <sfs_01_0057__fig1289720753914>`.

   -  If yes, the network problem has been resolved. Check other possible causes.

   -  If no, the ECS virtual IP address is unable to access SFS due to the network problem. Use the private IP address and run the **ping** command to access SFS and check whether the service is reachable.

      .. _sfs_01_0057__fig1289720753914:

      .. figure:: /_static/images/en-us_image_0113980196.png
         :alt: **Figure 1** Running the ping command to access SFS

         **Figure 1** Running the ping command to access SFS

-  Cause 5: The DNS used for accessing the file system is incorrect.

   Run the following command to check whether the DNS is correct:

   **nslookup** *File system domain name*

   Check whether the resolved IP address is in segment **100**.

   -  If yes, the DNS configuration is correct. Check other possible causes.
   -  If no, the DNS configuration is incorrect. Reconfigure DNS by referring to :ref:`Configuring DNS <sfs_01_0038>`.
