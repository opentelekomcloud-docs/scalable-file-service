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

If the fault persists after you have ruled out a cause, check other causes.


.. figure:: /_static/images/en-us_image_0000001515917312.png
   :alt: **Figure 1** Fault diagnosis

   **Figure 1** Fault diagnosis

.. table:: **Table 1** Fault diagnosis

   +---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Possible Cause                                    | Solution                                                                                                            |
   +===================================================+=====================================================================================================================+
   | The quota is insufficient.                        | The number of created file systems has reached the upper limit. to increase the quota.                              |
   +---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | The subnet does not have sufficient IP addresses. | If the subnet IP addresses are insufficient, you can change the subnet or release other IP addresses in the subnet. |
   +---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | The background capacity is insufficient.          | to expand the capacity.                                                                                             |
   +---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
