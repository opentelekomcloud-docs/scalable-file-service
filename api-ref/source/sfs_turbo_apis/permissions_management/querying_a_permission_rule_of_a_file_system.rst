:original_name: ShowPermRule.html

.. _ShowPermRule:

Querying a Permission Rule of a File System
===========================================

Function
--------

This API is used to query a permission rule of a file system.

Constraints
-----------

This API is only supported for NFS file systems.

URI
---

GET /v1/{project_id}/sfs-turbo/shares/{share_id}/fs/perm-rules/{rule_id}

.. table:: **Table 1** Path Parameters

   ========== ========= ====== =======================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =======================
   project_id Yes       String The project ID.
   share_id   Yes       String The file system ID.
   rule_id    Yes       String The permission rule ID.
   ========== ========= ====== =======================

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ==================
   Parameter    Mandatory Type   Description
   ============ ========= ====== ==================
   X-Auth-Token Yes       String The account token.
   Content-Type Yes       String The MIME type.
   ============ ========= ====== ==================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

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

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

**Status code: 500**

.. table:: **Table 5** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

Example Requests
----------------

Querying details about the permission rule whose ID is **11abef677ac40f46644d1d5cfc2424a4** for the file system whose ID is **77ba6f4b-6365-4895-8dda-bc7142af4dde**

.. code-block:: text

   GET HTTPS://{endpoint}/v1/{project_id}/sfs-turbo/shares/77ba6f4b-6365-4895-8dda-bc7142af4dde/fs/perm-rules/11abef677ac40f46644d1d5cfc2424a4

Example Responses
-----------------

**Status code: 200**

Successful query

-  Response example of querying a specific permission rule of a file system

   .. code-block::

      {
        "id" : "1131ed520xxxxxxebedb6e57xxxxxxxx",
        "ip_cidr" : "192.168.xx.xx/16",
        "rw_type" : "rw",
        "user_type" : "no_root_squash"
      }

**Status code: 400**

Error response

.. code-block::

   {
     "errCode" : "SFS.TURBO.0001",
     "errMsg" : "Invalid rule id"
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
400         Error response
500         Error response
=========== ================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
