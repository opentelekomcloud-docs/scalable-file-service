:original_name: BatchAddSharedTags.html

.. _BatchAddSharedTags:

Batch Adding Tags to a File System
==================================

Function
--------

This API is used to batch add tags for a specified file system.

A maximum of 20 tags can be added to a file system.

Tag keys added to the same file system must be unique.

This API is idempotent. If the file system already has the key you want to add, the tag will be updated.

URI
---

POST /v1/{project_id}/sfs-turbo/{share_id}/tags/action

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

   +-----------------+-----------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                          | Description                                                                                                                                                                                             |
   +=================+=================+===============================================================================+=========================================================================================================================================================================================================+
   | action          | Yes             | String                                                                        | Operation identifier. The value is **create**. Use **create** if you want to batch add tags to a file system.                                                                                           |
   +-----------------+-----------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | Array of :ref:`ResourceTag <batchaddsharedtags__request_resourcetag>` objects | Tag list.                                                                                                                                                                                               |
   |                 |                 |                                                                               |                                                                                                                                                                                                         |
   |                 |                 |                                                                               | This field is mandatory for users. For users with the op_service permission, choose either this field or **sys_tags**.                                                                                  |
   +-----------------+-----------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sys_tags        | No              | Array of :ref:`ResourceTag <batchaddsharedtags__request_resourcetag>` objects | System tag list.                                                                                                                                                                                        |
   |                 |                 |                                                                               |                                                                                                                                                                                                         |
   |                 |                 |                                                                               | This field is available only to users with the op_service permission. Choose either this field or **tags**. Only one resource_tag structure key, **\_sys_enterprise_project_id**, is used in TMS calls. |
   +-----------------+-----------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _batchaddsharedtags__request_resourcetag:

.. table:: **Table 4** ResourceTag

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================================================================================================================================================+
   | key             | Yes             | String          | Tag key.                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It can contain a maximum of 128 characters.                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It cannot be left empty and cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_). |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | Tag value.                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Each tag value can contain a maximum of 255 characters and can be an empty string.                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_).                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Batch adding tags for a file system, with tag key of the first tag set to **key1**, tag value of the first tag **value1**, tag key of the second tag **key2**, and tag value of the second tag **value1**

.. code-block::

   {
     "action" : "create",
     "tags" : [ {
       "key" : "key1",
       "value" : "value1"
     }, {
       "key" : "key2",
       "value" : "value1"
     } ]
   }

Example Responses
-----------------

None

Status Codes
------------

=========== =======================
Status Code Description
=========== =======================
204         File system tags added.
=========== =======================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
