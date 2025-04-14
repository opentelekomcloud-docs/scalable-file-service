:original_name: UpdatePermRule.html

.. _UpdatePermRule:

Modifying a Permission Rule
===========================

Function
--------

This API is used to modify a permission rule.

URI
---

PUT /v1/{project_id}/sfs-turbo/shares/{share_id}/fs/perm-rules/{rule_id}

.. table:: **Table 1** Path Parameters

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

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                    |
   +=================+=================+=================+================================================================================================================================================================================================================================================+
   | ip_cidr         | No              | String          | IP address or IP address range of the object to be authorized. Once configured, this parameter cannot be modified.                                                                                                                             |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rw_type         | No              | String          | Read/write permission of the object to be authorized.                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                |
   |                 |                 |                 | -  **rw**: read and write permission, which is the default option                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                |
   |                 |                 |                 | -  **ro**: read-only permission                                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                |
   |                 |                 |                 | -  **none**: no permission                                                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_type       | No              | String          | System user's permission to access the file system. The value can be any of the following:                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                |
   |                 |                 |                 | -  no_root_squash: default option. The client uses any user, including the root user. The NFS server retains the user used by the client and does not map the user.                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                |
   |                 |                 |                 | -  root_squash: When the client uses the root user, the user mapped to the NFS server is the NFS anonymous user (nfsnobody). If the client uses a non-root user, the NFS server retains the user used by the client and does not map the user. |
   |                 |                 |                 |                                                                                                                                                                                                                                                |
   |                 |                 |                 | -  all_squash: All users of clients that access the NFS server are mapped as anonymous users.                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

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

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========= ====== =================
   Parameter Type   Description
   ========= ====== =================
   errCode   String Error code
   errMsg    String Error description
   ========= ====== =================

**Status code: 500**

.. table:: **Table 6** Response body parameters

   ========= ====== =================
   Parameter Type   Description
   ========= ====== =================
   errCode   String Error code
   errMsg    String Error description
   ========= ====== =================

Example Requests
----------------

.. code-block::

   {
     "rw_type" : "rw",
     "user_type" : "no_root_squash"
   }

Example Responses
-----------------

**Status code: 200**

Successful creation

.. code-block::

   {
     "id" : "1131ed520xxxxxxebedb6e57xxxxxxxx",
     "ip_cidr" : "192.32.0.0/16",
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

=========== ===================
Status Code Description
=========== ===================
200         Successful creation
400         Error response
500         Error response
=========== ===================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
