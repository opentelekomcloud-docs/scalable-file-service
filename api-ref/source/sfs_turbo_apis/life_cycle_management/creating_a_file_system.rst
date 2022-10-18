:original_name: sfs_02_0051.html

.. _sfs_02_0051:

Creating a File System
======================

Function
--------

This API is used to create an SFS Turbo file system.

URI
---

-  URI format

   POST /v1/{project_id}/sfs-turbo/shares

-  Parameter description

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                              |
   +============+===========+========+==========================================================================================================================+
   | project_id | Yes       | String | Specifies the project ID. For details about how to obtain the project ID, see :ref:`API Usage Guidelines <sfs_02_0001>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                         |
   +===========+===========+========+=====================================================================================================================================================================+
   | share     | Yes       | Object | Specifies information about an SFS Turbo file system. For details about the parameters, see the :ref:`description of the share field <sfs_02_0051__table41176360>`. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Description of the **share** field

   .. _sfs_02_0051__table41176360:

   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                                                                                                                               |
   +===================+=================+=================+===========================================================================================================================================================================================================================================================================+
   | name              | Yes             | String          | Specifies the name of an SFS Turbo file system. The value contains 4 to 64 characters and must start with a letter. This value can contain letters (case insensitive), digits, hyphens (-), and underscores (_), and cannot contain other special characters.             |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_proto       | Yes             | String          | Specifies the protocol for sharing file systems. The valid value is **NFS**. Network File System (NFS) is a distributed file system protocol that allows different computers and operating systems to share data over a network.                                          |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_type        | Yes             | String          | Specifies the file system type. The valid values are **STANDARD** and **PERFORMANCE**                                                                                                                                                                                     |
   |                   |                 |                 |                                                                                                                                                                                                                                                                           |
   |                   |                 |                 | **STANDARD**: Standard file system, corresponding to the media of SAS disks.                                                                                                                                                                                              |
   |                   |                 |                 |                                                                                                                                                                                                                                                                           |
   |                   |                 |                 | **PERFORMANCE**: Performance file system, corresponding to the media of SSD disks.                                                                                                                                                                                        |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size              | Yes             | Int             | For a common file system, the value of capacity ranges from 500 to 32768 (in the unit of GB).                                                                                                                                                                             |
   |                   |                 |                 |                                                                                                                                                                                                                                                                           |
   |                   |                 |                 | For an enhanced file system where the **expand_type** field is specified for **metadata**, the capacity ranges from 10240 to 327680. For details about metadata, see :ref:`Description of the metadata field <sfs_02_0051__table546286>`.                                 |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone | Yes             | String          | Specifies the code of the AZ where the file system is located. For details about the code, see **Regions and Endpoints**.                                                                                                                                                 |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id            | Yes             | String          | Specifies the VPC ID of a tenant in a region. You can obtain the VPC ID from the console or by following the instructions provided in "Querying VPCs" in *Virtual Private Cloud API Reference*.                                                                           |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id         | Yes             | String          | Specifies the network ID of the subnet of a tenant in a VPC. You can obtain the network ID from the VPC console or by following the instructions provided in "Querying Subnets" in *Virtual Private Cloud API Reference*.                                                 |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id | Yes             | String          | Specifies the security group ID of a tenant in a region. You can obtain the security group ID from the console or by following the instructions provided in "Querying Security Groups" in *Virtual Private Cloud API Reference*.                                          |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | backup_id         | No              | String          | Specifies the backup ID. This parameter is mandatory when you create a file system from a backup. This is not supported by the current version.                                                                                                                           |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description       | No              | String          | Specifies the file system description. The length is 0-255 characters. This is not supported by the current version.                                                                                                                                                      |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata          | No              | Object          | Specifies the metadata information used to create the file system. The value consists of one or more key and value pairs organized as a dictionary of strings. For details about the parameters, see the :ref:`description of field metadata <sfs_02_0051__table546286>`. |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Description of the **metadata** field

   .. _sfs_02_0051__table546286:

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                                                                                                                           |
   +==============+===========+========+=======================================================================================================================================================================================================================================================================================+
   | expand_type  | No        | String | Specifies the extension type. The current valid value is **bandwidth**, indicating that an enhanced file system is created. For details about the differences between different types of SFS Turbo file systems, see "Recommended Configurations".                                    |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | crypt_key_id | No        | String | Specifies the ID of a KMS professional key when an encrypted file system is created. The key ID can be obtained from the console of Data Encryption Workshop (DEW) or by referring to section "Querying the Information About a CMK" in the *Data Encryption Workshop API Reference*. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   -  The regions mentioned above are the same region. Currently, cross-region configuration is not supported.
   -  SFS Turbo will create two private IP addresses and one virtual IP address under the subnet you specified.
   -  To ensure normal use, SFS Turbo will enable the inbound rules for ports **111**, **445**, **2049**, **2051**, **2052**, and **20048** in the security group you specified.
   -  An ECS cannot access file systems on VPCs other than the one where the ECS resides. Make sure that you enter the ID of the VPC when creating a file system to be the VPC where the ECS resides for mounting the file system.

-  Example request

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
          "security_group_id": "8c4ebbd0-6edf-4aae-8353-81ce6d06e1f4",
          "metadata": {
            "crypt_key_id": "015bf4b8-73cc-4235-8595-46931de7dfd0"
          }
        }
      }

Response
--------

-  Parameter description

   +-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                             |
   +===========+========+=========================================================================================================================+
   | id        | String | Specifies the ID of an SFS Turbo file system.                                                                           |
   +-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | name      | String | Specifies the name of an SFS Turbo file system.                                                                         |
   +-----------+--------+-------------------------------------------------------------------------------------------------------------------------+
   | status    | String | Specifies the status of an SFS Turbo file system. For details, see :ref:`SFS Turbo File System Statuses <sfs_02_0085>`. |
   +-----------+--------+-------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "id": "708c017c-54b5-429a-a098-7692e23fa518",
          "name": "sfs-turbo-test",
          "status": "100"
      }

Status Codes
------------

-  Normal

202

-  Abnormal

For details, see :ref:`Status Codes <sfs_02_0089>`.
