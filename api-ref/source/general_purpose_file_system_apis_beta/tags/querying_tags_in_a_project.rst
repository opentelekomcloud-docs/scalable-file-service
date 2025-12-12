:original_name: sfs_03_0007.html

.. _sfs_03_0007:

Querying Tags in a Project
==========================

Function
--------

This API is used to query tags of all resources owned by a tenant in a specified project.

URI
---

-  GET /v3/sfs/tms/{project_id}/file-systems/tags
-  Parameter description

   ========== ========= ====== ===============
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===============
   project_id Yes       String The project ID.
   ========== ========= ====== ===============

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

.. table:: **Table 2** Response body parameter

   +-----------+-----------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                           | Description                                                                                                  |
   +===========+===========+================================================================================+==============================================================================================================+
   | tags      | Yes       | List<:ref:`tag <sfs_03_0005__en-us_topic_0000001840191462_table138157172456>`> | The tag list. For details, see :ref:`Table 3 <sfs_03_0005__en-us_topic_0000001840191462_table138157172456>`. |
   +-----------+-----------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+

Example Request
---------------

Querying tags using project ID \**c80a2157ba1d46c0825265947342077c**:

.. code-block:: text

   GET https://{endpoint}/v3/sfs/tms/c80a2157ba1d46c0825265947342077c/file-systems/tags

Example Response
----------------

.. code-block::

   {
       "tags":[
           {
               "key":"key1",
               "values":[
                   "value1",
                   "value2"
               ]
           },
           {
               "key":"key2",
               "values":[
                   "value1",
                   "value2"
               ]
           }
       ]
   }

Status Codes
------------

-  Normal

=========== =================================
Status Code Description
=========== =================================
200         Resource tags queried by project.
=========== =================================

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
