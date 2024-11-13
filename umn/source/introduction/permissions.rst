:original_name: sfs_01_0013.html

.. _sfs_01_0013:

Permissions
===========

If you need to assign different permissions to employees in your enterprise to access your SFS resources on the cloud, Identity and Access Management (IAM) is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you to securely access your cloud resources.

With IAM, you can use your cloud account to create IAM users, and assign permissions to the users to control their access to specific resources. For example, some software developers in your enterprise need to use SFS resources but should not be allowed to delete the resources or perform any other high-risk operations. In this scenario, you can create IAM users for the software developers and grant them only the permissions required for using SFS resources.

If your cloud account does not require individual IAM users for permissions management, skip this section.

IAM can be used free of charge. You pay only for the resources in your account. For more information about IAM, see *Identity and Access Management User Guide*.

SFS Permissions
---------------

By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

SFS is a project-level service deployed and accessed in specific physical regions. To assign SFS permissions to a user group, specify the scope as region-specific projects and select projects for the permissions to take effect. If **All projects** is selected, the permissions will take effect for the user group in all region-specific projects. When accessing SFS, the users need to switch to a region where they have been authorized to use this service.

You can grant users permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism provides only a limited number of service-level roles for authorization. When using roles to grant permissions, you need to also assign other roles on which the permissions depend to take effect. However, roles are not an ideal choice for fine-grained authorization and secure access control.
-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant ECS users only the permissions for managing a certain type of ECSs. Most policies define permissions based on APIs. For the API actions supported by SFS, see section "Permissions Policies and Supported Actions" in the *Scalable File Service API Reference*.

:ref:`Table 1 <sfs_01_0013__table20157331101014>` lists all the system-defined roles and policies supported by SFS Turbo.

.. _sfs_01_0013__table20157331101014:

.. table:: **Table 1** System-defined roles and policies supported by SFS Turbo

   +--------------------------+--------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------+
   | Role/Policy Name         | Description                                                                                                                    | Type                  | Dependency |
   +==========================+================================================================================================================================+=======================+============+
   | SFS Turbo FullAccess     | Administrator permissions for SFS Turbo. Users granted these permissions can perform all operations on SFS Turbo file systems. | System-defined policy | None       |
   +--------------------------+--------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------+
   | SFS Turbo ReadOnlyAccess | Read-only permissions for SFS Turbo. Users granted these permissions can only view SFS Turbo file system data.                 | System-defined policy | None       |
   +--------------------------+--------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------+

:ref:`Table 2 <sfs_01_0013__table1836173142018>` lists all the system-defined roles and policies supported by General Purpose File System.

.. _sfs_01_0013__table1836173142018:

.. table:: **Table 2** System-defined roles and policies supported by General Purpose File System

   +----------------------+------------------------------------------------------------------------+-----------------------+------------+
   | Role/Policy Name     | Description                                                            | Type                  | Dependency |
   +======================+========================================================================+=======================+============+
   | Tenant Administrator | Permissions to perform all operations on all services except IAM       | System-defined policy | None       |
   +----------------------+------------------------------------------------------------------------+-----------------------+------------+
   | Tenant Guest         | Permissions to perform read-only operations on all services except IAM | System-defined policy | None       |
   +----------------------+------------------------------------------------------------------------+-----------------------+------------+
