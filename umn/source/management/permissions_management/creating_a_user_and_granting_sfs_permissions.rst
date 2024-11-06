:original_name: sfs_01_0032.html

.. _sfs_01_0032:

Creating a User and Granting SFS Permissions
============================================

This chapter describes how to use IAM to implement fine-grained permissions control for your SFS resources. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing SFS resources.
-  Grant only the permissions required for users to perform a specific task.

If your cloud account does not require individual IAM users, skip this section.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <sfs_01_0032__fig625610403530>`).

Prerequisites
-------------

Learn about the permissions (see :ref:`Permissions <sfs_01_0013>`) supported by SFS and choose policies or roles according to your requirements.

Restrictions
------------

-  Both system-defined policies and custom policies are supported in SFS Turbo file systems.

Process Flow
------------

.. _sfs_01_0032__fig625610403530:

.. figure:: /_static/images/en-us_image_0221089836.png
   :alt: **Figure 1** Process for granting SFS permissions

   **Figure 1** Process for granting SFS permissions

#. .. _sfs_01_0032__li539812235120:

   Create a user group and assign permissions to it.

   Create a user group on the IAM console, and attach the **SFS Turbo ReadOnlyAccess** policy to the group.

#. Create a user and add it to a user group.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <sfs_01_0032__li539812235120>`.

#. Log in and verify permissions.

   Log in to the SFS console using the created user, and verify that the user only has read permissions for SFS.

   -  Choose **Scalable File Service**. Click **Create File System** on the SFS console. If a message appears indicating that you have insufficient permissions to perform the operation, the **SFS Turbo ReadOnlyAccess** policy has already taken effect.
   -  Choose any other service. If a message appears indicating that you have insufficient permissions to access the service, the **SFS Turbo ReadOnlyAccess** policy has already taken effect.
