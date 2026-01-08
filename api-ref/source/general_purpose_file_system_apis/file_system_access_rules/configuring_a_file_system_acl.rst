:original_name: sfs_02_0116.html

.. _sfs_02_0116:

Configuring a File System ACL
=============================

Function
--------

This API is used to configure a file system ACL.

.. note::

   After the ACL is configured, the configuration takes about 30 second to take effect.

URI
---

PUT /

.. table:: **Table 1** Query parameter

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   sfsacl    Yes       String /
   ========= ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============= ========= ====== ==========================
   Parameter     Mandatory Type   Description
   ============= ========= ====== ==========================
   Date          Yes       String The request time.
   Authorization Yes       String The signature information.
   Host          Yes       String The host address.
   ============= ========= ====== ==========================

.. _sfs_02_0116__en-us_topic_0000001310871229_en-us_topic_0000001311039645_request_statement:

.. table:: **Table 3** Request body parameter

   +-----------+-----------+------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter | Mandatory | Type                                                                                                                         | Description           |
   +===========+===========+==============================================================================================================================+=======================+
   | Statement | No        | Array of :ref:`Statement <sfs_02_0116__en-us_topic_0000001310871229_en-us_topic_0000001311039645_request_statement>` objects | Unique identification |
   +-----------+-----------+------------------------------------------------------------------------------------------------------------------------------+-----------------------+

.. table:: **Table 4** Statement

   +-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                                               | Description                                                       |
   +=================+=================+====================================================================================================================+===================================================================+
   | Sid             | No              | String                                                                                                             | The statement ID.                                                 |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | Action          | Yes             | String                                                                                                             | The allowed statement action.                                     |
   |                 |                 |                                                                                                                    |                                                                   |
   |                 |                 |                                                                                                                    | Enumerated values:                                                |
   |                 |                 |                                                                                                                    |                                                                   |
   |                 |                 |                                                                                                                    | -  **FullControl**: read/write                                    |
   |                 |                 |                                                                                                                    | -  **Read**: read-only                                            |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | Effect          | Yes             | String                                                                                                             | The effect specifying that the statement permission is **Allow**. |
   |                 |                 |                                                                                                                    |                                                                   |
   |                 |                 |                                                                                                                    | Enumerated value:                                                 |
   |                 |                 |                                                                                                                    |                                                                   |
   |                 |                 |                                                                                                                    | -  **Allow**                                                      |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | Condition       | Yes             | :ref:`Condition <sfs_02_0116__en-us_topic_0000001310871229_en-us_topic_0000001311039645_request_condition>` object | The conditions for a statement to take effect.                    |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+

.. _sfs_02_0116__en-us_topic_0000001310871229_en-us_topic_0000001311039645_request_condition:

.. table:: **Table 5** Condition

   +-------------+-----------+------------------+----------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type             | Description                                                                            |
   +=============+===========+==================+========================================================================================+
   | SourceVpc   | Yes       | String           | A specified VPC ID.                                                                    |
   +-------------+-----------+------------------+----------------------------------------------------------------------------------------+
   | VpcSourceIp | No        | Array of strings | A specified IP address or IP address range. This parameter is currently not supported. |
   +-------------+-----------+------------------+----------------------------------------------------------------------------------------+

Response Parameters
-------------------

This response uses common headers. For details, see :ref:`Table 1 <sfs_02_0106__en-us_topic_0000001263068826_d0e686>`.

Example Request
---------------

Configuring a file system ACL (granting the read/write permissions for IP addresses **127.0.0.1/24** and **192.168.1.85/24** in VPC **241dbf6b-dc5d-41b2-9108-ca5e56b48386**):

.. code-block:: text

   PUT /?sfsacl HTTP/1.1
   Host: examplefilesystem.sfs3.example.region.com
   Date: WED, 01 Jul 2015 02:32:25 GMT
   Authorization: OBS H4IPJX0TQTHTHEBQQCEC:jZiAT8Vx4azWEvPRMWi0X5BpJMA=

   {
       "Statement": [{
           "Sid": "Stmt1375240018061",
           "Action": "FullControl",
           "Effect": "Allow",
           "Condition": {
               "SourceVpc": "241dbf6b-dc5d-41b2-9108-ca5e56b48386",
               "VpcSourceIp": ["127.0.0.1/24", "192.168.1.85/24"]
           }
       }]
   }

Example Response
----------------

.. code-block::

   HTTP/1.1 204 OK
   Server: OBS
   X-Obs-Request-Id: 0000018893B8073AC04721AA7EE3408B
   X-Obs-Id-2: 32AAAQAAEAABSAAgAAEAABAAAQAAEAABCS5QDe0QLbFNz6FXoKuXHzD2wS0eJQaj
   Date: Wed, 07 Jun 2023 02:38:11 GMT

Status Codes
------------

=========== ==================================
Status Code Description
=========== ==================================
204         The file system ACL is configured.
=========== ==================================

Error Codes
-----------

See :ref:`General Purpose File System Error Codes <sfs_02_0119>`.
