:original_name: CreatePermRule.html

.. _CreatePermRule:

Creating a Permission Rule
==========================

Function
--------

This API is used to create a permission rule.

Constraints
-----------

A maximum of 64 permissions rules can be configured for a file system.

URI
---

POST /v1/{project_id}/sfs-turbo/shares/{share_id}/fs/perm-rules

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

   +-----------+-----------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                                            | Description                                                                |
   +===========+===========+=================================================================================================+============================================================================+
   | rules     | Yes       | Array of :ref:`OnePermRuleRequestInfo <createpermrule__request_onepermrulerequestinfo>` objects | Permission rule details. A maximum of five rules can be created at a time. |
   +-----------+-----------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+

.. _createpermrule__request_onepermrulerequestinfo:

.. table:: **Table 4** OnePermRuleRequestInfo

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================+
   | ip_cidr         | No              | String          | IP address or IP address range of the object to be authorized. Once configured, this parameter cannot be modified.                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rw_type         | No              | String          | Read/write permission of the object to be authorized.                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | -  **rw**: read and write permission, which is the default option                                                                                                |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | -  **ro**: read-only permission                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | -  **none**: no permission                                                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_type       | No              | String          | File system access permission granted to the user of the object to be authorized. Supported values are:                                                          |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | -  **no_root_squash**: allows any user including the root user on the client to access the file system as who they are, instead of mapping them to another user. |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | -  **root_squash**: allows the root user on the client to access the file system as **nfsnobody**.                                                               |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | -  **all_squash**: allows any user on the client to access the file system as **nfsnobody**.                                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------+----------------------------------------------------------------------------------------------------+-------------------------+
   | Parameter | Type                                                                                               | Description             |
   +===========+====================================================================================================+=========================+
   | rules     | Array of :ref:`OnePermRuleResponseInfo <createpermrule__response_onepermruleresponseinfo>` objects | Permission rule details |
   +-----------+----------------------------------------------------------------------------------------------------+-------------------------+

.. _createpermrule__response_onepermruleresponseinfo:

.. table:: **Table 6** OnePermRuleResponseInfo

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

.. table:: **Table 7** Response body parameters

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

**Status code: 500**

.. table:: **Table 8** Response body parameters

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

.. code-block::

   {
     "rules" : [ {
       "ip_cidr" : "192.168.0.0/16",
       "rw_type" : "rw",
       "user_type" : "no_root_squash"
     }, {
       "ip_cidr" : "192.32.0.0/16",
       "rw_type" : "rw",
       "user_type" : "no_root_squash"
     } ]
   }

Example Responses
-----------------

**Status code: 200**

Successful creation

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
