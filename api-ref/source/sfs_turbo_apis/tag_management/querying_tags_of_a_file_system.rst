:original_name: ShowSharedTags.html

.. _ShowSharedTags:

Querying Tags of a File System
==============================

Function
--------

This API is used to query all tags of a specified file system.

URI
---

GET /v1/{project_id}/sfs-turbo/{share_id}/tags

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                       | Description                                                                                            |
   +=======================+============================================================================+========================================================================================================+
   | tags                  | Array of :ref:`ResourceTag <showsharedtags__response_resourcetag>` objects | Tag list                                                                                               |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
   | sys_tags              | Array of :ref:`ResourceTag <showsharedtags__response_resourcetag>` objects | Only users with the op_service permission can obtain this field.                                       |
   |                       |                                                                            |                                                                                                        |
   |                       |                                                                            | #. This field currently contains only one resource_tag structure key, **\_sys_enterprise_project_id**. |
   |                       |                                                                            |                                                                                                        |
   |                       |                                                                            | #. The key contains only value **0** currently, which indicates the default enterprise project.        |
   |                       |                                                                            |                                                                                                        |
   |                       |                                                                            | This field is not returned for users without the op_service permission.                                |
   +-----------------------+----------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+

.. _showsharedtags__response_resourcetag:

.. table:: **Table 4** ResourceTag

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================================================================================================================================+
   | key                   | String                | Tag key.                                                                                                                                                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | It can contain a maximum of 128 characters.                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | It cannot be left empty and cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_). |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Minimum: **1**                                                                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Maximum: **128**                                                                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value                 | String                | Tag value.                                                                                                                                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Each tag value can contain a maximum of 255 characters and can be an empty string.                                                                                                                                                                                                                               |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | It cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_).                          |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Minimum: **0**                                                                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Maximum: **255**                                                                                                                                                                                                                                                                                                 |
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
