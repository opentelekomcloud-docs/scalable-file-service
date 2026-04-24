:original_name: sfs_03_0002.html

.. _sfs_03_0002:

Batch Adding Tags to a Resource
===============================

Function
--------

This API is used to batch add tags for a general purpose file system. You can add up to 20 tags to a resource.

URI
---

-  POST /v3/sfs/tms/{project_id}/file-systems/{resource_id}/tags/create
-  Parameter description

   +-------------+-----------+--------+----------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                          |
   +=============+===========+========+======================================================================+
   | project_id  | Yes       | String | The project ID.                                                      |
   +-------------+-----------+--------+----------------------------------------------------------------------+
   | resource_id | Yes       | String | The resource ID, which is the name of a general purpose file system. |
   +-------------+-----------+--------+----------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 1** Request header parameters

   +-----------------+-----------------+-----------------+------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                        |
   +=================+=================+=================+====================================+
   | Content-type    | Yes             | String          | The MIME type of the request body. |
   |                 |                 |                 |                                    |
   |                 |                 |                 | Example: application/json          |
   +-----------------+-----------------+-----------------+------------------------------------+
   | X-Auth-Token    | No              | String          | The user token.                    |
   +-----------------+-----------------+-----------------+------------------------------------+

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+-----------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                    | Description                                                                                                  |
   +=================+=================+=========================================================================================+==============================================================================================================+
   | tags            | No              | List<:ref:`resource_tag <sfs_03_0002__en-us_topic_0000001886392461_table667613216170>`> | The tag list. For details, see :ref:`Table 3 <sfs_03_0002__en-us_topic_0000001886392461_table667613216170>`. |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | This parameter is mandatory for common tenants.                                                              |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | Use either **tags** or **sys_tags** if you have the op_service permissions.                                  |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | sys_tags        | No              | List<:ref:`resource_tag <sfs_03_0002__en-us_topic_0000001886392461_table667613216170>`> | The system tag list. This parameter is available only to the op_service permissions.                         |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | Use either **tags** or **sys_tags** if you have the op_service permissions.                                  |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | Only one **resource_tag** structure is used in TMS calls currently.                                          |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | The key is fixed at **\_sys_enterprise_project_id**.                                                         |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | The value can be **UUID** or **0**. **0** indicates the default enterprise project.                          |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | System tags can only be added.                                                                               |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | For details, see :ref:`Table 3 <sfs_03_0002__en-us_topic_0000001886392461_table667613216170>`.               |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+

.. _sfs_03_0002__en-us_topic_0000001886392461_table667613216170:

.. table:: **Table 3** resource_tag

   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                                                |
   +===========+===========+========+============================================================================================================================================================================================================================================================================================================================================+
   | key       | Yes       | String | The tag key. A tag key can contain a maximum of 128 characters. It can contain letters, digits, and spaces representable in UTF-8 and special characters ``(_.:=+-@).`` It cannot start or end with a space and cannot be left empty. Tag keys starting with **\_sys\_** are system tags, and you cannot start a tag key with **\_sys\_**. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value     | No        | String | The tag value. A tag value can contain a maximum of 255 characters. It can contain letters, digits, and spaces representable in UTF-8 and special characters ``(_.:=+-@)`` and can be left empty. It cannot start or end with a space.                                                                                                     |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

Batch adding tags to a general purpose file system whose name is **bucketName** with the project ID **c80a2157ba1d46c0825265947342077c**:

.. code-block:: text

   POST https://{endpoint}/v3/sfs/tms/c80a2157ba1d46c0825265947342077c/file-systems/bucketName/tags/create

Request body example:

.. code-block::

   {
       "tags":[
           {
               "key":"key1",
               "value":"value1"
           },
           {
               "key":"key2",
               "value":"value2"
           }
       ]
   }

Example Response
----------------

None

Status Codes
------------

-  Normal

=========== ========================
Status Code Description
=========== ========================
204         Resource tags are added.
=========== ========================

-  Abnormal

=========== ======================
Status Code Description
=========== ======================
400         Invalid tag parameter.
401         Certification failed.
403         Authentication failed.
404         Resource not found.
500         System error.
=========== ======================
