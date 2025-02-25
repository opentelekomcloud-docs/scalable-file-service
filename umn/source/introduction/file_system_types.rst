:original_name: sfs_01_0005.html

.. _sfs_01_0005:

File System Types
=================

SFS provides three types of file systems: SFS Capacity-Oriented, SFS Turbo, and General Purpose File System.

The following table describes the features, advantages, and application scenarios of these file system types.

SFS Capacity-Oriented
---------------------

.. table:: **Table 1** SFS Capacity-Oriented file systems

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                |
   +===================================+============================================================================================================================================================================================================+
   | Max. bandwidth                    | 10 GB/s                                                                                                                                                                                                    |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Max. IOPS                         | 10,000                                                                                                                                                                                                     |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Latency                           | Latency ranges:                                                                                                                                                                                            |
   |                                   |                                                                                                                                                                                                            |
   |                                   | -  For sequential large I/Os of large files, the latency ranges from 20 ms to 50 ms.                                                                                                                       |
   |                                   | -  For sequential small I/Os of large files, the latency ranges from 10 ms to 20 ms.                                                                                                                       |
   |                                   | -  For random small I/Os of large files, the latency ranges from 200 ms to 500 ms.                                                                                                                         |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Max. capacity                     | 2 PB                                                                                                                                                                                                       |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Highlights                        | Large capacity, high bandwidth, and low cost                                                                                                                                                               |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Application Scenarios             | Cost-sensitive workloads which require large-capacity scalability, such as media processing, file sharing, HPC, and data backup. For workloads dealing with massive small files, SFS Turbo is recommended. |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

General Purpose File System (BETA)
----------------------------------

.. _sfs_01_0005__table1763981963410:

.. table:: **Table 2** General purpose file systems

   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Description                                                                                                                                                                                                                       |
   +=======================+===================================================================================================================================================================================================================================+
   | Max. bandwidth        | 5 GB/s                                                                                                                                                                                                                            |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Latency               | 10 ms                                                                                                                                                                                                                             |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Max. capacity         | 4 PB                                                                                                                                                                                                                              |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Highlights            | Large capacity, high bandwidth, and low cost                                                                                                                                                                                      |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Application Scenarios | Cost-sensitive workloads which require large-capacity scalability, such as media processing, file sharing, high-performance computing, and data backup. For workloads dealing with massive small files, SFS Turbo is recommended. |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   -  Latency refers to the minimum latency under low workload conditions. It is unstable.
   -  Large files refer to files larger than 10 MB, and large I/Os refer to I/Os larger than 1 MB.

SFS Turbo
---------

.. table:: **Table 3** SFS Turbo file systems

   +----------------------------+--------------------------------------------------------------+--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | **Parameter**              | **20 MB/s/TiB**                                              | **40 MB/s/TiB**                                              | **125 MB/s/TiB**                                                                                      | **250 MB/s/TiB**                                                                                      |
   +----------------------------+--------------------------------------------------------------+--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Max. bandwidth             | 8 GB/s                                                       | 8 GB/s                                                       | 20 GB/s                                                                                               | 20 GB/s                                                                                               |
   +----------------------------+--------------------------------------------------------------+--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Max. IOPS                  | 250,000                                                      | 250,000                                                      | 1 million                                                                                             | 1 million                                                                                             |
   +----------------------------+--------------------------------------------------------------+--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Single-queue, 4 KB latency | 2-5 ms                                                       | 2-5 ms                                                       | 1-3 ms                                                                                                | 1-3 ms                                                                                                |
   +----------------------------+--------------------------------------------------------------+--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Capacity                   | 3.6 TB to 1 PB                                               | 1.2 TB to 1 PB                                               | 1.2 TB to 1 PB                                                                                        | 1.2 TB to 1 PB                                                                                        |
   +----------------------------+--------------------------------------------------------------+--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | IOPS calculation formula   | IOPS = Min. (250,000, 600 x Capacity)                        | IOPS = Min. (250,000, 1,200 x Capacity)                      | IOPS = Min. (1,000,000, 6,000 x Capacity)                                                             | IOPS = Min. (1,000,000, 12,500 x Capacity)                                                            |
   |                            |                                                              |                                                              |                                                                                                       |                                                                                                       |
   |                            | Capacity unit: TB                                            | Capacity unit: TB                                            | Capacity unit: TB                                                                                     | Capacity unit: TB                                                                                     |
   +----------------------------+--------------------------------------------------------------+--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Highlights                 | Large capacity and low cost                                  | Large capacity and low cost                                  | Low latency and cost effectiveness                                                                    | Low latency and cost effectiveness                                                                    |
   +----------------------------+--------------------------------------------------------------+--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Typical scenarios          | Log storage, file sharing, content management, and websites. | Log storage, file sharing, content management, and websites. | AI training, autonomous driving, EDA simulation, rendering, enterprise NAS, and HPC web applications. | AI training, autonomous driving, EDA simulation, rendering, enterprise NAS, and HPC web applications. |
   +----------------------------+--------------------------------------------------------------+--------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** Previous-generation SFS Turbo file systems

   +----------------------------+-------------------------------------------------------------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | **Parameter**              | **Standard**                                                | **Standard-Enhanced**                                       | **Performance**                                                                                  | **Performance-Enhanced**                                                                         |
   +----------------------------+-------------------------------------------------------------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | Max. bandwidth             | 120 MB/s                                                    | 1 GB/s                                                      | 320 MB/s                                                                                         | 2 GB/s                                                                                           |
   +----------------------------+-------------------------------------------------------------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | Max. IOPS                  | 3,000                                                       | 15,000                                                      | 20,000                                                                                           | 100,000                                                                                          |
   +----------------------------+-------------------------------------------------------------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | Single-queue, 4 KB latency | 2-5 ms                                                      | 2-5 ms                                                      | 1-3 ms                                                                                           | 1-3 ms                                                                                           |
   +----------------------------+-------------------------------------------------------------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | Capacity                   | 500 GB to 32 TB                                             | 10 TB to 320 TB                                             | 500 GB to 32 TB                                                                                  | 10 TB to 320 TB                                                                                  |
   +----------------------------+-------------------------------------------------------------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | Highlights                 | Low latency and tenant exclusive                            | Low latency, high bandwidth, and tenant exclusive           | Low latency, high IOPS, and tenant exclusive                                                     | Low latency, high IOPS, high bandwidth, and tenant exclusive                                     |
   +----------------------------+-------------------------------------------------------------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | Typical scenarios          | Code storage, file sharing, enterprise OA, and log storage. | Code storage, file sharing, enterprise OA, and log storage. | HPC websites, file sharing, content management, image rendering, AI training, and enterprise OA. | HPC websites, file sharing, content management, image rendering, AI training, and enterprise OA. |
   +----------------------------+-------------------------------------------------------------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+

.. note::

   -  In the table, the maximum IOPS and maximum bandwidth all include both the read and write operations. So, maximum IOPS = read IOPS + write IOPS.
   -  The minimum expansion increment of SFS Turbo Standard, Standard-Enhanced, Performance, and Performance-Enhanced file systems is 100 GB. The expansion increment of 20 MB/s/TiB, 40 MB/s/TiB, 125 MB/s/TiB, and 250 MB/s/TiB file systems is 1.2 TB.
   -  Maximum performance can be reached with multiple ECSs in parallel which have recommended configuration c4.4xlarge.4.
