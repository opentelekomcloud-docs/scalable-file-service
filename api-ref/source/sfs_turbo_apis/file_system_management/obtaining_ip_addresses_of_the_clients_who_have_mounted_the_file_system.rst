:original_name: ShowClientIpInfo.html

.. _ShowClientIpInfo:

Obtaining IP Addresses of the Clients Who Have Mounted the File System
======================================================================

Function
--------

This API is used to obtain the IP addresses of the clients who have mounted the file system.

URI
---

POST /v1/{project_id}/sfs-turbo/shares/{share_id}/action

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===================
   project_id Yes       String The project ID.
   share_id   Yes       String The file system ID.
   ========== ========= ====== ===================

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ==================
   Parameter    Mandatory Type   Description
   ============ ========= ====== ==================
   X-Auth-Token Yes       String The account token.
   Content-Type Yes       String The MIME type.
   ============ ========= ====== ==================

.. table:: **Table 3** Request body parameters

   +----------------+-----------+---------------------------------------------------------------------+------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type                                                                | Description                                                            |
   +================+===========+=====================================================================+========================================================================+
   | get_client_ips | Yes       | :ref:`ClientIpInfo <showclientipinfo__request_clientipinfo>` object | Obtaining IP addresses of the clients who have mounted the file system |
   +----------------+-----------+---------------------------------------------------------------------+------------------------------------------------------------------------+

.. _showclientipinfo__request_clientipinfo:

.. table:: **Table 4** ClientIpInfo

   +-----------+-----------+--------+-------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                       |
   +===========+===========+========+===================================================================+
   | ips       | No        | String | The IP addresses of the clients who have mounted the file system. |
   +-----------+-----------+--------+-------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response header parameters

   ============ ====== ===============
   Parameter    Type   Description
   ============ ====== ===============
   X-request-id String The request ID.
   ============ ====== ===============

.. table:: **Table 6** Response body parameters

   +-----------+------------------+-------------------------------------------------------------------+
   | Parameter | Type             | Description                                                       |
   +===========+==================+===================================================================+
   | id        | String           | The file system ID.                                               |
   +-----------+------------------+-------------------------------------------------------------------+
   | ips       | Array of strings | The IP addresses of the clients who have mounted the file system. |
   +-----------+------------------+-------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 7** Response header parameters

   ============ ====== ===============
   Parameter    Type   Description
   ============ ====== ===============
   X-request-id String The request ID.
   ============ ====== ===============

.. table:: **Table 8** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

**Status code: 500**

.. table:: **Table 9** Response header parameters

   ============ ====== ===============
   Parameter    Type   Description
   ============ ====== ===============
   X-request-id String The request ID.
   ============ ====== ===============

.. table:: **Table 10** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 400**

Error response

.. code-block::

   {
     "errCode" : "SFS.TURBO.0001",
     "errMsg" : "parameter error"
   }

**Status code: 500**

Error response

.. code-block::

   {
     "errCode" : "SFS.TURBO.0005",
     "errMsg" : "Internal server error"
   }

Status Codes
------------

=========== ==============
Status Code Description
=========== ==============
200         Success
400         Error response
500         Error response
=========== ==============

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
