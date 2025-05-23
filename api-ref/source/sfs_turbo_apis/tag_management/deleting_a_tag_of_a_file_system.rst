:original_name: DeleteSharedTag.html

.. _DeleteSharedTag:

Deleting a Tag of a File System
===============================

Function
--------

This API is used to delete a tag of a specified file system. If the key to be deleted does not exist, error 404 will be returned.

URI
---

DELETE /v1/{project_id}/sfs-turbo/{share_id}/tags/{key}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID                                                                                                                                                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_id        | Yes             | String          | File system ID                                                                                                                                                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key             | Yes             | String          | Tag key, which can contain a maximum of 128 characters.                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | It cannot be left blank and cannot contain the following characters: ASCII (0-31), equal signs (=), asterisks (``*``), left angle brackets (<), right angle brackets (>), backslashes (), commas (,), vertical bars (|), and slashes (/). It can contain only letters, digits, hyphens (-), and underscores (_). |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | When this API is called to delete a tag, if the tag key contains special characters that cannot be directly resolved by the URL, the key needs to be escaped.                                                                                                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

None

Example Requests
----------------

Deleting tags whose key is **test** for the file system whose ID is **77ba6f4b-6365-4895-8dda-bc7142af4dde**

.. code-block:: text

   DELETE HTTPS://{endpoint}/v1/{project_id}/sfs-turbo/77ba6f4b-6365-4895-8dda-bc7142af4dde/tags/test

Example Responses
-----------------

None

Status Codes
------------

=========== ========================
Status Code Description
=========== ========================
204         File system tag deleted.
=========== ========================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
