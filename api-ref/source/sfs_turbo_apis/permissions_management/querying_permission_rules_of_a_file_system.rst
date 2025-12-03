:original_name: ListPermRules.html

.. _ListPermRules:

Querying Permission Rules of a File System
==========================================

Function
--------

This API is used to query permission rules of a file system.

Constraints
-----------

A maximum of 64 permission rules can be added for a file system.

This API is only supported for NFS file systems.

URI
---

GET /v1/{project_id}/sfs-turbo/shares/{share_id}/fs/perm-rules

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===================
   project_id Yes       String The project ID.
   share_id   Yes       String The file system ID.
   ========== ========= ====== ===================

.. table:: **Table 2** Query Parameters

   +-----------+-----------+------+--------------------------------------------------------------+
   | Parameter | Mandatory | Type | Description                                                  |
   +===========+===========+======+==============================================================+
   | limit     | No        | Long | The maximum number of permission rules that can be returned. |
   +-----------+-----------+------+--------------------------------------------------------------+
   | offset    | No        | Long | The offset of the returned permission rules.                 |
   +-----------+-----------+------+--------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ============ ========= ====== ==================
   Parameter    Mandatory Type   Description
   ============ ========= ====== ==================
   X-Auth-Token Yes       String The account token.
   Content-Type Yes       String The MIME type.
   ============ ========= ====== ==================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+---------------------------------------------------------------------------------------------------+-----------------------------+
   | Parameter | Type                                                                                              | Description                 |
   +===========+===================================================================================================+=============================+
   | rules     | Array of :ref:`OnePermRuleResponseInfo <listpermrules__response_onepermruleresponseinfo>` objects | The permission information. |
   +-----------+---------------------------------------------------------------------------------------------------+-----------------------------+

.. _listpermrules__response_onepermruleresponseinfo:

.. table:: **Table 5** OnePermRuleResponseInfo

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                           |
   +=======================+=======================+=======================================================================================================================================================================================================+
   | id                    | String                | The permission rule ID.                                                                                                                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_cidr               | String                | The IP address or IP address range of the authorized object. It cannot be modified after configuration.                                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rw_type               | String                | The read/write permission of the authorized object.                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                       |
   |                       |                       | -  **rw**: read and write permission, which is the default option                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                       |
   |                       |                       | -  **ro**: read-only permission                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                       |
   |                       |                       | -  **none**: no permission                                                                                                                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_type             | String                | The file system access permission granted to the user of the authorized object. The value can be:                                                                                                     |
   |                       |                       |                                                                                                                                                                                                       |
   |                       |                       | -  **no_root_squash** (default value): allows any user including root on the client to access the file system as who they are, instead of mapping them to another user.                               |
   |                       |                       |                                                                                                                                                                                                       |
   |                       |                       | -  **root_squash**: allows root on the client to access the file system as **nfsnobody** and allows a non-root user on the client to access as who they are, instead of being mapped to another user. |
   |                       |                       |                                                                                                                                                                                                       |
   |                       |                       | -  **all_squash**: allows any user on the client to access the file system as **nfsnobody**.                                                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 500**

.. table:: **Table 6** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

Example Requests
----------------

Querying the permission rules of the file system whose ID is **77ba6f4b-6365-4895-8dda-bc7142af4dde**

.. code-block:: text

   GET HTTPS://{endpoint}/v1/{project_id}/sfs-turbo/shares/77ba6f4b-6365-4895-8dda-bc7142af4dde/fs/perm-rules

Example Responses
-----------------

**Status code: 200**

Successful query

-  Response example of querying the permission rules of a file system

   .. code-block::

      {
        "rules" : [ {
          "id" : "1131ed520xxxxxxebedb6e57xxxxxxxx",
          "ip_cidr" : "192.168.xx.xx/16",
          "rw_type" : "rw",
          "user_type" : "no_root_squash"
        }, {
          "id" : "1231ed520xxxxxxebedb6e57xxxxxxxx",
          "ip_cidr" : "192.32.xx.xx/16",
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
