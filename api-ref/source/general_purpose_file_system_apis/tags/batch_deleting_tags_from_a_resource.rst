:original_name: sfs_03_0003.html

.. _sfs_03_0003:

Batch Deleting Tags from a Resource
===================================

Function
--------

This API is used to batch delete tags from a specified resource. System tags cannot be deleted. If any tag to be deleted is not found, a successful result is returned.

URI
---

-  POST /v3/sfs/tms/{project_id}/file-systems/{resource_id}/tags/delete

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

   +-----------+-----------+-----------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                                    | Description                                                                                                  |
   +===========+===========+=========================================================================================+==============================================================================================================+
   | tags      | Yes       | List<:ref:`resource_tag <sfs_03_0002__en-us_topic_0000001886392461_table667613216170>`> | The tag list. For details, see :ref:`Table 3 <sfs_03_0002__en-us_topic_0000001886392461_table667613216170>`. |
   +-----------+-----------+-----------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

Batch deleting tags from a general purpose file system whose name is **bucketName** with the project ID **c80a2157ba1d46c0825265947342077c**:

.. code-block:: text

   POST https://{endpoint}/v3/sfs/tms/c80a2157ba1d46c0825265947342077c/file-systems/bucketName/tags/delete

Request body example:

.. code-block::

   {
       "tags":[
           {
               "key":"key1"
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

=========== ==========================
Status Code Description
=========== ==========================
204         Resource tags are deleted.
=========== ==========================

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
