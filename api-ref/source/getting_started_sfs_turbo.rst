:original_name: sfs_02_0015.html

.. _sfs_02_0015:

Getting Started (SFS Turbo)
===========================

This section describes how to use APIs by calling an API to create an SFS Turbo file system.

.. note::

   The token obtained from IAM is valid for only 24 hours. If you want to use one token for authentication, you can cache it to avoid frequently calling.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the API when making a call. The following APIs are involved in the request for creating an SFS Turbo file system:

-  API for obtaining tokens from IAM
-  API for creating SFS Turbo file systems.

Procedure
---------

#. Obtain the token by following instructions in :ref:`Authentication <sfs_02_0011>`.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. code-block::

      {
        "share": {
          "name": "sfs-turbo-test",
          "share_proto": "NFS",
          "share_type": "STANDARD",
          "size": 100,
          "availability_zone": "az1",
          "vpc_id": "d651ea2b-2b20-4c6d-8bbf-2adcec18dac9",
          "subnet_id": "b8884abe-f47b-4917-9f6c-f64825c365db",
          "security_group_id": "8c4ebbd0-6edf-4aae-8353-81ce6d06e1f4"
        }
      }

#. Send the request **POST https://Endpoint of SFS Turbo/v1/{project_id}/sfs-turbo/shares**.

#. After the request is successfully responded, the ID and name of the SFS Turbo file system are returned.

   If the request fails, an error code and error information are returned. For details about the error codes, see the abnormal return values of the corresponding API.

   Query SFS Turbo file system details based on the returned file system ID.

   If the returned status of the file system is **200**, the SFS Turbo file system is successfully created. For details about the return values of request exceptions, see the abnormal return values of the corresponding API. For other statuses, see :ref:`SFS Turbo File System Statuses <sfs_02_0085>`.

   You can query and delete an SFS Turbo file system based on the file system ID.

Configuration Example
---------------------

If the token has been obtained, you can run the following **curl** command to create an SFS Turbo file system:

.. code-block::

   curl -k -i -X POST -H "X-Auth-Token: token_value" -H "Content-Type: application/json" -d '{"share": {"name": "sfs-turbo-test", "share_proto": "NFS", "share_type": "STANDARD", "size": 100, "availability_zone": "az1", "vpc_id": "d651ea2b-2b20-4c6d-8bbf-2adcec18dac9", "subnet_id": "b8884abe-f47b-4917-9f6c-f64825c365db", "security_group_id": "8c4ebbd0-6edf-4aae-8353-81ce6d06e1f4"}}' "https://127.0.0.1:8979/v1/xxxbxbex5cfx41f0a08ay915fd79240d/sfs-turbo/shares"
