:original_name: sfs_02_0113.html

.. _sfs_02_0113:

Deleting a File System
======================

Function
--------

This API is used to delete a file system.

URI
---

DELETE /

Request Parameters
------------------

.. table:: **Table 1** Request header parameters

   ============= ========= ====== ===========================
   Parameter     Mandatory Type   Description
   ============= ========= ====== ===========================
   Authorization Yes       String The signature header field.
   Date          Yes       String The request time.
   Host          Yes       String The host address.
   ============= ========= ====== ===========================

Response Parameters
-------------------

This response uses common headers. For details, see :ref:`Table 1 <sfs_02_0106__en-us_topic_0000001263068826_d0e686>`.

Example Request
---------------

.. code-block:: text

   DELETE / HTTP/1.1
   User-Agent: curl/7.29.0
   Host: examplefilesystem.sfs3.example.region.com
   Accept: */*
   Date: WED, 01 Jul 2015 02:31:25 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:jZiAT8Vx4azWEvPRMWi0X5BpJMA=

Example Response
----------------

.. code-block::

   HTTP/1.1 204 No Content
   Server: OBS
   X-Obs-Request-Id: 0000018893B8081DC047305E783867DD
   X-Obs-Id-2: 32AAAQAAEAABSkAgAAEAABAAAQAAEAABCT5UWgsaro3EEnOsNEzf8w8dnydR+Eak
   Date: WED, 01 Jul 2015 02:31:25 GMT

Status Codes
------------

=========== ===========================
Status Code Description
=========== ===========================
204         The file system is deleted.
=========== ===========================

Error Codes
-----------

See :ref:`General Purpose File System Error Codes <sfs_02_0119>`.
