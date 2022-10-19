:original_name: sfs_02_0018.html

.. _sfs_02_0018:

Querying All API Versions
=========================

Function
--------

This API is used to query all available versions of APIs provided by SFS.

To support function extension, SFS APIs can be distinguished by version. SFS has two types API version IDs:

Major version: Independent URL. For example: **v1** and **v2**.

Microversion: with the HTTP request header **X-Openstack-Manila-Api-Version:** *Microversion ID*. For example: **X-Openstack-Manila-Api-Version: 2.4**.

.. note::

   This API does not require authentication.

URI
---

-  GET /
-  Parameter description

None

Request
-------

-  Parameter description

   None

-  Example request

   GET https://{endpoint}/

Response
--------

-  Parameter description

   +-----------+------------------+---------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                               |
   +===========+==================+===========================================================================+
   | versions  | Array of objects | Lists objects of all available API versions, including **v1** and **v2**. |
   +-----------+------------------+---------------------------------------------------------------------------+

-  Description of the **version** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                   |
   +=======================+=======================+===============================================================================================================================================================================+
   | id                    | String                | Specifies the common name of the version.                                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated               | String                | Specifies the UTC time when the API is last modified. The format is YYYY-MM-DDTHH:MM:SSZ.                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                | Specifies the API version status, including:                                                                                                                                  |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  **CURRENT**: indicates that the current API is the preferred version.                                                                                                      |
   |                       |                       | -  **SUPPORTED**: indicates that the current version is an earlier version which is still supported.                                                                          |
   |                       |                       | -  **DEPRECATED**: indicates that the current version is a deprecated version that may be deleted later.                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links                 | Array of objects      | Specifies the share links. For details, see the description of the **links** field.                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | media-types           | Array of objects      | Specifies the media types supported by the API. For details, see the description of the **media-types** field.                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version               | String                | If the API in the current version supports microversions, this parameter is the latest microversion. If microversions are not supported, this parameter is an empty string.   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_version           | String                | If the API in the current version supports microversions, this parameter is the earliest microversion. If microversions are not supported, this parameter is an empty string. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Description of the **links** field

   +-----------+--------+---------------------------------------------------------------+
   | Parameter | Type   | Description                                                   |
   +===========+========+===============================================================+
   | href      | String | Specifies the API access path, which is used as a reference.  |
   +-----------+--------+---------------------------------------------------------------+
   | type      | String | Specifies the type of the text returned by the reference API. |
   +-----------+--------+---------------------------------------------------------------+
   | rel       | String | Specifies the additional description on links.                |
   +-----------+--------+---------------------------------------------------------------+

-  Description of the **media-types** field

   ========= ====== ==============================
   Parameter Type   Description
   ========= ====== ==============================
   base      String Specifies the basic text type.
   type      String Specifies the text type.
   ========= ====== ==============================

-  Example response

   .. code-block::

      {
        "versions": [
          {
            "status": "CURRENT",
            "updated": "2015-08-27T11:33:21Z",
            "links": [
              {
                "href": "http://docs.openstack.org/",
                "type": "text/html",
                "rel": "describedby"
              },
              {
                "href": "https://sfs.region.www.t-systems.com/v2/",
                "rel": "self"
              }
            ],
            "min_version": "2.0",
            "version": "2.28",
            "media-types": [
              {
                "base": "application/json",
                "type": "application/vnd.openstack.share+json;version=1"
              }
            ],
            "id": "v2.0"
          }
        ]
      }

Status Codes
------------

-  Normal

   300

-  Abnormal

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Status Code                       | Description                                                                                                                                                     |
   +===================================+=================================================================================================================================================================+
   | 400 Bad Request                   | The server failed to process the request.                                                                                                                       |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 400 Bad Request                   | Invalid input: The post-deduction capacity must be larger than 0 and smaller than the current capacity. (Current capacity: *XX*; post-deduction capacity: *XX*) |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 400 Bad Request                   | Invalid input: The post-expansion capacity must be larger than the current capacity. (Current capacity: *XX*; post-expansion capacity: *XX*)                    |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 401 Unauthorized                  | You must enter a username and the password to access the requested page.                                                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 403 Forbidden                     | Access to the requested page is forbidden.                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 404 Not Found                     | The requested page was not found.                                                                                                                               |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 405 Method Not Allowed            | You are not allowed to use the method specified in the request.                                                                                                 |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 406 Not Acceptable                | The response generated by the server could not be accepted by the client.                                                                                       |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 407 Proxy Authentication Required | You must use the proxy server for authentication. Then the request can be processed.                                                                            |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 408 Request Timeout               | The request timed out.                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 409 Conflict                      | The request could not be processed due to a conflict.                                                                                                           |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 500 Internal Server Error         | The request is not completed because of a service error.                                                                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 501 Not Implemented               | The request is not completed because the server does not support the requested function.                                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 502 Bad Gateway                   | The request is not completed because the request is invalid.                                                                                                    |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 503 Service Unavailable           | The request is not completed because the service is unavailable.                                                                                                |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 504 Gateway Timeout               | A gateway timeout error occurred.                                                                                                                               |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
