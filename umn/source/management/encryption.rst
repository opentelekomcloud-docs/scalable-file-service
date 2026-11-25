:original_name: sfs_01_0042.html

.. _sfs_01_0042:

Encryption
==========

Creating an Encrypted File System
---------------------------------

-  To use SFS Capacity-Oriented file system encryption, you need to authorize SFS to access KMS when creating an SFS Capacity-Oriented file system. If you have the Security Administrator permissions, grant SFS the KMS access permissions directly. Otherwise, you need to contact the system administrator to obtain the Security Administrator permissions first. For details, see :ref:`File System Encryption <sfs_01_0006>`.
-  To use general purpose file system encryption, you can directly select server-side encryption when creating a general purpose file system. Ensure that you have the kms:cmk:get, kms:cmk:list, kms:cmk:decrypt, kms:cmk:create, kms:cmk:encrypt, kms:dek:create, kms:dek:decrypt, kms:dek:encrypt, iam:agencies:getAgency, and iam:agencies:createAgency permissions before creating encrypted file systems. For details about how to obtain required IAM action permissions, see section "Creating a Custom Policy" in the *Identity and Access Management User Guide*. If this is your first time using encryption, the system will prompt you the **Create Agency** window. You only need to click **OK** to have the required authorization automatically granted to you. The system will automatically create an agency named **SFSAccessKMS** to grant KMS access permissions to SFS. The delegated account and permissions of the agency are **op_svc_sfs** and **KMS Administrator**. After permissions are granted, SFS can obtain KMS keys to encrypt and decrypt file systems.
-  You can directly use encryption when creating SFS Turbo file systems. No authorization is required.

You can create an SFS file system that is encrypted or not, but you cannot change the encryption attribute of an existing file system.

For details about how to create an encrypted file system, see :ref:`Create a File System <en-us_topic_0034428727>`.

Unmounting an Encrypted File System
-----------------------------------

If the custom key used by the encrypted file system is disabled or scheduled for deletion, the file system can only be used within a certain period of time (30s by default). Exercise caution in this case.

For details about how to unmount the file system, see :ref:`Unmount a File System <sfs_01_0026>`.
