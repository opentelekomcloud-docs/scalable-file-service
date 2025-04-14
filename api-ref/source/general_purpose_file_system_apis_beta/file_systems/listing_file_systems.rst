:original_name: sfs_02_0114.html

.. _sfs_02_0114:

Listing File Systems
====================

Function
--------

This API is used to list file systems.

URI
---

GET /

Request Parameters
------------------

.. table:: **Table 1** Request header parameters

   +-------------------+-----------------+-----------------+--------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                            |
   +===================+=================+=================+========================================================+
   | x-obs-bucket-type | Yes             | String          | The header used to specify the content to be obtained. |
   |                   |                 |                 |                                                        |
   |                   |                 |                 | Enumerated value:                                      |
   |                   |                 |                 |                                                        |
   |                   |                 |                 | -  **SFS**: listing all file systems                   |
   +-------------------+-----------------+-----------------+--------------------------------------------------------+
   | Authorization     | Yes             | String          | The signature information.                             |
   +-------------------+-----------------+-----------------+--------------------------------------------------------+
   | Date              | Yes             | String          | The request time.                                      |
   +-------------------+-----------------+-----------------+--------------------------------------------------------+
   | Host              | Yes             | String          | The host address.                                      |
   +-------------------+-----------------+-----------------+--------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+-----------------------------------------------------------------------------------------------------------------+---------------------------------------------------------+
   | Parameter | Type                                                                                                            | Description                                             |
   +===========+=================================================================================================================+=========================================================+
   | Owner     | :ref:`Owner <sfs_02_0114__en-us_topic_0000001263591136_en-us_topic_0000001263399526_response_owner>` object     | File system owner information, including the tenant ID. |
   +-----------+-----------------------------------------------------------------------------------------------------------------+---------------------------------------------------------+
   | Buckets   | :ref:`Buckets <sfs_02_0114__en-us_topic_0000001263591136_en-us_topic_0000001263399526_response_buckets>` object | The list of file systems owned by the user.             |
   +-----------+-----------------------------------------------------------------------------------------------------------------+---------------------------------------------------------+

.. _sfs_02_0114__en-us_topic_0000001263591136_en-us_topic_0000001263399526_response_owner:

.. table:: **Table 3** Owner

   ========= ====== =====================================
   Parameter Type   Description
   ========= ====== =====================================
   ID        String The domain ID (account ID) of a user.
   ========= ====== =====================================

.. _sfs_02_0114__en-us_topic_0000001263591136_en-us_topic_0000001263399526_response_buckets:

.. table:: **Table 4** Buckets

   +-----------+---------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter | Type                                                                                                          | Description                       |
   +===========+===============================================================================================================+===================================+
   | Bucket    | :ref:`Bucket <sfs_02_0114__en-us_topic_0000001263591136_en-us_topic_0000001263399526_response_bucket>` object | Detailed file system information. |
   +-----------+---------------------------------------------------------------------------------------------------------------+-----------------------------------+

.. _sfs_02_0114__en-us_topic_0000001263591136_en-us_topic_0000001263399526_response_bucket:

.. table:: **Table 5** Bucket

   ============ ====== ========================================
   Parameter    Type   Description
   ============ ====== ========================================
   Name         String The name of a file system.
   CreationDate String The time when a file system was created.
   Location     String The location of a file system.
   ============ ====== ========================================

Example Request
---------------

.. code-block:: text

   GET / HTTP/1.1
   Host: sfs3.example.region.com
   Date: date
   x-obs-bucket-type: SFS
   Authorization: authorization

Example Response
----------------

.. code-block::

   HTTP/1.1 200 OK
   Server: OBS
   X-Obs-Request-Id: 0000018893B8126DC048B06DD3816BD4
   X-Obs-Id-2: 32AAAQAAEAABAAAQAAEAABAAAQAAEAABCTMZh3Thi7lcDxuGWu9Qtp9PJbYXa7lb
   Date: Wed, 07 Jun 2023 02:38:14 GMT
   Content-Type: application/xml
   Content-Length: 377

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ListAllMyBucketsResult xmlns="http://obs.otc.t-systems.com/doc/2016-01-01/">
     <Owner>
       <ID>783fc6652cf246c096ea836694f71855</ID>
     </Owner>
     <Buckets>
       <Bucket>
         <Name>examplebucket01</Name>
         <CreationDate>2018-06-21T09:15:01.032Z</CreationDate>
         <Location>example-region-1</Location>
         <BucketType>SFS</BucketType>
       </Bucket>
       <Bucket>
         <Name>examplebucket02</Name>
         <CreationDate>2018-06-22T03:56:33.700Z</CreationDate>
         <Location>example-region-2</Location>
         <BucketType>SFS</BucketType>
       </Bucket>
     </Buckets>
   </ListAllMyBucketsResult>

Status Codes
------------

=========== ==============================
Status Code Description
=========== ==============================
200         The file systems are obtained.
=========== ==============================

Error Codes
-----------

See :ref:`General Purpose File System Error Codes <sfs_02_0119>`.
