:original_name: sfs_02_0038.html

.. _sfs_02_0038:

Deleting a Tag from a Shared File System
========================================

Function
--------

This API is used to delete a tag from a specified shared file system.

.. note::

   If the key to be deleted does not exist in the shared file system, error 404 is returned after API calling.

URI
---

-  DELETE /v2/{project_id}/sfs/{share_id}/tags/{key}
-  Parameter description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================================================+
   | project_id      | Yes             | String          | Specifies the project ID of the operator.                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_id        | Yes             | String          | Specifies the ID of the shared file system.                                                                                                                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key             | Yes             | String          | Specifies the tag key. The value can contain a maximum of 36 characters. The key cannot be left blank and can only contain letters, digits, hyphens (-), and underscores (_). |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | .. important::                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 |    NOTICE:                                                                                                                                                                    |
   |                 |                 |                 |    When calling this API to delete a tag, if the tag key contains special characters that are not directly resolved by the URL, the key needs to be escaped.                  |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   None

-  Example request

   None

Response
--------

-  Parameter description

   None

-  Example response

   None

Status Codes
------------

-  Normal

   204

-  Abnormal

   +---------------------------+----------------------------------------------------------+
   | Status Code               | Description                                              |
   +===========================+==========================================================+
   | 400 Bad Request           | Invalid value.                                           |
   +---------------------------+----------------------------------------------------------+
   | 401 Unauthorized          | Authentication failed.                                   |
   +---------------------------+----------------------------------------------------------+
   | 403 Forbidden             | Access to the requested page is forbidden.               |
   +---------------------------+----------------------------------------------------------+
   | 404 Not Found             | The requested resource was not found.                    |
   +---------------------------+----------------------------------------------------------+
   | 500 Internal Server Error | The request is not completed because of a service error. |
   +---------------------------+----------------------------------------------------------+
