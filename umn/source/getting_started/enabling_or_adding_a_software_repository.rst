:original_name: sfs_01_0027.html

.. _sfs_01_0027:

Enabling or Adding a Software Repository
========================================

This section explains how to enable or add a software repository in CentOS, SUSE, and Ubuntu.

CentOS
------

#. Run the following command to check whether a software repository has been enabled.

   **yum repolist all**

   If **status** is **disabled**, as shown in :ref:`Figure 1 <sfs_01_0027__fig50710110103819>`, no software repository has been enabled. Proceed to the next step.

   .. _sfs_01_0027__fig50710110103819:

   .. figure:: /_static/images/en-us_image_0000001516076948.png
      :alt: **Figure 1** Checking software repositories

      **Figure 1** Checking software repositories

#. Run the following command to enable a software repository. This step uses **Public-OTC-CentOS-7-Base** as an example.

   **yum-config-manager --enable Public-OTC-CentOS-7-Base**


   .. figure:: /_static/images/en-us_image_0000001516076956.png
      :alt: **Figure 2** Enabling a software repository

      **Figure 2** Enabling a software repository

#. Run the following command to check whether the software repository described in step 2 has been enabled.

   **yum repolist all**

   If **status** is **enabled**, as shown in :ref:`Figure 3 <sfs_01_0027__fig33842796104733>`, the software repository has been enabled.

   .. _sfs_01_0027__fig33842796104733:

   .. figure:: /_static/images/en-us_image_0000001567316449.png
      :alt: **Figure 3** Checking whether the software repository has been enabled

      **Figure 3** Checking whether the software repository has been enabled

SUSE
----

#. Run the following command to check whether a software repository has been enabled.

   **zypper lr**

   If no software repository is detected, as shown in :ref:`Figure 4 <sfs_01_0027__en-us_topic_0077171435_en-us_topic_0077171435_fig50710110103819>`, proceed to the next step.

   .. _sfs_01_0027__en-us_topic_0077171435_en-us_topic_0077171435_fig50710110103819:

   .. figure:: /_static/images/en-us_image_0000001567076789.png
      :alt: **Figure 4** Checking software repositories

      **Figure 4** Checking software repositories

#. Run the following command to add a software repository. This step uses **opensuse12.2** as an example.

   **zypper addrepo http://download.opensuse.org/distribution/12.2/repo/oss/ opensuse-main**


   .. figure:: /_static/images/en-us_image_0000001516076952.png
      :alt: **Figure 5** Adding a software repository

      **Figure 5** Adding a software repository

#. Run the following command to update and add software repositories.

   **zypper refresh**


   .. figure:: /_static/images/en-us_image_0000001567076793.png
      :alt: **Figure 6** Updating and adding repositories

      **Figure 6** Updating and adding repositories

#. Run the following command to check whether the software repository described in step 2 has been enabled.

   **zypper lr**

   If **Enabled** is **Yes**, as shown in :ref:`Figure 7 <sfs_01_0027__en-us_topic_0077171435_en-us_topic_0077171435_fig33842796104733>`, the software repository has been enabled.

   .. _sfs_01_0027__en-us_topic_0077171435_en-us_topic_0077171435_fig33842796104733:

   .. figure:: /_static/images/en-us_image_0000001567396709.png
      :alt: **Figure 7** Checking whether the software repository has been enabled

      **Figure 7** Checking whether the software repository has been enabled

Ubuntu
------

#. Run the following command to add a software repository.

   **apt-add-repository http://archive.canonical.com/ubuntu**


   .. figure:: /_static/images/en-us_image_0000001567316453.png
      :alt: **Figure 8** Adding a software repository

      **Figure 8** Adding a software repository

#. Run the following command to update and add software repositories.

   **apt-get update**


   .. figure:: /_static/images/en-us_image_0000001515917372.png
      :alt: **Figure 9** Updating and adding repositories

      **Figure 9** Updating and adding repositories
