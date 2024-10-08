:original_name: sfs_02_0030.html

.. _sfs_02_0030:

Deleting a File System Access Rule
==================================

Function
--------

This API is used to delete a file system access rule.

.. note::

   This API is an asynchronous API. If the returned status code is **202**, the API request is successfully delivered and received. Later, you can refer to :ref:`Querying File System Access Rules <sfs_02_0031>` to identify whether the access rule is deleted successfully.

URI
---

-  POST /v2/{project_id}/shares/{share_id}/action
-  Parameter description

   ========== ========= ====== ===========================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========================================
   share_id   Yes       String Specifies the ID of the shared file system.
   project_id Yes       String Specifies the project ID of the operator.
   ========== ========= ====== ===========================================

Request
-------

-  Parameter description

   ============== ========= ====== ========================================
   Parameter      Mandatory Type   Description
   ============== ========= ====== ========================================
   os-deny_access Yes       Object Specifies the **os-deny_access** object.
   ============== ========= ====== ========================================

   .. note::

      If the API version ranges from 1.0 to 2.6, the top-layer parameters of the request body in the JSON format use prefix **os-**. If the API version is later than 2.6, prefix **os-** must be removed.

-  Description of field **os-deny_access**

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                           |
   +===========+===========+========+=======================================================================================================+
   | access_id | Yes       | String | Specifies the ID of the access rule of the shared file system. The value contains 1 to 36 characters. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------+

-  Example request

   Deleting a file system access rule (rule ID: **418e3cf4-08c3-4ed2-a29a-ceffa346b3b8**):

   .. code-block::

      {
          "os-deny_access": {
              "access_id": "418e3cf4-08c3-4ed2-a29a-ceffa346b3b8"
          }
      }

Response
--------

-  Parameter description

None

-  Example response

   None

Status Codes
------------

-  Normal

   202

-  Abnormal

   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | Status Code                       | Description                                                                                |
   +===================================+============================================================================================+
   | 400 Bad Request                   | The server failed to process the request.                                                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 401 Unauthorized                  | You must enter a username and the password to access the requested page.                   |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 403 Forbidden                     | Access to the requested page is forbidden.                                                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 404 Not Found                     | The requested page was not found.                                                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 405 Method Not Allowed            | You are not allowed to use the method specified in the request.                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 406 Not Acceptable                | The response generated by the server could not be accepted by the client.                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 407 Proxy Authentication Required | You must use the proxy server for authentication. Then the request can be processed.       |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 408 Request Timeout               | The request timed out.                                                                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 409 Conflict                      | The request could not be processed due to a conflict.                                      |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 500 Internal Server Error         | Failed to complete the request because of an internal service error.                       |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 501 Not Implemented               | Failed to complete the request because the server does not support the requested function. |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 502 Bad Gateway                   | Failed to complete the request because the request is invalid.                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 503 Service Unavailable           | Failed to complete the request because the service is unavailable.                         |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 504 Gateway Timeout               | A gateway timeout error occurred.                                                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
