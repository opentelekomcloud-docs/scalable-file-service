:original_name: sfs_02_0044.html

.. _sfs_02_0044:

Querying the Number of Shared File Systems by Tag
=================================================

Function
--------

This API is used to query the number of shared file systems by tag.

URI
---

-  POST /v2/{project_id}/sfs/resource_instances/action
-  Parameter description

   ========== ========= ====== =========================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================================
   project_id Yes       String Specifies the project ID of the operator.
   ========== ========= ====== =========================================

Request
-------

-  Parameter description

   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   +=================+=================+==================+=============================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | action          | Yes             | String           | Specifies the operation identifier. Possible values are **filter** and **count**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                  | Use **count** to query the number of share instances based on tags.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | No              | Array of matches | Specifies the file system query field. If this parameter is left null, all shared file systems of the tenant are searched by default.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | Array of tags    | Specifies the tag search field, which is a list of tags. Only shared file systems containing all the listed tags can be returned. Tags in this search criteria are in the AND relationship. Specifically, a shared file system can be searched only when it meets all the tag search criteria. In the key-values structure of each tag search condition, tag values are in the OR relationship. If the value of **tags** is not specified, all shared file systems meet the requirement of this tag search field. This field contains a maximum of 20 tag keys and each tag key has a maximum of 10 tag values. The tag value corresponding to each tag key can be an empty array but the structure cannot be missing. Tag keys must be unique. Tag values in a key-values structure must be unique.                        |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags_any        | No              | Array of tags    | Specifies the tag search field, which is a list of tags. Shared file systems that contain any listed tag will be returned. Tags in this search criteria are in the OR relationship. Specifically, a shared file system can be searched as long as it meets one tag search condition. In the key-values structure of each tag search condition, tag values are in the OR relationship. If the value of **tags_any** is not specified, all shared file systems meet the requirement of this tag search field. This field contains a maximum of 20 tag keys and each tag key has a maximum of 10 tag values. The tag value corresponding to each tag key can be an empty array but the structure cannot be missing. Tag keys must be unique. Tag values in a key-values structure must be unique.                              |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags        | No              | Array of tags    | Specifies the tag search field, which is a list of tags. Only shared file systems that contain none of the listed tags will be returned. Tags in this search criteria are in the NOR relationship. Specifically, a shared file system can be searched only when it does not meet any tag search criteria. In the key-values structure of each tag search condition, tag values are in the OR relationship. If the value of **not_tags** is not specified, all shared file systems meet the requirement of this tag search field. This field contains a maximum of 20 tag keys and each tag key has a maximum of 10 tag values. The tag value corresponding to each tag key can be an empty array but the structure cannot be missing. Tag keys must be unique. Tag values in a key-values structure must be unique.         |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags_any    | No              | Array of tags    | Specifies the tag search field, which is a list of tags. Shared file systems that do not contain any of the listed tags will be returned. Tags in this search criteria are in the NAND relationship. Specifically, a shared file system can be searched as long as it does not meet one tag search condition. In the key-values structure of each tag search condition, tag values are in the OR relationship. If the value of **not_tags_any** is not specified, all shared file systems meet the requirement of this tag search field. This field contains a maximum of 20 tag keys and each tag key has a maximum of 10 tag values. The tag value corresponding to each tag key can be an empty array but the structure cannot be missing. Tag keys must be unique. Tag values in a key-values structure must be unique. |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sys_tags        | No              | Array of tags    | Only the op_service permission can use this field to filter resources.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                  | #. Currently, TMS can invoke only one tag structure key, **\_sys_enterprise_project_id**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                  | #. Currently, **key** contains only one value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                  | #. **sys_tags** and tenant tag filtering conditions (**tags**, **tags_any**, **not_tags**, and **not_tags_any**) cannot be used at the same time.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. important::

      In the request parameters, tag search fields **tags**, **tags_any**, **not_tags**, and **not_tags_any** are optional and can be combined with each other. Such tag search fields are in the AND relationship.

-  Description of the **match** field

   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                              |
   +===========+===========+========+==========================================================================================================================================================================================================================================================================================================+
   | key       | Yes       | String | Specifies the key. The value is fixed to **resource_name**.                                                                                                                                                                                                                                              |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value     | Yes       | String | Specifies the value. **value** indicates the name of a shared file system. An empty string specifies an exact match and only shared file systems whose names are empty can be queried. A non-empty string specifies a fuzzy query (case insensitive). The value can contain a maximum of 255 characters. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Description of the **tag** field

   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                                                                                                                    |
   +===========+===========+==================+================================================================================================================================================================+
   | key       | Yes       | String           | Specifies the key of the tag. A tag key can contain a maximum of 127 characters. This parameter cannot be left blank.                                          |
   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | values    | Yes       | Array of strings | Lists the values. Each value can contain a maximum of 255 characters. If the value is left empty, any value is matched. The values are in the OR relationship. |
   +-----------+-----------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   Querying the number of shared file systems (file system name **share_name**) using tag (key1, value2)

   .. code-block::

      {
          "action": "count",
          "matches": [{
              "key": "resource_name",
              "value": "share_name"
          }],
          "tags": [{
              "key": "key1",
              "values": ["value2"]
          }, {
              "key": "key2",
              "values": []
          }],
          "tags_any": [{
              "key": "key3",
              "values": ["value3"]
          }, {
              "key": "key4",
              "values": []
          }],
          "not_tags": [{
              "key": "key5",
              "values": ["value5"]
          }, {
              "key": "key6",
              "values": []
          }],
          "not_tags_any": [{
              "key": "key7",
              "values": ["value7", "value8"]
          }, {
              "key": "key9",
              "values": []
          }]
      }

-  Example request (without passing **matches**)

   Querying the number of shared file systems using tag (key1, value2)

   .. code-block::

      {
          "action": "count",
          "tags": [{
              "key": "key1",
              "values": ["value2"]
          }, {
              "key": "key2",
              "values": []
          }]
      }

-  Example request (without passing **tags**, **not_tags**, **tags_any**, and **not_tags_any**)

   Querying the number of shared file systems (file system name **share_name**)

   .. code-block::

      {
          "action": "count",
          "matches": [{
              "key": "resource_name",
              "value": "share_name"
          }]
      }

-  Example request (with the **action** field only)

   Querying the total number of shared file systems of the tenant

   .. code-block::

      {
          "action": "count"
      }

Response
--------

-  Parameter description

   +-------------+---------+---------------------------------------------------------------------------------+
   | Parameter   | Type    | Description                                                                     |
   +=============+=========+=================================================================================+
   | total_count | Integer | Specifies the total number of shared file systems that meet the query criteria. |
   +-------------+---------+---------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "total_count":1
      }

Status Codes
------------

-  Normal

   200

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
