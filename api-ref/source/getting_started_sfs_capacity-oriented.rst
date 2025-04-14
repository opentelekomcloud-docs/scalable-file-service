:original_name: sfs_02_0014.html

.. _sfs_02_0014:

Getting Started (SFS Capacity-Oriented)
=======================================

Scenarios
---------

SFS provides high-performance network-attached storage (NAS) that is scalable on demand. A shared file system can be shared with multiple Elastic Cloud Servers (ECSs) and Bare Metal Servers (BMSs). If you need a fully hosted shared file storage and want to access a file system on multiple ECSs, SFS is perfect for you.

The following describes how to call the API for :ref:`Creating a Shared File System <sfs_02_0021>`. For details, see :ref:`Making an API Request <sfs_02_0009>`.

Prerequisites
-------------

You need to plan the region where a file system resides and determine the endpoint for calling an API based on the region. It can be obtained from `Regions and Endpoints <https://docs.otc.t-systems.com/regions-and-endpoints/index.html>`__.

Creating a Shared File System
-----------------------------

The following is the sample code about how to create a shared file system with the simplest configurations:

.. code-block::

   {
      "share": {
          "description": "test description",
          "share_type": "default",
          "name": "share_London",
          "metadata": {
              "key1": "value1",
              "key2": "value2"
          },
          "share_proto": "NFS",
          "size": 10,
          "is_public": false
      }
   }

-  **description**: Specifies the description of the shared file system, which adds remarks to the shared file system.
-  **share_type**: Specifies the name of a share type. A share type is used to specify the type of the storage service to be allocated.
-  **share_proto**: Specifies the protocol types of the shared file system.
-  **name**: Specifies the custom name of the shared file system. For example, **share_London**.
-  **size**: Specifies the size (in GB) of the shared file system.
-  **is_public**: Specifies the visibility level of the shared file system. If it is set to **true**, the file system can be seen publicly. If it is set to **false**, the file system can be seen privately. The default value is **false**.
-  **metadata**: Specifies the metadata information of the shared file system. The value consists of one or more key and value pairs organized as a dictionary of strings.

Creating an Encrypted Shared File System
----------------------------------------

You can also encrypt a shared file system. You only need to add parameters related to encryption of a shared file system to the metadata of the request body. The following is an example:

.. code-block::

   {
      "share": {
          "share_type": null,
          "name": "test",
          "snapshot_id": null,
          "description": "test description",
          "metadata": {
              "#sfs_crypt_key_id": "9130c90d-73b8-4203-b790-d49f98d503df",
              "#sfs_crypt_domain_id": "3b2d9670690444c582942801ed7d457b",
              "#sfs_crypt_alias": "sfs/default"
          },
          "share_proto": "NFS",
          "share_network_id": null,
          "size": 1,
          "is_public": false
      }
   }

-  **#sfs_crypt_key_id**: Specifies the encryption key ID. If **#sfs_crypt_key_id**, **#sfs_crypt_domain_id**, and **#sfs_crypt_alias** exist at the same time, the data encryption function is enabled.
-  **#sfs_crypt_domain_id**: Specifies the tenant domain ID. If **#sfs_crypt_domain_id**, **#sfs_crypt_key_id**, and **#sfs_crypt_alias** exist at the same time, the data encryption function is enabled.
-  **#sfs_crypt_alias**: Specifies the encryption key alias. If **#sfs_crypt_alias**, **#sfs_crypt_key_id**, and **#sfs_crypt_domain_id** exist at the same time, the data encryption function is enabled.
