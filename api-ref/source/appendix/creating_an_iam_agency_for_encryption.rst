:original_name: sfs_02_0192.html

.. _sfs_02_0192:

Creating an IAM Agency for Encryption
=====================================

Scenarios
---------

If this is your first time using file system encryption with the account, you need to create an IAM agency to grant account **op_svc_sfs** the KMS Administrator permissions. The created agency takes effect in about 10 minutes.

Creating an Agency on the Console
---------------------------------

#. Log in to the IAM console.

#. In the navigation pane on the left, choose **Agencies**.

#. Click **Create Agency** in the upper right corner. On the displayed page, set the parameters based on your requirements. Mandatory parameters are described as follows:

   -  **Agency Name**: Enter a name, for example, **SFSAccessKMS**.
   -  **Agency Type**: Select **Account**.
   -  **Delegated Account**: Enter **op_svc_sfs**.
   -  **Validity Period**: Select **Unlimited**. After the configuration is complete, click **OK**.

#. After the agency is created, click **Authorize** in the **Operation** column.

#. Select a policy.

   Search for and select the **KMS Administrator** policy and click **Next**.

#. Select a scope.

   **All resources** is preselected. You can select **Region-specific projects** as required. Click **OK**.
