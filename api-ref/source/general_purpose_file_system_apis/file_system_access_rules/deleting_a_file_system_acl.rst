:original_name: sfs_02_0118.html

.. _sfs_02_0118:

Deleting a File System ACL
==========================

Function
--------

This API is used to delete a file system ACL.

URI
---

DELETE /

.. table:: **Table 1** Query parameter

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   sfsacl    Yes       String /
   ========= ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============= ========= ====== ==========================
   Parameter     Mandatory Type   Description
   ============= ========= ====== ==========================
   Date          Yes       String The request time.
   Authorization Yes       String The signature information.
   Host          Yes       String The host address.
   ============= ========= ====== ==========================

Response Parameters
-------------------

This response uses common headers. For details, see :ref:`Table 1 <sfs_02_0106__en-us_topic_0000001263068826_d0e686>`.

Example Request
---------------

.. code-block:: text

   DELETE /?sfsacl HTTP/1.1
   Host: examplefilesystem.sfs3.example.region.com
   Date: WED, 01 Jul 2015 02:36:06 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:jZiAT8Vx4azWEvPRMWi0X5BpJMA=

Example Response
----------------

.. code-block::

   HTTP/1.1 204 No Content
   Server: OBS
   X-Obs-Id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCSj4dxiqb1Lw50CTjVQeV3ebh3QQ6PAj
   X-Obs-Request-Id: 0000018893B807D5C0472A6161D87032
   Date: WED, 01 Jul 2015 02:36:06 GMT

Status Codes
------------

=========== ===============================
Status Code Description
=========== ===============================
204         The file system ACL is deleted.
=========== ===============================

Error Codes
-----------

See :ref:`General Purpose File System Error Codes <sfs_02_0119>`.
