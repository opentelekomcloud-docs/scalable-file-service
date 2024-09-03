:original_name: ListPermRules.html

.. _ListPermRules:

Querying Permission Rules of a File System
==========================================

Function
--------

This API is used to query the permission rules of a file system.

URI
---

GET /v1/{project_id}/sfs-turbo/shares/{share_id}/fs/perm-rules

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+---------------------------------------------------------------------------------------------------+-----------------------------+
   | Parameter | Type                                                                                              | Description                 |
   +===========+===================================================================================================+=============================+
   | rules     | Array of :ref:`OnePermRuleResponseInfo <listpermrules__response_onepermruleresponseinfo>` objects | Permission rule information |
   +-----------+---------------------------------------------------------------------------------------------------+-----------------------------+

.. _listpermrules__response_onepermruleresponseinfo:

.. table:: **Table 4** OnePermRuleResponseInfo

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                           |
   +=======================+=======================+=======================================================================================================================+
   | id                    | String                | Permission rule ID                                                                                                    |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | ip_cidr               | String                | IP address or IP address range of the authorized object                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | rw_type               | String                | Read/write permission of the authorized object.                                                                       |
   |                       |                       |                                                                                                                       |
   |                       |                       | -  **rw**: read and write permission, which is the default option                                                     |
   |                       |                       |                                                                                                                       |
   |                       |                       | -  **ro**: read-only permission                                                                                       |
   |                       |                       |                                                                                                                       |
   |                       |                       | -  **none**: no permission                                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | user_type             | String                | File system access permission granted to the user of the authorized object. Supported values are:                     |
   |                       |                       |                                                                                                                       |
   |                       |                       | -  **no_root_squash**: allows the root user on the client to access the file system as **root**.                      |
   |                       |                       |                                                                                                                       |
   |                       |                       | -  **root_squash**: allows the root user on the client to access the file system as **nfsnobody**.                    |
   |                       |                       |                                                                                                                       |
   |                       |                       | -  **all_squash**: allows any user on the client to access the file system as **nfsnobody**. It is the default value. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+

**Status code: 500**

.. table:: **Table 5** Response body parameters

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | errCode               | String                | Error code            |
   |                       |                       |                       |
   |                       |                       | Minimum: **8**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **36**       |
   +-----------------------+-----------------------+-----------------------+
   | errMsg                | String                | Error description     |
   |                       |                       |                       |
   |                       |                       | Minimum: **2**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **512**      |
   +-----------------------+-----------------------+-----------------------+

Example Requests
----------------

Querying the permission rules of the file system whose ID is **77ba6f4b-6365-4895-8dda-bc7142af4dde**

.. code-block:: text

   GET HTTPS://{endpoint}/v1/{project_id}/sfs-turbo/shares/77ba6f4b-6365-4895-8dda-bc7142af4dde/fs/perm-rules

Example Responses
-----------------

**Status code: 200**

Successful query

.. code-block::

   {
     "rules" : [ {
       "id" : "1131ed520xxxxxxebedb6e57xxxxxxxx",
       "ip_cidr" : "192.168.0.0/16",
       "rw_type" : "rw",
       "user_type" : "no_root_squash"
     }, {
       "id" : "1231ed520xxxxxxebedb6e57xxxxxxxx",
       "ip_cidr" : "192.32.0.0/16",
       "rw_type" : "rw",
       "user_type" : "no_root_squash"
     } ]
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

=========== ================
Status Code Description
=========== ================
200         Successful query
500         Error response
=========== ================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
