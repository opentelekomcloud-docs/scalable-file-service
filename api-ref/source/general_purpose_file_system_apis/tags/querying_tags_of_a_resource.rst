:original_name: sfs_03_0004.html

.. _sfs_03_0004:

Querying Tags of a Resource
===========================

Function
--------

This API is used to query tags of a specified resource.

URI
---

-  GET /v3/sfs/tms/{project_id}/file-systems/{resource_id}/tags

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

Response Parameters
-------------------

.. table:: **Table 2** Response body parameters

   +-----------------+-----------------+-----------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                    | Description                                                                                                  |
   +=================+=================+=========================================================================================+==============================================================================================================+
   | tags            | No              | List<:ref:`resource_tag <sfs_03_0002__en-us_topic_0000001886392461_table667613216170>`> | The tag list. For details, see :ref:`Table 3 <sfs_03_0002__en-us_topic_0000001886392461_table667613216170>`. |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | sys_tags        | No              | List<:ref:`resource_tag <sfs_03_0002__en-us_topic_0000001886392461_table667613216170>`> | The system tag list. This parameter is only available to users with the **op_service** permission.           |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | This field contains only one **resource_tag** structure currently.                                           |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | The key is fixed at **\_sys_enterprise_project_id**.                                                         |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | The value is the ID of an enterprise project. Value **0** indicates the default enterprise project.          |
   |                 |                 |                                                                                         |                                                                                                              |
   |                 |                 |                                                                                         | For details, see :ref:`Table 3 <sfs_03_0002__en-us_topic_0000001886392461_table667613216170>`.               |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Querying tags of a general purpose file system whose name is **bucketName** with the project ID **c80a2157ba1d46c0825265947342077c**:

.. code-block:: text

   GET https://{endpoint}/v3/sfs/tms/c80a2157ba1d46c0825265947342077c/file-systems/bucketName/tags

Example Response
----------------

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

Status Codes
------------

-  Normal

=========== ======================
Status Code Description
=========== ======================
200         Resource tags queried.
=========== ======================

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
