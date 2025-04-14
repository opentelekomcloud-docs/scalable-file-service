:original_name: CreateShare.html

.. _CreateShare:

Creating a File System
======================

Function
--------

This API is used to create a file system.

URI
---

POST /v1/{project_id}/sfs-turbo/shares

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== =============
   Parameter    Mandatory Type   Description
   ============ ========= ====== =============
   X-Auth-Token Yes       String Account token
   Content-Type Yes       String MIME type
   ============ ========= ====== =============

.. table:: **Table 3** Request body parameters

   +-----------+-----------+--------------------------------------------------+-----------------------------------------+
   | Parameter | Mandatory | Type                                             | Description                             |
   +===========+===========+==================================================+=========================================+
   | share     | Yes       | :ref:`Share <createshare__request_share>` object | Request body for creating a file system |
   +-----------+-----------+--------------------------------------------------+-----------------------------------------+

.. _createshare__request_share:

.. table:: **Table 4** Share

   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type                                                                   | Description                                                                                                                                                                                                                                                                                                              |
   +===================+=================+========================================================================+==========================================================================================================================================================================================================================================================================================================================+
   | availability_zone | Yes             | String                                                                 | Code of the AZ where the file system is located. For details about the code, see section "Regions and Endpoints."                                                                                                                                                                                                        |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description       | No              | String                                                                 | Description of the file system, which can contain 0 to 255 characters. This parameter is not supported by the current version.                                                                                                                                                                                           |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata          | No              | :ref:`Metadata <createshare__request_metadata>` object                 | Metadata of the file system. The value consists of key and value pairs as a directory of strings.                                                                                                                                                                                                                        |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name              | Yes             | String                                                                 | Name of the SFS Turbo file system. The name contains 4 to 64 characters and must start with a letter. It can contain letters (case insensitive), digits, hyphens (-), and underscores (_), and cannot contain other special characters.                                                                                  |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id | Yes             | String                                                                 | Security group ID of a tenant in a region. You can obtain the security group ID from the console or by following the instructions provided in section "Querying Security Groups" in *Virtual Private Cloud API Reference*.                                                                                               |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_proto       | Yes             | String                                                                 | File sharing protocol. The valid value is **NFS**. Network File System (NFS) is a distributed file system protocol that allows different computers and operating systems to share data over a network.                                                                                                                   |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_type        | Yes             | String                                                                 | File system type. Valid values are **STANDARD** and **PERFORMANCE**. This field is not returned when the file system is being created.                                                                                                                                                                                   |
   |                   |                 |                                                                        |                                                                                                                                                                                                                                                                                                                          |
   |                   |                 |                                                                        | -  For a previous-generation SFS Turbo file system, specify **STANDARD** for a Standard or Standard - Enhanced file system, and **PERFORMANCE** for a Performance or Performance - Enhanced file system.                                                                                                                 |
   |                   |                 |                                                                        | -  For a 250 MB/s/TiB, 125 MB/s/TiB, 40 MB/s/TiB, or 20 MB/s/TiB file system, this field is not verified. Specify either **STANDARD** or **PERFORMANCE**.                                                                                                                                                                |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size              | Yes             | Integer                                                                | -  SFS Turbo previous-generation file system specifications-file system capacity: The value ranges from 500 to 32768, in GiB.                                                                                                                                                                                            |
   |                   |                 |                                                                        | -  For an SFS Turbo Enhanced file system, if expand_type is set to bandwidth in the metadata field, the capacity ranges from 10240 to 327680, in GiB.                                                                                                                                                                    |
   |                   |                 |                                                                        | -  20MB/s/TiB: If expand_type is set to hpc and hpc_bw is set to 20M in the metadata field, the capacity ranges from 3686 to 1048576, in GiB. The capacity must be a multiple of 1.2 TiB. The value must be rounded down after being converted to GiB. For example, 3.6TiB->3686GiB, 4.8TiB->4915GiB, 8.4TiB->8601GiB.   |
   |                   |                 |                                                                        | -  40MB/s/TiB: If expand_type is set to hpc and hpc_bw is set to 40M in the metadata field, the capacity ranges from 1228 to 1048576, in GiB. The capacity must be a multiple of 1.2 TiB. The value must be rounded down after being converted to GiB. For example, 3.6TiB->3686GiB, 4.8TiB->4915GiB, 8.4TiB->8601GiB.   |
   |                   |                 |                                                                        | -  125MB/s/TiB: If expand_type is set to hpc and hpc_bw is set to 125M in the metadata field, the capacity ranges from 1228 to 1048576, in GiB. The capacity must be a multiple of 1.2 TiB. The value must be rounded down after being converted to GiB. For example, 3.6TiB->3686GiB, 4.8TiB->4915GiB, 8.4TiB->8601GiB. |
   |                   |                 |                                                                        | -  250MB/s/TiB: If expand_type is set to hpc and hpc_bw is set to 250M in the metadata field, the capacity ranges from 1228 to 1048576, in GiB. The capacity must be a multiple of 1.2 TiB. The value must be rounded down after being converted to GiB. For example, 3.6TiB->3686GiB, 4.8TiB->4915GiB, 8.4TiB->8601GiB. |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id         | Yes             | String                                                                 | Subnet ID of a tenant in a VPC                                                                                                                                                                                                                                                                                           |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id            | Yes             | String                                                                 | VPC ID of a tenant in a region                                                                                                                                                                                                                                                                                           |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | backup_id         | No              | String                                                                 | Backup ID. This parameter is mandatory if you create a file system from a backup.                                                                                                                                                                                                                                        |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags              | No              | Array of :ref:`ResourceTag <createshare__request_resourcetag>` objects | Tag list                                                                                                                                                                                                                                                                                                                 |
   +-------------------+-----------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createshare__request_metadata:

.. table:: **Table 5** Metadata

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================+
   | crypt_key_id    | No              | String          | ID of a KMS professional key. This parameter is used if you want to create an encrypted file system.                                                                        |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | expand_type     | No              | String          | Extension type. This parameter is not returned when the file system is being created.                                                                                       |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | This parameter is mandatory when you are creating an SFS Turbo 250 MB/s/TiB, 125 MB/s/TiB, 40 MB/s/TiB, 20 MB/s/TiB, or Enhanced file system.                               |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | -  Specify **bandwidth** when you are creating a Standard - Enhanced or Performance - Enhanced file system.                                                                 |
   |                 |                 |                 | -  Specify **hpc** when you are creating a 250 MB/s/TiB, 125 MB/s/TiB, 40 MB/s/TiB, or 20 MB/s/TiB file system.                                                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hpc_bw          | No              | String          | File system bandwidth.                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | This parameter is mandatory when you are creating an SFS Turbo 250 MB/s/TiB, 125 MB/s/TiB, 40 MB/s/TiB, or 20 MB/s/TiB file system.                                         |
   |                 |                 |                 |                                                                                                                                                                             |
   |                 |                 |                 | Specify **20M** for a 20 MB/s/TiB file system, **40M** for a 40 MB/s/TiB file system, **125M** for a 125 MB/s/TiB file system, and **250M** for a 250 MB/s/TiB file system. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createshare__request_resourcetag:

.. table:: **Table 6** ResourceTag

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================================================================================================================================================+
   | key             | Yes             | String          | Tag key.                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It can contain a maximum of 128 characters.                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It cannot be left empty and cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_). |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | Tag value.                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Each tag value can contain a maximum of 255 characters and can be an empty string.                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_).                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 7** Response body parameters

   ========= ====== =========================================
   Parameter Type   Description
   ========= ====== =========================================
   id        String ID of the created SFS Turbo file system
   name      String Name of the created SFS Turbo file system
   status    String Status of the SFS Turbo file system
   ========= ====== =========================================

Example Requests
----------------

-  Previous-generation SFS Turbo file system:

   This example creates an SFS Turbo Standard file system in the AZ whose AZ code is **example**, with the file system name set to **sfs-turbo-test**, protocol type to NFS, capacity to 500 GB. The security group ID is **8c4ebbd0-6edf-4aae-8353-xxx**, the subnet ID is **b8884abe-f47b-4917-9f6c-xxx**, and the VPC ID is **d651ea2b-2b20-4c6d-8bbf-xxx**.

   .. code-block:: text

      POST HTTPS://{endpoint}/v1/{project_id}/sfs-turbo/shares

      {
        "share" : {
          "name" : "sfs-turbo-test",
          "availability_zone" : "example",
          "security_group_id" : "8c4ebbd0-6edf-4aae-8353-xxx",
          "share_proto" : "NFS",
          "share_type" : "STANDARD",
          "size" : 500,
          "subnet_id" : "b8884abe-f47b-4917-9f6c-xxx",
          "vpc_id" : "d651ea2b-2b20-4c6d-8bbf-xxx"
        }
      }

-  125 MB/s/TiB:

   This example creates an SFS Turbo 125 MB/s/TiB file system in the AZ whose AZ code is **example**, with the file system name set to **sfs-turbo-test**, protocol type to NFS, capacity to 3686 GB. The security group ID is **8c4ebbd0-6edf-4aae-8353-xxx**, the subnet ID is **b8884abe-f47b-4917-9f6c-xxx**, and the VPC ID is **d651ea2b-2b20-4c6d-8bbf-xxx**.

   .. code-block:: text

      POST HTTPS://{endpoint}/v1/{project_id}/sfs-turbo/shares

      {
        "share" : {
          "name" : "sfs-turbo-test",
          "availability_zone" : "example",
          "security_group_id" : "8c4ebbd0-6edf-4aae-8353-xxx",
          "share_proto" : "NFS",
          "share_type" : "STANDARD",
          "size" : 3686,
          "subnet_id" : "b8884abe-f47b-4917-9f6c-xxx",
          "vpc_id" : "d651ea2b-2b20-4c6d-8bbf-xxx",
          "metadata" : {
            "expand_type" : "hpc",
            "hpc_bw" : "125M"
          }
        }
      }

Example Responses
-----------------

**Status code: 202**

Response body for creating a file system

.. code-block::

   {
     "id" : "708c017c-54b5-429a-a098-7692e23fa518",
     "name" : "sfs-turbo-test",
     "status" : "100"
   }

Status Codes
------------

=========== ========================================
Status Code Description
=========== ========================================
202         Response body for creating a file system
=========== ========================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
