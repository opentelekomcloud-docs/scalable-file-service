:original_name: DeleteShare.html

.. _DeleteShare:

Deleting a File System
======================

Function
--------

This API is used to delete a file system.

URI
---

DELETE /v1/{project_id}/sfs-turbo/shares/{share_id}

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

Response Parameters
-------------------

**Status code: 202**

File system deletion request delivered

None

Example Requests
----------------

Deleting the file system whose ID is **77ba6f4b-6365-4895-8dda-bc7142af4dde**

.. code-block:: text

   DELETE HTTPS://{endpoint}/v1/{project_id}/sfs-turbo/shares/77ba6f4b-6365-4895-8dda-bc7142af4dde

Example Responses
-----------------

None

Status Codes
------------

=========== ======================================
Status Code Description
=========== ======================================
202         File system deletion request delivered
=========== ======================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
