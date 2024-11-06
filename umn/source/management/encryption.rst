:original_name: sfs_01_0042.html

.. _sfs_01_0042:

Encryption
==========

Creating an Encrypted File System
---------------------------------

To use the file system encryption function, you need to authorize SFS Capacity-Oriented to access KMS when creating an SFS Capacity-Oriented file system. If you have the Security Administrator rights, grant SFS the permissions to access KMS directly. Otherwise, you need to contact the system administrator to obtain the "Security Administrator" rights first. For details, see :ref:`File System Encryption <sfs_01_0006>`.

SFS Turbo file systems do not require authorization.

You can create an encrypted or non-encrypted file system, but you cannot change the encryption settings of an existing file system.

For details about how to create an encrypted file system, see :ref:`Create a File System <en-us_topic_0034428727>`.

Unmounting an Encrypted File System
-----------------------------------

If the custom key used by the encrypted file system is disabled or scheduled for deletion, the file system can only be used within a certain period of time (30s by default). Exercise caution in this case.

For details about how to unmount a file system, see :ref:`Unmount a File System <sfs_01_0026>`
