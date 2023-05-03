:original_name: sfs_01_0033.html

.. _sfs_01_0033:

Creating a Custom Policy
========================

Custom policies can be created to supplement the system-defined policies of SFS. For the actions supported for custom policies, see section "Permissions Policies and Supported Actions" in the *Scalable File Service API Reference*.

You can create custom policies in either of the following two ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

This section provides examples of common custom SFS policies.

Example Custom Policies
-----------------------

-  Example 1: Allowing users to create file systems

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Action": [
                                      "sfsturbo:shares:createShare"
                              ],
                              "Effect": "Allow"
                      }
              ]
      }

-  Example 2: Denying file system deletion

   A policy with only "Deny" permissions must be used in conjunction with other policies to take effect. If the permissions assigned to a user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   The following method can be used if you need to assign permissions of the **SFS Turbo FullAccess** policy to a user but also forbid the user from deleting file systems. Create a custom policy for denying file system deletion, and attach both policies to the group to which the user belongs. Then, the user can perform all operations on SFS except deleting file systems. The following is an example of a deny policy:

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Effect": "Deny",
                              "Action": [
                                      "sfsturbo:shares:deleteShare"
                              ]
                      }
              ]
      }

-  Example 3: Defining permissions for multiple services in a policy

   A custom policy can contain actions of multiple services that are all of the global or project-level type. The following is an example policy containing actions of multiple services:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "sfsturbo:shares:createShare",
                      "sfsturbo:shares:deleteShare",
                      "sfsturbo:shares:updateShare"
                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "ecs:servers:delete"
                  ]
              }
          ]
      }
