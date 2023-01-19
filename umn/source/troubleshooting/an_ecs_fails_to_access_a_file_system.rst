:original_name: sfs_01_0058.html

.. _sfs_01_0058:

An ECS Fails to Access a File System
====================================

Symptom
-------

An ECS fails to access a file system. The system displays a message indicating that the access request is denied. All services on the ECS are abnormal.

Possible Causes
---------------

-  Cause 1: The file system is abnormal.
-  Cause 2: After a forcible unmount operation on the ECS, mount fails.

Fault Diagnosis
---------------

Take troubleshooting measures based on possible causes.

Solution
--------

-  Cause 1: The file system is abnormal.

   Log in to the management console. On the **Scalable File System** page, check whether the file system is in the **Available** state.

   -  If yes, go to Cause 2.
   -  If no, see :ref:`The File System Is Abnormal <sfs_01_0059>` to restore the file system to the available state, and then access the file system again.

-  Cause 2: After a forcible unmount operation on the ECS, mount fails.

   #. This problem is caused by an inherent defect of ECSs. Restart the ECS to resolve this problem.
   #. Check whether the file system can be properly mounted and accessed.

      -  If yes, no further action is required.
      -  If no, contact technical support.
