:original_name: sfs_02_0112.html

.. _sfs_02_0112:

Creating a File System
======================

Function
--------

This API is used to create a file system with a specified name.

.. note::

   -  A file system name must be unique in SFS. If a user repeatedly creates a file system with the same name as that of an existing file system in a given region, a success response is returned. In other cases, if a file system with the same name is repeatedly created, an error message will be returned, indicating that the file system already exists.
   -  By default, a user can have a maximum of 100 file systems.
   -  If a general purpose file system is deleted, you can create a new file system with the same name after at least 12 hours.

URI
---

PUT /

Request Parameters
------------------

.. table:: **Table 1** Request header parameters

   +-----------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                               | Mandatory       | Type            | Description                                                                                                                                                                                                                                        |
   +=========================================+=================+=================+====================================================================================================================================================================================================================================================+
   | Authorization                           | Yes             | String          | The signature information.                                                                                                                                                                                                                         |
   +-----------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Date                                    | Yes             | String          | The request time.                                                                                                                                                                                                                                  |
   +-----------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-az-redundancy                     | Yes             | String          | When creating a file system, you must include this header, which sets the file system redundancy to 3AZ.                                                                                                                                           |
   |                                         |                 |                 |                                                                                                                                                                                                                                                    |
   |                                         |                 |                 | Example: **x-obs-az-redundancy:3az**                                                                                                                                                                                                               |
   +-----------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-bucket-type                       | Yes             | String          | The header field used to specify the file system creation.                                                                                                                                                                                         |
   |                                         |                 |                 |                                                                                                                                                                                                                                                    |
   |                                         |                 |                 | Enumerated value:                                                                                                                                                                                                                                  |
   |                                         |                 |                 |                                                                                                                                                                                                                                                    |
   |                                         |                 |                 | -  **SFS** (creating a file system)                                                                                                                                                                                                                |
   +-----------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Host                                    | Yes             | String          | The host address.                                                                                                                                                                                                                                  |
   +-----------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption            | No              | String          | The header field that specifies the file system encryption mode. If this header is not specified, file system encryption is disabled.                                                                                                              |
   |                                         |                 |                 |                                                                                                                                                                                                                                                    |
   |                                         |                 |                 | If this is your first time creating an encrypted file system, you need to create an IAM agency to grant the **op_svc_sfs** account the KMS administrator permissions. For details, see :ref:`Creating an IAM Agency for Encryption <sfs_02_0192>`. |
   |                                         |                 |                 |                                                                                                                                                                                                                                                    |
   |                                         |                 |                 | Enumerated value:                                                                                                                                                                                                                                  |
   |                                         |                 |                 |                                                                                                                                                                                                                                                    |
   |                                         |                 |                 | -  **kms** (creating an encrypted file system using server-side encryption)                                                                                                                                                                        |
   +-----------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-data-encryption       | No              | String          | The header field that specifies the algorithm used for server-side encryption. If file system encryption is enabled but this header is not included, the AES256 algorithm is used for data encryption.                                             |
   |                                         |                 |                 |                                                                                                                                                                                                                                                    |
   |                                         |                 |                 | Enumerated values:                                                                                                                                                                                                                                 |
   |                                         |                 |                 |                                                                                                                                                                                                                                                    |
   |                                         |                 |                 | -  **AES256** (using the AES256 algorithm)                                                                                                                                                                                                         |
   +-----------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-server-side-encryption-kms-key-id | No              | String          | The header field that specifies the encryption key ID used for server-side encryption. For how to obtain the key ID, see :ref:`Obtaining a KMS Key ID <sfs_02_0191>`.                                                                              |
   |                                         |                 |                 |                                                                                                                                                                                                                                                    |
   |                                         |                 |                 | If you specify **kms** for encryption but do not specify a key ID, the default key will be used. If the default key is not found, the system will create one and use it.                                                                           |
   +-----------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | x-obs-sse-kms-key-project-id            | No              | String          | The header field that specifies the ID of the project where the server-side encryption key belongs. For how to obtain the project ID, see :ref:`Obtaining a Project ID <sfs_02_0090>`.                                                             |
   |                                         |                 |                 |                                                                                                                                                                                                                                                    |
   |                                         |                 |                 | Specify the project ID (not an enterprise project ID) that matches the KMS key ID specified by **x-obs-server-side-encryption-kms-key-id**.                                                                                                        |
   +-----------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Request body parameter

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   Location  No        String The region.
   ========= ========= ====== ===========

Response Parameters
-------------------

This response uses common headers. For details, see :ref:`Table 1 <sfs_02_0106__en-us_topic_0000001263068826_d0e686>`.

(Optional) Response Body
------------------------

A response body contains information other than the response header. It is usually sent in a structured format (JSON or XML) defined by the response header parameter **Content-type**.

Example Request: Creating a File System
---------------------------------------

Creating a file system in the **example** region (with the host address **Host: example-sfs-01.sfs3.example.region.com:443**):

.. code-block:: text

   PUT / HTTP/1.1
   Host: example-sfs-01.sfs3.example.region.com:443
   Date: Wed, 07 Jun 2023 02:38:09 GMT
   x-obs-bucket-type: SFS
   Authorization: OBS FNEX1B77SXDIB3TFMSZZ:0Xsnu4hJVOI7VWH0wIQczVN+rbg=
   Content-Length: 85
   x-obs-az-redundancy:3az

   <CreateBucketConfiguration>
       <Location>example</Location>
   </CreateBucketConfiguration>

Example Response: Creating a File System
----------------------------------------

.. code-block::

   HTTP/1.1 200 OK
   Server: OBS
   X-Obs-Request-Id: 0000018893B8058EC0470388BE6EDE88
   Location: /example-sfs-01
   X-Obs-Id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCTRa4voOUvr50ncznQT/hligMxL4so2z
   Date: Wed, 07 Jun 2023 02:38:11 GMT
   Content-Length: 0

Example Request: Creating an Encrypted File System Using the Default Key
------------------------------------------------------------------------

Creating an encrypted file system using the default key in the **example** region:

.. code-block:: text

   PUT / HTTP/1.1
   Host: example-sfs-02.sfs3.example.region.com:443
   Date: Wed, 07 Jun 2023 02:38:09 GMT
   x-obs-bucket-type: SFS
   Authorization: OBS FNEX1B77SXDIB3TFMSZZ:0Xsnu4hJVOI7VWH0wIQczVN+rbg=
   Content-Length: 85
   x-obs-server-side-encryption: kms
   <CreateBucketConfiguration>
       <Location>example</Location>
   </CreateBucketConfiguration>

Example Response: Creating an Encrypted File System Using the Default Key
-------------------------------------------------------------------------

.. code-block::

   HTTP/1.1 200 OK
   Server: OBS
   X-Obs-Request-Id: 0000018893B8058EC0470388BE6EDE88
   Location: /example-sfs-02
   X-Obs-Id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCTRa4voOUvr50ncznQT/hligMxL4so2z
   Date: Wed, 07 Jun 2023 02:38:11 GMT
   Content-Length: 0

Example Request: Creating an Encrypted File System Using a Custom Key
---------------------------------------------------------------------

Creating an encrypted file system using the custom key in the example region (with the key ID **d8309a24-41ca-4a72-82f7-f699e39529a9** and the key's project ID **c80a2157ba1d46c0825265947342077c**):

.. code-block:: text

   PUT / HTTP/1.1
   Host: example-sfs-03.sfs3.example.region.com:443
   Date: Wed, 07 Jun 2023 02:38:09 GMT
   x-obs-bucket-type: SFS
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:75/Y4Ng1izvzc1nTGxpMXTE6ynw=
   Content-Length: 85
   x-obs-server-side-encryption: kms
   x-obs-server-side-encryption-kms-key-id:d8309a24-41ca-4a72-82f7-f699e39529a9
   x-obs-sse-kms-key-project-id:c80a2157ba1d46c0825265947342077c
   <CreateBucketConfiguration>
       <Location>example</Location>
   </CreateBucketConfiguration>

Example Response: Creating an Encrypted File System Using a Custom Key
----------------------------------------------------------------------

.. code-block::

   HTTP/1.1 200 OK
   Server: OBS
   X-Obs-Request-Id: 0000018893B8058EC0470388BE6EDE88
   Location: /example-sfs-03
   X-Obs-Id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCTRa4voOUvr50ncznQT/hligMxL4so2z
   x-obs-server-side-encryption-kms-key-id:d8309a24-41ca-4a72-82f7-f699e39529a9
   x-obs-sse-kms-key-project-id:c80a2157ba1d46c0825265947342077c
   Date: Wed, 07 Jun 2023 02:38:11 GMT
   Content-Length: 0

Status Codes
------------

=========== ===========================
Status Code Description
=========== ===========================
200         The file system is created.
=========== ===========================

Error Codes
-----------

See :ref:`General Purpose File System Error Codes <sfs_02_0119>`.
