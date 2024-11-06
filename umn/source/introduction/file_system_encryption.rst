:original_name: sfs_01_0006.html

.. _sfs_01_0006:

File System Encryption
======================

SFS provides you with the encryption function. You can encrypt data on the new file systems if needed.

Keys for encrypting file systems are provided by Key Management Service (KMS), which is secure and convenient. You do not need to establish and maintain key management infrastructure. If you want to use your own key material, use the key import function on the KMS console to create a custom key whose key material is empty and import the key material to the custom key. For details, see section "Importing Key Materials" in *Key Management Service User Guide*.

To use the file system encryption function, you need to authorize SFS Capacity-Oriented to access KMS when creating an SFS Capacity-Oriented file system. SFS Turbo file systems do not need authorization.

Encryption Key
--------------

Keys provided by KMS for encrypting SFS Capacity-Oriented file systems include a default key and custom keys.

-  Default key: SFS automatically creates a default key and names it **sfs/default**.

   The default key cannot be disabled and does not support scheduled deletion.

-  Custom keys: Existing or newly created custom keys. For details, see Creating a Custom Key in the *Key Management Service User Guide*.

   If the custom key used by the encrypted file system is disabled or scheduled for deletion, the file system can only be used within a certain period of time (30s by default). Exercise caution in this case.

SFS Turbo file systems do not have default keys. You can use your existing key or create a key. For details, see section "Creating a Key" in the *Key Management Service User Guide*.

General Purpose File System does not support file system encryption.

Who Has the Rights to Encrypt File Systems?
-------------------------------------------

-  The security administrator who has the "Security Administrator" permission can grant the KMS access rights for encryption.
-  A common user who does not have the "Security Administrator" permission needs to contact the system administrator to obtain the "Security Administrator" permission.

As long as the KMS access rights have been granted to SFS Capacity-Oriented, all common users in the same region can directly use the encryption function.

If there are multiple projects in the current region, the KMS access rights need to be granted to each project in this region.
