:original_name: sfs_01_0058.html

.. _sfs_01_0058:

A Client Server Failed to Access a File System
==============================================

Symptom
-------

Access from a client server to a file system was denied. All services on the server were abnormal.

Possible Causes
---------------

-  Cause 1: The file system is abnormal.
-  Cause 2: The file system fails to be mounted to the server after being forcibly unmounted.

Fault Diagnosis
---------------

Take troubleshooting measures based on possible causes.

Solution
--------

-  Cause 1: The file system is abnormal.

   Log in to the management console. On the **Scalable File System** page, check whether the file system is in the **Available** state.

   -  If yes, go to Cause 2.
   -  If no, see :ref:`File System Is Abnormal <sfs_01_0059>` to restore the file system to the available state, and then access the file system again.

-  Cause 2: The file system fails to be mounted to the server after being forcibly unmounted.

   #. This problem is caused by a defect of servers. Restart the server to resolve this problem.
   #. Check whether the file system can be properly mounted and accessed from the server.

      -  If yes, no further action is required.
      -  If no, contact technical support.
