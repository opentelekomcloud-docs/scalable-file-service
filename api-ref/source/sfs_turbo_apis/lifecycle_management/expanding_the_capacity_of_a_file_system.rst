:original_name: ExpandShare.html

.. _ExpandShare:

Expanding the Capacity of a File System
=======================================

Function
--------

This API is used to expand the capacity of a file system.

URI
---

POST /v1/{project_id}/sfs-turbo/shares/{share_id}/action

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ==============
   Parameter  Mandatory Type   Description
   ========== ========= ====== ==============
   project_id Yes       String Project ID
   share_id   Yes       String File system ID
   ========== ========= ====== ==============

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

   +-----------+-----------+----------------------------------------------------+----------------------+
   | Parameter | Mandatory | Type                                               | Description          |
   +===========+===========+====================================================+======================+
   | extend    | Yes       | :ref:`Extend <expandshare__request_extend>` object | Object of **extend** |
   +-----------+-----------+----------------------------------------------------+----------------------+

.. _expandshare__request_extend:

.. table:: **Table 4** Extend

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================================================================================================================================================================================================+
   | new_size        | Yes             | Integer         | New capacity of the file system, in GiB                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | For a previous-generation Standard or Performance file system, the capacity ranges from **500** to **32768** (in GiB), and the expansion increment is 100 GiB.                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | For a previous-generation Standard - Enhanced or Performance Enhanced file system, the capacity ranges from **10240** to **327680** (in GiB), and the expansion increment is 100 GiB.                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | For a 20 MB/s/TiB file system, the capacity ranges from **3686** to **1048576** (in GiB) and must be a multiple of 1.2 TiB. The desired capacity must be converted to GiB and rounded down to the nearest integer. For example, use 4915 GiB for a 4.8 TiB file system and 8601 GiB for a 8.4 TiB file system. The expansion increment is 1.2 TiB. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | For a 40 MB/s/TiB file system, the capacity ranges from **1228** to **1048576** (in GiB) and must be a multiple of 1.2 TiB. The desired capacity must be converted to GiB and rounded down to the nearest integer. For example, use 4915 GiB for a 4.8 TiB file system and 8601 GiB for a 8.4 TiB file system. The expansion increment is 1.2 TiB. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | The capacity range and expansion increment of 250 MB/s/TiB and 125 MB/s/TiB file systems are the same as those of 40 MB/s/TiB file systems.                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | Minimum: **500**                                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | Maximum: **1048576**                                                                                                                                                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 5** Response body parameters

   ========= ====== =================================
   Parameter Type   Description
   ========= ====== =================================
   id        String ID of the SFS Turbo file system
   name      String Name of the SFS Turbo file system
   ========= ====== =================================

Example Requests
----------------

Expanding the capacity of a file system to 1,000 GB

.. code-block::

   {
     "extend" : {
       "new_size" : 1000
     }
   }

Example Responses
-----------------

**Status code: 202**

Response body for expanding the capacity of a file system

.. code-block::

   {
     "id" : "67d4bd5e-7b2f-4c24-9a0b-c0038940c6f8",
     "name" : "sfs-turbo-test"
   }

Status Codes
------------

=========== =========================================================
Status Code Description
=========== =========================================================
202         Response body for expanding the capacity of a file system
=========== =========================================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
