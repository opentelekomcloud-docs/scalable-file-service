:original_name: BatchAddSharedTags.html

.. _BatchAddSharedTags:

Batch Adding Tags to a File System
==================================

Function
--------

This API is used to batch add tags to a file system.

A maximum of 20 tags can be added to a file system.

Tag keys added to the same file system must be unique.

This API is idempotent. If the file system already has the key you want to add, the tag will be updated.

URI
---

POST /v1/{project_id}/sfs-turbo/{share_id}/tags/action

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

   +-----------------+-----------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                          | Description                                                                                                       |
   +=================+=================+===============================================================================+===================================================================================================================+
   | action          | Yes             | String                                                                        | The operation identifier. The value is **create**. Use **create** if you want to batch add tags to a file system. |
   |                 |                 |                                                                               |                                                                                                                   |
   |                 |                 |                                                                               | Enumeration values:                                                                                               |
   |                 |                 |                                                                               |                                                                                                                   |
   |                 |                 |                                                                               | -  **create**                                                                                                     |
   +-----------------+-----------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | tags            | Yes             | Array of :ref:`ResourceTag <batchaddsharedtags__request_resourcetag>` objects | The list of tags.                                                                                                 |
   +-----------------+-----------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+

.. _batchaddsharedtags__request_resourcetag:

.. table:: **Table 4** ResourceTag

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================================================================================================================================================+
   | key             | Yes             | String          | The tag key.                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It can contain a maximum of 128 characters.                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It cannot be left empty and cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_). |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | The tag value.                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Each tag value can contain a maximum of 255 characters and can be an empty string.                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_).                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

Batch adding tags succeeded

None

Example Requests
----------------

Batch adding tags to a file system, with tag key of the first tag set to **key1**, tag value of the first tag **value1**, tag key of the second tag **key2**, and tag value of the second tag **value1**

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

=========== ===========================
Status Code Description
=========== ===========================
204         Batch adding tags succeeded
=========== ===========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
