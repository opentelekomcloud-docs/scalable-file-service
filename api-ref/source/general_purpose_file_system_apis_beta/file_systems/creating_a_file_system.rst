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
   -  If a file system is deleted, you can only create a file system with the same name as the deleted one 30 minutes after that file system has been deleted.

URI
---

PUT /

Request Parameters
------------------

.. table:: **Table 1** Request header parameters

   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                              |
   +=====================+=================+=================+==========================================================================================================+
   | Authorization       | Yes             | String          | The signature information.                                                                               |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Date                | Yes             | String          | The request time.                                                                                        |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | x-obs-az-redundancy | Yes             | String          | When creating a file system, you must include this header, which sets the file system redundancy to 3AZ. |
   |                     |                 |                 |                                                                                                          |
   |                     |                 |                 | Example: **x-obs-az-redundancy:3az**                                                                     |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | x-obs-bucket-type   | Yes             | String          | The header used to specify the file system creation.                                                     |
   |                     |                 |                 |                                                                                                          |
   |                     |                 |                 | Enumerated value:                                                                                        |
   |                     |                 |                 |                                                                                                          |
   |                     |                 |                 | -  **SFS**                                                                                               |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Host                | Yes             | String          | The host address.                                                                                        |
   +---------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+

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

Example Request
---------------

Creating a file system in example (with the host address **Host: example-sfs-01.sfs3.example.region.com:443**):

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

Example Response
----------------

.. code-block::

   HTTP/1.1 200 OK
   Server: OBS
   X-Obs-Request-Id: 0000018893B8058EC0470388BE6EDE88
   Location: /example-sfs-01
   X-Obs-Id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCTRa4voOUvr50ncznQT/hligMxL4so2z
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
