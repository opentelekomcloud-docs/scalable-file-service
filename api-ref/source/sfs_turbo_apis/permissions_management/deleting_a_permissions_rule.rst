:original_name: en-us_topic_0000001614557076.html

.. _en-us_topic_0000001614557076:

Deleting a Permissions Rule
===========================

Function
--------

This API is used to delete a permission rule.

URI
---

DELETE /v1/{project_id}/sfs-turbo/shares/{share_id}/fs/perm-rules/{rule_id}

.. table:: **Table 1** Path parameters

   ========== ========= ====== ==================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ==================
   project_id Yes       String Project ID
   share_id   Yes       String File system ID
   rule_id    Yes       String Permission rule ID
   ========== ========= ====== ==================

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

**Status code: 400**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+--------------------------------+
   | Parameter             | Type                  | Description                    |
   +=======================+=======================+================================+
   | errCode               | String                | Error code                     |
   |                       |                       |                                |
   |                       |                       | Minimum length: 8 characters   |
   |                       |                       |                                |
   |                       |                       | Maximum length: 36 characters  |
   +-----------------------+-----------------------+--------------------------------+
   | errMsg                | String                | Error message                  |
   |                       |                       |                                |
   |                       |                       | Minimum length: 2 characters   |
   |                       |                       |                                |
   |                       |                       | Maximum length: 512 characters |
   +-----------------------+-----------------------+--------------------------------+

**Status code: 500**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+--------------------------------+
   | Parameter             | Type                  | Description                    |
   +=======================+=======================+================================+
   | errCode               | String                | Error code                     |
   |                       |                       |                                |
   |                       |                       | Minimum length: 8 characters   |
   |                       |                       |                                |
   |                       |                       | Maximum length: 36 characters  |
   +-----------------------+-----------------------+--------------------------------+
   | errMsg                | String                | Error message                  |
   |                       |                       |                                |
   |                       |                       | Minimum length: 2 characters   |
   |                       |                       |                                |
   |                       |                       | Maximum length: 512 characters |
   +-----------------------+-----------------------+--------------------------------+

Example Request
---------------

None

Example Response
----------------

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
