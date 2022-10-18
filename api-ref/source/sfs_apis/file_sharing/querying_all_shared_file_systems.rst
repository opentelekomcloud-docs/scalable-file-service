:original_name: sfs_02_0022.html

.. _sfs_02_0022:

Querying All Shared File Systems
================================

Function
--------

This API is used to list the basic information of all shared file systems.

URI
---

-  GET /v2/{project_id}/shares?all_tenants={all_tenants}&status={status}&limit={limit}&offset={offset}&sort_key={sort_key}&sort_dir={sort_dir}&project_id={project_id}&is_public={is_public}&metadata={metadata}& export_location_id={export_location_id}& export_location_path={export_location_path}& name~={name}& description~={description}& with_count={with_count}
-  Parameter description

   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory            | Type            | Description                                                                                                                                                                                                                                                                                                                                                                         |
   +======================+======================+=================+=====================================================================================================================================================================================================================================================================================================================================================================================+
   | project_id           | Yes                  | String          | Specifies the project ID of the operator.                                                                                                                                                                                                                                                                                                                                           |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | all_tenants          | No (query parameter) | Boolean         | This parameter is available only to users with administrator permissions. Specifies whether to list shared file systems of all tenants. To list shared file systems of all tenants, set it to **1**. To list shared file systems only of the current tenant, set it to **0**.                                                                                                       |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id           | No (query parameter) | String          | This parameter is available only to users with administrator permissions. Specifies the ID of the project to which the shared file system belongs. This parameter needs to be used together with **all_tenants**.                                                                                                                                                                   |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status               | No (query parameter) | String          | Filters shared file systems by status. Possible values are:                                                                                                                                                                                                                                                                                                                         |
   |                      |                      |                 |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                      |                      |                 | -  **creating**: The shared file system is being created.                                                                                                                                                                                                                                                                                                                           |
   |                      |                      |                 | -  **error**: The shared file system fails to be created.                                                                                                                                                                                                                                                                                                                           |
   |                      |                      |                 | -  **available**: The shared file system is available.                                                                                                                                                                                                                                                                                                                              |
   |                      |                      |                 | -  **deleting**: The shared file system is being deleted.                                                                                                                                                                                                                                                                                                                           |
   |                      |                      |                 | -  **error_deleting**: The shared file system fails to be deleted.                                                                                                                                                                                                                                                                                                                  |
   |                      |                      |                 | -  **extending**: The shared file system is being expanded.                                                                                                                                                                                                                                                                                                                         |
   |                      |                      |                 | -  **extending_error**: The shared file system fails to be expanded.                                                                                                                                                                                                                                                                                                                |
   |                      |                      |                 | -  **shrinking**: The shared file system is being shrunk.                                                                                                                                                                                                                                                                                                                           |
   |                      |                      |                 | -  **shrinking_error**: The shared file system fails to be shrunk.                                                                                                                                                                                                                                                                                                                  |
   |                      |                      |                 | -  **shrinking_possible_data_loss_error**: The shared file system fails to be shrunk due to data loss.                                                                                                                                                                                                                                                                              |
   |                      |                      |                 | -  **manage_starting**: Shared file system management starts.                                                                                                                                                                                                                                                                                                                       |
   |                      |                      |                 | -  **manage_error**: The shared file system fails to be managed.                                                                                                                                                                                                                                                                                                                    |
   |                      |                      |                 | -  **unmanage_starting**: Canceling shared file system management starts.                                                                                                                                                                                                                                                                                                           |
   |                      |                      |                 | -  **unmanage_error**: Failed to cancel shared file system management.                                                                                                                                                                                                                                                                                                              |
   |                      |                      |                 | -  **unmanaged**: The shared file system is not managed.                                                                                                                                                                                                                                                                                                                            |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit                | No (query parameter) | Integer         | Specifies the maximum number of shared file systems that can be returned. If this parameter is not specified, all the shared file systems are returned by default.                                                                                                                                                                                                                  |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset               | No (query parameter) | Integer         | Specifies the offset to define the start point from 0 of shared file system listing. The value must be greater than or equal to **0**.                                                                                                                                                                                                                                              |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_key             | No (query parameter) | String          | Specifies the keyword for sorting the queried shared file systems. Possible values are **id**, **status**, **size**, **host**, **share_proto**, **availability_zone_id**, **user_id**, **project_id**, **created_at**, **updated_at**, **display_name**, **name**, **share_type_id**, **share_network_id**, and **snapshot_id**. By default, the value is sorted by **created_at**. |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_dir             | No (query parameter) | String          | Specifies the direction to sort shared file systems. Possible values are **asc** (ascending) and **desc** (descending).                                                                                                                                                                                                                                                             |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_public            | No (query parameter) | String          | When this parameter is set to **true**, the current tenant can query all its own shared file systems and other tenants' shared file systems whose **is_public** is set to **true**. When this parameter is set to **false**, the current tenant can query only the shared file systems owned by the tenant.                                                                         |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata             | No (query parameter) | String          | Specifies the metadata information used to query the shared file systems. The value consists of one or more key and value pairs organized as a dictionary of strings.                                                                                                                                                                                                               |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | export_location_id   | No (query parameter) | String          | Specifies the field used for filtering based on the ID of the mount path. This field is supported by API v2.35 and later versions.                                                                                                                                                                                                                                                  |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | export_location_path | No (query parameter) | String          | Specifies the field used for filtering based on the mount path. This field is supported by API v2.35 and later versions.                                                                                                                                                                                                                                                            |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name~                | No (query parameter) | String          | Specifies the field used for fuzzy filtering based on the name of a shared file system. This field is supported by API v2.36 and later versions.                                                                                                                                                                                                                                    |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description~         | No (query parameter) | String          | Specifies the field used for fuzzy filtering based on the description of a shared file system. This field is supported by API v2.36 and later versions.                                                                                                                                                                                                                             |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | with_count           | No (query parameter) | String          | Specifies whether the number of queried shared file systems is returned. This field is supported by API v2.42 and later versions. This parameter is specified by **?with_count=true** in the URI. The default value is **false**.                                                                                                                                                   |
   +----------------------+----------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   None

-  Example request

   GET https://{endpoint}/v2/16e1ab15c35a457e9c2b2aa189f544e1/shares

Response
--------

-  Parameter description

   +-----------+------------------+----------------------------------------------------------+
   | Parameter | Type             | Description                                              |
   +===========+==================+==========================================================+
   | shares    | Array of objects | For details, see the description of the **share** field. |
   +-----------+------------------+----------------------------------------------------------+
   | count     | String           | Specifies the number of returned shared file systems.    |
   +-----------+------------------+----------------------------------------------------------+

-  Description of the **share** field

   +-----------+------------------+-------------------------------------------------------------------+
   | Parameter | Type             | Description                                                       |
   +===========+==================+===================================================================+
   | id        | String           | Specifies the ID of the shared file system.                       |
   +-----------+------------------+-------------------------------------------------------------------+
   | links     | Array of objects | Specifies the request link information of the shared file system. |
   +-----------+------------------+-------------------------------------------------------------------+
   | name      | String           | Specifies the name of the shared file system.                     |
   +-----------+------------------+-------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "count": 1,
          "shares": [
          {
              "id": "1390cb29-539b-4926-8953-d8d6b106071a",
              "links": [
              {
                  "href": "https://192.168.196.47:8796/v2/f24555bfcf3146ca936d21bcb548687e/shares/1390cb29-539b-4926-8953-d8d6b106071a",
                  "rel": "self"
              },
              {
                  "href": "https://192.168.196.47:8796/f24555bfcf3146ca936d21bcb548687e/shares/1390cb29-539b-4926-8953-d8d6b106071a",
                  "rel": "bookmark"
              }
              ],
              "name": null
          }
      ]
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
