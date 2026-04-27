:original_name: sfs_02_0191.html

.. _sfs_02_0191:

Obtaining a KMS Key ID
======================

Scenarios
---------

When creating an encrypted file system, you need to add the KMS key ID to the request header. You can obtain the key ID in the following ways:

-  :ref:`Querying the ID of a KMS Key Using an API <sfs_02_0191__section11713201013562>`
-  :ref:`Creating a KMS Key and Obtaining Its ID Using an API <sfs_02_0191__section271871075611>`
-  :ref:`Querying the ID of a KMS Key on the Console <sfs_02_0191__section672081015563>`
-  :ref:`Creating a KMS Key and Obtaining Its ID on the Console <sfs_02_0191__section1672220107566>`

.. _sfs_02_0191__section11713201013562:

Querying the ID of a KMS Key Using an API
-----------------------------------------

You can call the `Querying the List of CMKs <https://docs.otc.t-systems.com/key-management-service/api-ref/apis/key_management_service/cmk_management/querying_the_list_of_cmks.html>`__ API of KMS to obtain the key ID.

The API used to obtain a key ID is POST https://{Endpoint}/v1.0/{project_id}/kms/list-keys. {Endpoint} is the IAM endpoint, and you can obtain it from `Regions and Endpoints <https://docs.otc.t-systems.com/regions-and-endpoints/index.html>`__. You can obtain {project_id} by referring to :ref:`Obtaining a Project ID <sfs_02_0090>`.

The following shows an example request and response. For details about the parameters, see `Querying the List of CMKs <https://docs.otc.t-systems.com/key-management-service/api-ref/apis/key_management_service/cmk_management/querying_the_list_of_cmks.html>`__.

**Example request:**

.. code-block::

   {
        "limit": "2",
        "marker": "1"
   }

**Example response**: **key_id** indicates the key ID.

.. code-block::

   {
     "keys" : [ "0d0466b0-e727-4d9c-b35d-f84bb474a37f"],
     "key_details" : [ {
       "key_id" : "0d0466b0-e727-4d9c-b35d-f84bb474a37f",
       "domain_id" : "00074811d5c27c4f8d48bb91e4a1dcfd",
       "key_alias" : "test",
       "realm" : "aaa",
       "key_description" : "key_description",
       "creation_date" : "1502799822000",
       "scheduled_deletion_date" : "",
       "key_spec" : "AES_256",
       "key_usage" : "ENCRYPT_DECRYPT",
       "key_state" : "2",
       "default_key_flag" : "0",
       "key_type" : "1",
       "expiration_time" : "1501578672000",
       "origin" : "kms",
       "key_rotation_enabled" : "true",
       "sys_enterprise_project_id" : "0",
       "partition_type" : "1"
   }
     ],
     "next_marker" : "",
     "truncated" : "false",
     "total" : 1
   }

.. _sfs_02_0191__section271871075611:

Creating a KMS Key and Obtaining Its ID Using an API
----------------------------------------------------

If no key is found, you can call the `Creating a CMK <https://docs.otc.t-systems.com/key-management-service/api-ref/apis/key_management_service/cmk_management/creating_a_cmk.html>`__ API of KMS to create one.

The API used to create a key is POST https://{Endpoint}/v1.0/{project_id}/kms/create-key. {Endpoint} is the IAM endpoint, and you can obtain it from `Regions and Endpoints <https://docs.otc.t-systems.com/regions-and-endpoints/index.html>`__. You can obtain {project_id} by referring to :ref:`Obtaining a Project ID <sfs_02_0090>`.

The following shows an example request and response. For details about the parameters, see `Creating a CMK <https://docs.otc.t-systems.com/key-management-service/api-ref/apis/key_management_service/cmk_management/creating_a_cmk.html>`__.

**Example request:**

.. code-block::

   {
        "key_alias": "test"
   }

**Example response**: **key_id** indicates the key ID.

.. code-block::

   {
     "key_info" : {
       "key_id" : "bb6a3d22-dc93-47ac-b5bd-88df7ad35f1e",
       "domain_id" : "b168fe00ff56492495a7d22974df2d0b"
     }
   }

.. _sfs_02_0191__section672081015563:

Querying the ID of a KMS Key on the Console
-------------------------------------------

#. Log in to the KMS console and choose **Key Management Service**.

#. Select the desired region in the upper left corner.

#. On the **Custom Keys** tab, copy the ID of the desired key.


   .. figure:: /_static/images/en-us_image_0000002542835887.png
      :alt: **Figure 1** Copying the key ID

      **Figure 1** Copying the key ID

.. _sfs_02_0191__section1672220107566:

Creating a KMS Key and Obtaining Its ID on the Console
------------------------------------------------------

#. Log in to the KMS console and choose **Key Management Service**.

2. Select the desired region in the upper left corner.

3. Click **Create Key** in the upper right corner. On the displayed page, set the parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002511210156.png
      :alt: **Figure 2** Creating a key

      **Figure 2** Creating a key

4. On the **Custom Keys** tab, copy the ID of the desired key.


   .. figure:: /_static/images/en-us_image_0000002511370156.png
      :alt: **Figure 3** Copying the key ID

      **Figure 3** Copying the key ID
