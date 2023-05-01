:original_name: sfs_02_0032.html

.. _sfs_02_0032:

Quota Management
================

Function
--------

This API is used to query quota information.

URI
---

-  GET /v2/{project_id}/os-quota-sets/{project_id}
-  Parameter description

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                        |
   +============+===========+========+====================================================================================================================================================================================+
   | project_id | Yes       | String | Specifies the project ID of the operator.                                                                                                                                          |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Specifies the ID of the tenant whose quotas are to be queried, updated, or deleted. This ID differs from the first project ID (the administrative tenant ID) contained in the URI. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Query parameter

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                |
   +===========+===========+========+============================================================================================================+
   | usage     | No        | String | If the parameter is set to **true**, the current **in_use** and **reserved** counts will also be returned. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   None

-  Example request

   .. code-block:: text

      GET /v2/{project_id}/os-quota-sets/{project_id_1}?usage=true

Response
--------

-  Parameter description

   ========= ====== ====================================
   Parameter Type   Description
   ========= ====== ====================================
   quota_set Object Specifies the **quota_set** objects.
   ========= ====== ====================================

-  Description of field **quota_set**

   +--------------------+---------+-----------------------------------------------------------------------+
   | Parameter          | Type    | Description                                                           |
   +====================+=========+=======================================================================+
   | gigabytes          | Integer | Specifies the capacity in gigabytes allowed for each tenant.          |
   +--------------------+---------+-----------------------------------------------------------------------+
   | snapshots          | Integer | Specifies the number of snapshots allowed for each tenant.            |
   +--------------------+---------+-----------------------------------------------------------------------+
   | shares             | Integer | Specifies the number of shared file systems allowed for each tenant.  |
   +--------------------+---------+-----------------------------------------------------------------------+
   | snapshot_gigabytes | Integer | Specifies the snapshot capacity in gigabytes allowed for each tenant. |
   +--------------------+---------+-----------------------------------------------------------------------+
   | id                 | String  | Specifies the ID of the tenant for which you manage quotas.           |
   +--------------------+---------+-----------------------------------------------------------------------+
   | share_networks     | Integer | Specifies the number of share networks allowed for each tenant.       |
   +--------------------+---------+-----------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "quota_set": {
          "gigabytes": {
            "reserved": 0,
            "limit": 512000,
            "in_use": 645
          },
          "snapshots": {
            "reserved": 0,
            "limit": -1,
            "in_use": 0
          },
          "snapshot_gigabytes": {
            "reserved": 0,
            "limit": -1,
            "in_use": 0
          },
          "shares": {
            "reserved": 0,
            "limit": 10,
            "in_use": 4
          },
          "id": "da0f615c35eb4d72812d1547a77b5394",
          "share_networks": {
            "reserved": 0,
            "limit": 10,
            "in_use": 0
          }
        }
      }

Status Codes
------------

-  Normal

   200

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
