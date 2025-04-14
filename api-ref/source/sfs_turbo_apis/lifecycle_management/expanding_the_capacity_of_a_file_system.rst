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

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================================================================================================================================================+
   | new_size        | Yes             | Integer         | New capacity of the file system after expansion, in GiB.                                                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                 | The value ranges from 500 GiB to 32768 GiB, and the capacity expansion step is greater than or equal to 100 GiB.                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                 | Specifications of the previous-generation SFS Turbo file system: Standard Enhanced and Performance Enhanced. The capacity ranges from 10240 GiB to 327680 GiB. The capacity expansion step is greater than or equal to 100 GiB.                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                 | 20 MB/s/TiB. The capacity ranges from 3686 GiB to 1048576 GiB. The capacity must be a multiple of 1.2 TiB, and the capacity expansion step must be greater than or equal to 1.2 TiB. The target capacity must be converted to GiB and then rounded down. For example, 4.8 TiB->4915 GiB, 8.4 TiB->8601 GiB. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                 | 40 MB/s/TiB. The capacity ranges from 1228 GiB to 1048576 GiB. The capacity must be a multiple of 1.2 TiB, and the capacity expansion step must be greater than or equal to 1.2 TiB. The target capacity must be converted to GiB and then rounded down. For example, 4.8 TiB->4915 GiB, 8.4 TiB->8601 GiB. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                 | 125 MB/s/TiB, 250 MB/s/TiB and 40 MB/s/TiB, the expansion steps are the same.                                                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
