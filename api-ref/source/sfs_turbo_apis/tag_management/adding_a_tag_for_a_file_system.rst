:original_name: CreateSharedTag.html

.. _CreateSharedTag:

Adding a Tag for a File System
==============================

Function
--------

This API is used to add a tag to a specified file system. A maximum of 20 tags can be added to a file system. Tag keys added to the same file system must be unique. This API is idempotent. If the file system already has the key you want to add, the tag will be updated.

URI
---

POST /v1/{project_id}/sfs-turbo/{share_id}/tags

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

   +-----------+-----------+------------------------------------------------------------------+-------------------------------------------+
   | Parameter | Mandatory | Type                                                             | Description                               |
   +===========+===========+==================================================================+===========================================+
   | tag       | Yes       | :ref:`ResourceTag <createsharedtag__request_resourcetag>` object | Description of the **resource_tag** field |
   +-----------+-----------+------------------------------------------------------------------+-------------------------------------------+

.. _createsharedtag__request_resourcetag:

.. table:: **Table 4** ResourceTag

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================================================================================================================================================+
   | key             | Yes             | String          | Tag key.                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It can contain a maximum of 128 characters.                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It cannot be left empty and cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_). |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Minimum: **1**                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Maximum: **128**                                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | Tag value.                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Each tag value can contain a maximum of 255 characters and can be an empty string.                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_).                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Minimum: **0**                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Maximum: **255**                                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Creating a file system tag, with tag value set to **key1** and tag key **value1**

.. code-block::

   {
     "tag" : {
       "key" : "key1",
       "value" : "value1"
     }
   }

Example Responses
-----------------

None

Status Codes
------------

=========== =============================
Status Code Description
=========== =============================
204         Tag adding request delivered.
=========== =============================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
