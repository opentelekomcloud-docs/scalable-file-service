:original_name: DeletePermRule.html

.. _DeletePermRule:

Deleting a Permission Rule
==========================

Function
--------

This API is used to delete a permission rule.

Constraints
-----------

This API is only supported for NFS file systems.

URI
---

DELETE /v1/{project_id}/sfs-turbo/shares/{share_id}/fs/perm-rules/{rule_id}

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

**Status code: 204**

Successful deletion

**Status code: 400**

.. table:: **Table 3** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

**Status code: 500**

.. table:: **Table 4** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

Example Requests
----------------

Deleting the permission rule whose ID is **11abef677ac40f46644d1d5cfc2424a4** for the file system whose ID is **77ba6f4b-6365-4895-8dda-bc7142af4dde**

.. code-block:: text

   DELETE HTTPS://{endpoint}/v1/{project_id}/sfs-turbo/shares/77ba6f4b-6365-4895-8dda-bc7142af4dde/fs/perm-rules/11abef677ac40f46644d1d5cfc2424a4

Example Responses
-----------------

**Status code: 500**

Error response

.. code-block::

   {
     "errCode" : "SFS.TURBO.0005",
     "errMsg" : "Internal server error"
   }

Status Codes
------------

=========== ===================
Status Code Description
=========== ===================
204         Successful deletion
400         Error response
500         Error response
=========== ===================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
