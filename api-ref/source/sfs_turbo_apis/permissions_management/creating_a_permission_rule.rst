:original_name: CreatePermRule.html

.. _CreatePermRule:

Creating a Permission Rule
==========================

Function
--------

This API is used to create a permission rule.

Constraints
-----------

A maximum of 64 permission rules can be added for a file system.

This API is only supported for NFS file systems.

URI
---

POST /v1/{project_id}/sfs-turbo/shares/{share_id}/fs/perm-rules

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

   +-----------+-----------+-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                                            | Description                                                                 |
   +===========+===========+=================================================================================================+=============================================================================+
   | rules     | Yes       | Array of :ref:`OnePermRuleRequestInfo <createpermrule__request_onepermrulerequestinfo>` objects | The permission rule details. You can add a maximum of five rules at a time. |
   +-----------+-----------+-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+

.. _createpermrule__request_onepermrulerequestinfo:

.. table:: **Table 4** OnePermRuleRequestInfo

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================================================================================+
   | ip_cidr         | Yes             | String          | The IP address or IP address range of the object to be authorized. Once configured, this parameter cannot be modified.                                                                                   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rw_type         | Yes             | String          | The read/write permission of the object to be authorized.                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                          |
   |                 |                 |                 | -  **rw**: read and write permission, which is the default option                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                          |
   |                 |                 |                 | -  **ro**: read-only permission                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                          |
   |                 |                 |                 | -  **none**: no permission                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_type       | Yes             | String          | The file system access permission granted to the user of the object to be authorized. The value can be:                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                          |
   |                 |                 |                 | -  **no_root_squash**: allows any user including root on the client to access the file system as who they are, instead of mapping them to another user.                                                  |
   |                 |                 |                 |                                                                                                                                                                                                          |
   |                 |                 |                 | -  **root_squash**: allows root on the client to access the file system as **nfsnobody**. Client access using a non-root user will be retained as who they are, instead of being mapped to another user. |
   |                 |                 |                 |                                                                                                                                                                                                          |
   |                 |                 |                 | -  **all_squash**: allows any user on the client to access the file system as **nfsnobody**.                                                                                                             |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------+----------------------------------------------------------------------------------------------------+----------------------------------+
   | Parameter | Type                                                                                               | Description                      |
   +===========+====================================================================================================+==================================+
   | rules     | Array of :ref:`OnePermRuleResponseInfo <createpermrule__response_onepermruleresponseinfo>` objects | The permission rule information. |
   +-----------+----------------------------------------------------------------------------------------------------+----------------------------------+

.. _createpermrule__response_onepermruleresponseinfo:

.. table:: **Table 6** OnePermRuleResponseInfo

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

.. table:: **Table 7** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   errCode   String The error code.
   errMsg    String The error message.
   ========= ====== ==================

Example Requests
----------------

-  Request example for creating permission rules

   .. code-block::

      {
        "rules" : [ {
          "ip_cidr" : "192.168.xx.xx/16",
          "rw_type" : "rw",
          "user_type" : "no_root_squash"
        }, {
          "ip_cidr" : "192.32.xx.xx/16",
          "rw_type" : "rw",
          "user_type" : "no_root_squash"
        } ]
      }

Example Responses
-----------------

**Status code: 200**

Successful creation

-  Response example for creating permission rules

   .. code-block::

      {
        "rules" : [ {
          "id" : "1131ed520xxxxxxebedb6e57xxxxxxxx",
          "ip_cidr" : "192.32.0.0/16",
          "rw_type" : "rw",
          "user_type" : "no_root_squash"
        }, {
          "id" : "1131ed520xxxxxxebedb6e57xxxxxxxx",
          "ip_cidr" : "192.32.0.1",
          "rw_type" : "rw",
          "user_type" : "no_root_squash"
        } ]
      }

**Status code: 400**

Error response

.. code-block::

   {
     "errCode" : "SFS.TURBO.0001",
     "errMsg" : "Rules not allowed empty"
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
