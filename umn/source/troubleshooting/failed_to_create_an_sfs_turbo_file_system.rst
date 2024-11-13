:original_name: sfs_01_0118.html

.. _sfs_01_0118:

Failed to Create an SFS Turbo File System
=========================================

Symptom
-------

An SFS Turbo file system fails to be created.

Fault Diagnosis
---------------

The following fault causes are sequenced based on their occurrence probability.

If the fault persists after you have ruled out one cause, move on to the next one in the list.


.. figure:: /_static/images/en-us_image_0000002053408725.png
   :alt: **Figure 1** Fault diagnosis

   **Figure 1** Fault diagnosis

.. table:: **Table 1** Fault diagnosis

   +---------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | Possible Cause                                    | Solution                                                                                                               |
   +===================================================+========================================================================================================================+
   | The quota is insufficient.                        | The number of created file systems has reached the upper limit. to increase the quota.                                 |
   +---------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | The subnet does not have sufficient IP addresses. | If the IP addresses in the subnet are insufficient, change the subnet or release IP addresses in the subnet.           |
   +---------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | The background resources are insufficient.        | Background resources, such as compute and storage resources, have reached the upper limit. for technical consultation. |
   +---------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
