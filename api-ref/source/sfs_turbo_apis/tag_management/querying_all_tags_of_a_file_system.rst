:original_name: ShowSharedTags.html

.. _ShowSharedTags:

Querying All Tags of a File System
==================================

Function
--------

This API is used to query all tags of a file system.

URI
---

GET /v1/{project_id}/sfs-turbo/{share_id}/tags

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

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+----------------------------------------------------------------------------+---------------+
   | Parameter | Type                                                                       | Description   |
   +===========+============================================================================+===============+
   | tags      | Array of :ref:`ResourceTag <showsharedtags__response_resourcetag>` objects | The tag list. |
   +-----------+----------------------------------------------------------------------------+---------------+

.. _showsharedtags__response_resourcetag:

.. table:: **Table 4** ResourceTag

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================================================================================================================================+
   | key                   | String                | The tag key.                                                                                                                                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | It can contain a maximum of 128 characters.                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | It cannot be left empty and cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_). |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value                 | String                | The tag value.                                                                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Each tag value can contain a maximum of 255 characters and can be an empty string.                                                                                                                                                                                                                               |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | It cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_).                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying tags of the file system whose ID is **77ba6f4b-6365-4895-8dda-bc7142af4dde**

.. code-block:: text

   GET HTTPS://{endpoint}/v1/v1/{project_id}/sfs-turbo/77ba6f4b-6365-4895-8dda-bc7142af4dde/tags

Example Responses
-----------------

**Status code: 200**

Response body for query all tags of a specified file system

.. code-block::

   {
     "tags" : [ {
       "key" : "key1",
       "value" : "value1"
     }, {
       "key" : "key2",
       "value" : "value1"
     } ]
   }

Status Codes
------------

=========== ===========================================================
Status Code Description
=========== ===========================================================
200         Response body for query all tags of a specified file system
=========== ===========================================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
