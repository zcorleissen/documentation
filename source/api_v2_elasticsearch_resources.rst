Elasticsearch Resources
=======================

Check state of instances provided
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /elasticsearch/check_states/

.. note::

   The **instance_list** is a list of instance ID's (these can be found from the **/v2/instances/** route), and the **states** field must be one of the following: COMPLETED, ACTIVE, RESIZE, or ERROR.

Request:

.. code-block:: bash

   {
       "instance_list": [
           "55e0a924cb143c426df6927e",
           "55e631a9ffbbf85bdfa35086"
       ],
       "states": [
           "ACTIVE"
       ]
   }

Response:

.. code-block:: bash

   {
       "data": [
           false,
           true
       ]
   }

Get details on the specified Elasticsearch instance's cluster
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/<instance_name>/cluster/

Response:

.. code-block:: bash

   {
       "data": {
           "cluster_name": "17fa73756374a77594d094d34d4e87e0",
           "indices": {
               "completion": {
                   "size_in_bytes": 0
               },
               "count": 0,
               "docs": {
                   "count": 0,
                   "deleted": 0
               },
               "fielddata": {
                   "evictions": 0,
                   "memory_size_in_bytes": 0
               },
               "filter_cache": {
                   "evictions": 0,
                   "memory_size_in_bytes": 0
               },
               "id_cache": {
                   "memory_size_in_bytes": 0
               },
               "percolate": {
                   "current": 0,
                   "memory_size": "-1b",
                   "memory_size_in_bytes": -1,
                   "queries": 0,
                   "time_in_millis": 0,
                   "total": 0
               },
               "segments": {
                   "count": 0,
                   "fixed_bit_set_memory_in_bytes": 0,
                   "index_writer_max_memory_in_bytes": 0,
                   "index_writer_memory_in_bytes": 0,
                   "memory_in_bytes": 0,
                   "version_map_memory_in_bytes": 0
               },
               "shards": {},
               "store": {
                   "size_in_bytes": 0,
                   "throttle_time_in_millis": 0
               }
           },
           "nodes": {
               "count": {
                   "client": 0,
                   "data_only": 4,
                   "master_data": 0,
                   "master_only": 3,
                   "total": 11
               },
               "fs": {
                   "available_in_bytes": 19097329664,
                   "free_in_bytes": 19097329664,
                   "total_in_bytes": 21071462400
               },
               "jvm": {
                   "max_uptime_in_millis": 949375008,
                   "mem": {
                       "heap_max_in_bytes": 6302597120,
                       "heap_used_in_bytes": 954506776
                   },
                   "threads": 341,
                   "versions": [
                       {
                           "count": 11,
                           "version": "1.8.0_40",
                           "vm_name": "Java HotSpot(TM) 64-Bit Server VM",
                           "vm_vendor": "Oracle Corporation",
                           "vm_version": "25.40-b25"
                       }
                   ]
               },
               "os": {
                   "available_processors": 22,
                   "cpu": [
                       {
                           "cache_size_in_bytes": 20480,
                           "cores_per_socket": 16,
                           "count": 11,
                           "mhz": 3201,
                           "model": "Xeon",
                           "total_cores": 32,
                           "total_sockets": 2,
                           "vendor": "Intel"
                       }
                   ],
                   "mem": {
                       "total_in_bytes": 12884901888
                   }
               },
               "plugins": [
                   {
                       "description": "No description found.",
                       "jvm": false,
                       "name": "head",
                       "site": true,
                       "url": "/_plugin/head/",
                       "version": "NA"
                   },
                   {
                       "description": "No description found.",
                       "jvm": false,
                       "name": "HQ",
                       "site": true,
                       "url": "/_plugin/HQ/",
                       "version": "NA"
                   }
               ],
               "process": {
                   "cpu": {
                       "percent": 0
                   },
                   "open_file_descriptors": {
                       "avg": 381,
                       "max": 393,
                       "min": 376
                   }
               },
               "versions": [
                   "1.6.2"
               ]
           },
           "status": "green",
           "timestamp": 1441736158992
       }
   }

Get details on the specified Elasticsearch instance's data nodes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/<instance_name>/data_nodes/

Response:

.. code-block:: bash

   {
       "data": {
           "active": [
               {
                   "attributes": {
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esdn0"
                   },
                   "fs": {
                       "data": [
                           {
                               "available": "1.9gb",
                               "available_in_bytes": 2043478016,
                               "dev": "/dev/simfs",
                               "free": "1.9gb",
                               "free_in_bytes": 2043478016,
                               "mount": "/data0",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total": "1.9gb",
                               "total_in_bytes": 2046640128,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736278633,
                       "total": {
                           "available": "1.9gb",
                           "available_in_bytes": 2043478016,
                           "free": "1.9gb",
                           "free_in_bytes": 2043478016,
                           "total": "1.9gb",
                           "total_in_bytes": 2046640128
                       }
                   },
                   "host": "iad1esdn0vz16",
                   "id": "w66J0I4ITOWufukPBbXCZQ",
                   "ip": [
                       "inet[/10.56.145.94:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 20,
                               "total_capacity": "4.7mb",
                               "total_capacity_in_bytes": 4980736,
                               "used": "4.7mb",
                               "used_in_bytes": 4980736
                           },
                           "mapped": {
                               "count": 0,
                               "total_capacity": "0b",
                               "total_capacity_in_bytes": 0,
                               "used": "0b",
                               "used_in_bytes": 0
                           }
                       },
                       "gc": {
                           "collectors": {
                               "old": {
                                   "collection_count": 1,
                                   "collection_time": "11ms",
                                   "collection_time_in_millis": 11
                               },
                               "young": {
                                   "collection_count": 4,
                                   "collection_time": "51ms",
                                   "collection_time_in_millis": 51
                               }
                           }
                       },
                       "mem": {
                           "heap_committed": "123.7mb",
                           "heap_committed_in_bytes": 129761280,
                           "heap_max": "123.7mb",
                           "heap_max_in_bytes": 129761280,
                           "heap_used": "29.2mb",
                           "heap_used_in_bytes": 30638976,
                           "heap_used_percent": 23,
                           "non_heap_committed": "41.5mb",
                           "non_heap_committed_in_bytes": 43589632,
                           "non_heap_used": "40.7mb",
                           "non_heap_used_in_bytes": 42719936,
                           "pools": {
                               "old": {
                                   "max": "85.3mb",
                                   "max_in_bytes": 89522176,
                                   "peak_max": "85.3mb",
                                   "peak_max_in_bytes": 89522176,
                                   "peak_used": "14.9mb",
                                   "peak_used_in_bytes": 15662224,
                                   "used": "10.4mb",
                                   "used_in_bytes": 10916784
                               },
                               "survivor": {
                                   "max": "4.2mb",
                                   "max_in_bytes": 4456448,
                                   "peak_max": "4.2mb",
                                   "peak_max_in_bytes": 4456448,
                                   "peak_used": "4.2mb",
                                   "peak_used_in_bytes": 4456448,
                                   "used": "4.2mb",
                                   "used_in_bytes": 4456448
                               },
                               "young": {
                                   "max": "34.1mb",
                                   "max_in_bytes": 35782656,
                                   "peak_max": "34.1mb",
                                   "peak_max_in_bytes": 35782656,
                                   "peak_used": "34.1mb",
                                   "peak_used_in_bytes": 35782656,
                                   "used": "14.5mb",
                                   "used_in_bytes": 15265744
                               }
                           }
                       },
                       "threads": {
                           "count": 28,
                           "peak_count": 36
                       },
                       "timestamp": 1441736278633,
                       "uptime": "10.7m",
                       "uptime_in_millis": 647380
                   },
                   "name": "iad1esdn0vz16",
                   "os": {
                       "cpu": {
                           "idle": 99,
                           "stolen": 0,
                           "sys": 0,
                           "usage": 0,
                           "user": 0
                       },
                       "load_average": [
                           0.02,
                           0.02,
                           0.0
                       ],
                       "mem": {
                           "actual_free": "19.1mb",
                           "actual_free_in_bytes": 20115456,
                           "actual_used": "236.8mb",
                           "actual_used_in_bytes": 248320000,
                           "free": "17.5mb",
                           "free_in_bytes": 18411520,
                           "free_percent": 7,
                           "used": "238.4mb",
                           "used_in_bytes": 250023936,
                           "used_percent": 92
                       },
                       "swap": {
                           "free": "1013.5mb",
                           "free_in_bytes": 1062739968,
                           "used": "10.4mb",
                           "used_in_bytes": 11001856
                       },
                       "timestamp": 1441736278633,
                       "uptime": "661ms",
                       "uptime_in_millis": 661
                   },
                   "timestamp": 1441736278632,
                   "transport_address": "inet[/10.56.145.94:30121]"
               },
               {
                   "attributes": {
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esdn7"
                   },
                   "fs": {
                       "data": [
                           {
                               "available": "1.9gb",
                               "available_in_bytes": 2043478016,
                               "dev": "/dev/simfs",
                               "free": "1.9gb",
                               "free_in_bytes": 2043478016,
                               "mount": "/data0",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total": "1.9gb",
                               "total_in_bytes": 2046640128,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736278618,
                       "total": {
                           "available": "1.9gb",
                           "available_in_bytes": 2043478016,
                           "free": "1.9gb",
                           "free_in_bytes": 2043478016,
                           "total": "1.9gb",
                           "total_in_bytes": 2046640128
                       }
                   },
                   "host": "iad1esdn7vz21",
                   "id": "nTTBnF7HRDuJb3vfMNtv8A",
                   "ip": [
                       "inet[/10.56.148.12:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 32,
                               "total_capacity": "6.7mb",
                               "total_capacity_in_bytes": 7079788,
                               "used": "6.7mb",
                               "used_in_bytes": 7079788
                           },
                           "mapped": {
                               "count": 0,
                               "total_capacity": "0b",
                               "total_capacity_in_bytes": 0,
                               "used": "0b",
                               "used_in_bytes": 0
                           }
                       },
                       "gc": {
                           "collectors": {
                               "old": {
                                   "collection_count": 1,
                                   "collection_time": "26ms",
                                   "collection_time_in_millis": 26
                               },
                               "young": {
                                   "collection_count": 207,
                                   "collection_time": "567ms",
                                   "collection_time_in_millis": 567
                               }
                           }
                       },
                       "mem": {
                           "heap_committed": "123.7mb",
                           "heap_committed_in_bytes": 129761280,
                           "heap_max": "123.7mb",
                           "heap_max_in_bytes": 129761280,
                           "heap_used": "28.7mb",
                           "heap_used_in_bytes": 30188608,
                           "heap_used_percent": 23,
                           "non_heap_committed": "44.7mb",
                           "non_heap_committed_in_bytes": 46931968,
                           "non_heap_used": "44mb",
                           "non_heap_used_in_bytes": 46148808,
                           "pools": {
                               "old": {
                                   "max": "85.3mb",
                                   "max_in_bytes": 89522176,
                                   "peak_max": "85.3mb",
                                   "peak_max_in_bytes": 89522176,
                                   "peak_used": "15.7mb",
                                   "peak_used_in_bytes": 16548872,
                                   "used": "13.5mb",
                                   "used_in_bytes": 14218368
                               },
                               "survivor": {
                                   "max": "4.2mb",
                                   "max_in_bytes": 4456448,
                                   "peak_max": "4.2mb",
                                   "peak_max_in_bytes": 4456448,
                                   "peak_used": "4.2mb",
                                   "peak_used_in_bytes": 4456448,
                                   "used": "8kb",
                                   "used_in_bytes": 8288
                               },
                               "young": {
                                   "max": "34.1mb",
                                   "max_in_bytes": 35782656,
                                   "peak_max": "34.1mb",
                                   "peak_max_in_bytes": 35782656,
                                   "peak_used": "34.1mb",
                                   "peak_used_in_bytes": 35782656,
                                   "used": "15.2mb",
                                   "used_in_bytes": 15961952
                               }
                           }
                       },
                       "threads": {
                           "count": 29,
                           "peak_count": 36
                       },
                       "timestamp": 1441736278617,
                       "uptime": "10.9d",
                       "uptime_in_millis": 949495423
                   },
                   "name": "iad1esdn7vz21",
                   "os": {
                       "cpu": {
                           "idle": 99,
                           "stolen": 0,
                           "sys": 0,
                           "usage": 0,
                           "user": 0
                       },
                       "load_average": [
                           0.0,
                           0.0,
                           0.0
                       ],
                       "mem": {
                           "actual_free": "13.4mb",
                           "actual_free_in_bytes": 14123008,
                           "actual_used": "242.5mb",
                           "actual_used_in_bytes": 254312448,
                           "free": "7.1mb",
                           "free_in_bytes": 7520256,
                           "free_percent": 5,
                           "used": "248.8mb",
                           "used_in_bytes": 260915200,
                           "used_percent": 94
                       },
                       "swap": {
                           "free": "990.4mb",
                           "free_in_bytes": 1038553088,
                           "used": "33.5mb",
                           "used_in_bytes": 35188736
                       },
                       "timestamp": 1441736278617,
                       "uptime": "15.8m",
                       "uptime_in_millis": 949515
                   },
                   "timestamp": 1441736278617,
                   "transport_address": "inet[/10.56.148.12:30121]"
               },
               {
                   "attributes": {
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esdn7"
                   },
                   "fs": {
                       "data": [
                           {
                               "available": "1.9gb",
                               "available_in_bytes": 2043478016,
                               "dev": "/dev/simfs",
                               "free": "1.9gb",
                               "free_in_bytes": 2043478016,
                               "mount": "/data0",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total": "1.9gb",
                               "total_in_bytes": 2046640128,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736278352,
                       "total": {
                           "available": "1.9gb",
                           "available_in_bytes": 2043478016,
                           "free": "1.9gb",
                           "free_in_bytes": 2043478016,
                           "total": "1.9gb",
                           "total_in_bytes": 2046640128
                       }
                   },
                   "host": "iad1esdn7vz22",
                   "id": "3jmRQ_-nQq-C555e_Kzn4w",
                   "ip": [
                       "inet[/10.56.148.13:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 32,
                               "total_capacity": "6.7mb",
                               "total_capacity_in_bytes": 7079788,
                               "used": "6.7mb",
                               "used_in_bytes": 7079788
                           },
                           "mapped": {
                               "count": 0,
                               "total_capacity": "0b",
                               "total_capacity_in_bytes": 0,
                               "used": "0b",
                               "used_in_bytes": 0
                           }
                       },
                       "gc": {
                           "collectors": {
                               "old": {
                                   "collection_count": 1,
                                   "collection_time": "18ms",
                                   "collection_time_in_millis": 18
                               },
                               "young": {
                                   "collection_count": 205,
                                   "collection_time": "581ms",
                                   "collection_time_in_millis": 581
                               }
                           }
                       },
                       "mem": {
                           "heap_committed": "123.7mb",
                           "heap_committed_in_bytes": 129761280,
                           "heap_max": "123.7mb",
                           "heap_max_in_bytes": 129761280,
                           "heap_used": "39.6mb",
                           "heap_used_in_bytes": 41568504,
                           "heap_used_percent": 32,
                           "non_heap_committed": "44.3mb",
                           "non_heap_committed_in_bytes": 46473216,
                           "non_heap_used": "43.6mb",
                           "non_heap_used_in_bytes": 45794136,
                           "pools": {
                               "old": {
                                   "max": "85.3mb",
                                   "max_in_bytes": 89522176,
                                   "peak_max": "85.3mb",
                                   "peak_max_in_bytes": 89522176,
                                   "peak_used": "18.2mb",
                                   "peak_used_in_bytes": 19178184,
                                   "used": "18.2mb",
                                   "used_in_bytes": 19178184
                               },
                               "survivor": {
                                   "max": "4.2mb",
                                   "max_in_bytes": 4456448,
                                   "peak_max": "4.2mb",
                                   "peak_max_in_bytes": 4456448,
                                   "peak_used": "4.2mb",
                                   "peak_used_in_bytes": 4456448,
                                   "used": "8.6kb",
                                   "used_in_bytes": 8832
                               },
                               "young": {
                                   "max": "34.1mb",
                                   "max_in_bytes": 35782656,
                                   "peak_max": "34.1mb",
                                   "peak_max_in_bytes": 35782656,
                                   "peak_used": "34.1mb",
                                   "peak_used_in_bytes": 35782656,
                                   "used": "21.3mb",
                                   "used_in_bytes": 22386096
                               }
                           }
                       },
                       "threads": {
                           "count": 29,
                           "peak_count": 36
                       },
                       "timestamp": 1441736278352,
                       "uptime": "10.9d",
                       "uptime_in_millis": 942061069
                   },
                   "name": "iad1esdn7vz22",
                   "os": {
                       "cpu": {
                           "idle": 99,
                           "stolen": 0,
                           "sys": 0,
                           "usage": 0,
                           "user": 0
                       },
                       "load_average": [
                           0.0,
                           0.0,
                           0.0
                       ],
                       "mem": {
                           "actual_free": "20.4mb",
                           "actual_free_in_bytes": 21405696,
                           "actual_used": "235.5mb",
                           "actual_used_in_bytes": 247029760,
                           "free": "13.6mb",
                           "free_in_bytes": 14352384,
                           "free_percent": 7,
                           "used": "242.3mb",
                           "used_in_bytes": 254083072,
                           "used_percent": 92
                       },
                       "swap": {
                           "free": "977.3mb",
                           "free_in_bytes": 1024839680,
                           "used": "46.6mb",
                           "used_in_bytes": 48902144
                       },
                       "timestamp": 1441736278351,
                       "uptime": "15.7m",
                       "uptime_in_millis": 942074
                   },
                   "timestamp": 1441736278351,
                   "transport_address": "inet[/10.56.148.13:30121]"
               },
               {
                   "attributes": {
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esdn4"
                   },
                   "fs": {
                       "data": [
                           {
                               "available": "1.9gb",
                               "available_in_bytes": 2043478016,
                               "dev": "/dev/simfs",
                               "free": "1.9gb",
                               "free_in_bytes": 2043478016,
                               "mount": "/data0",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total": "1.9gb",
                               "total_in_bytes": 2046640128,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736278715,
                       "total": {
                           "available": "1.9gb",
                           "available_in_bytes": 2043478016,
                           "free": "1.9gb",
                           "free_in_bytes": 2043478016,
                           "total": "1.9gb",
                           "total_in_bytes": 2046640128
                       }
                   },
                   "host": "iad1esdn4vz25",
                   "id": "hqC9t45pQ1ac1Jve3bzeiA",
                   "ip": [
                       "inet[/10.56.147.224:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 32,
                               "total_capacity": "6.7mb",
                               "total_capacity_in_bytes": 7079788,
                               "used": "6.7mb",
                               "used_in_bytes": 7079788
                           },
                           "mapped": {
                               "count": 0,
                               "total_capacity": "0b",
                               "total_capacity_in_bytes": 0,
                               "used": "0b",
                               "used_in_bytes": 0
                           }
                       },
                       "gc": {
                           "collectors": {
                               "old": {
                                   "collection_count": 1,
                                   "collection_time": "12ms",
                                   "collection_time_in_millis": 12
                               },
                               "young": {
                                   "collection_count": 207,
                                   "collection_time": "579ms",
                                   "collection_time_in_millis": 579
                               }
                           }
                       },
                       "mem": {
                           "heap_committed": "123.7mb",
                           "heap_committed_in_bytes": 129761280,
                           "heap_max": "123.7mb",
                           "heap_max_in_bytes": 129761280,
                           "heap_used": "23.3mb",
                           "heap_used_in_bytes": 24486000,
                           "heap_used_percent": 18,
                           "non_heap_committed": "44.5mb",
                           "non_heap_committed_in_bytes": 46694400,
                           "non_heap_used": "43.7mb",
                           "non_heap_used_in_bytes": 45864792,
                           "pools": {
                               "old": {
                                   "max": "85.3mb",
                                   "max_in_bytes": 89522176,
                                   "peak_max": "85.3mb",
                                   "peak_max_in_bytes": 89522176,
                                   "peak_used": "18.4mb",
                                   "peak_used_in_bytes": 19393544,
                                   "used": "18.4mb",
                                   "used_in_bytes": 19393544
                               },
                               "survivor": {
                                   "max": "4.2mb",
                                   "max_in_bytes": 4456448,
                                   "peak_max": "4.2mb",
                                   "peak_max_in_bytes": 4456448,
                                   "peak_used": "4.2mb",
                                   "peak_used_in_bytes": 4456448,
                                   "used": "131.5kb",
                                   "used_in_bytes": 134688
                               },
                               "young": {
                                   "max": "34.1mb",
                                   "max_in_bytes": 35782656,
                                   "peak_max": "34.1mb",
                                   "peak_max_in_bytes": 35782656,
                                   "peak_used": "34.1mb",
                                   "peak_used_in_bytes": 35782656,
                                   "used": "4.7mb",
                                   "used_in_bytes": 4957768
                               }
                           }
                       },
                       "threads": {
                           "count": 29,
                           "peak_count": 37
                       },
                       "timestamp": 1441736278715,
                       "uptime": "10.9d",
                       "uptime_in_millis": 949495511
                   },
                   "name": "iad1esdn4vz25",
                   "os": {
                       "cpu": {
                           "idle": 99,
                           "stolen": 0,
                           "sys": 0,
                           "usage": 0,
                           "user": 0
                       },
                       "load_average": [
                           0.0,
                           0.0,
                           0.0
                       ],
                       "mem": {
                           "actual_free": "23.2mb",
                           "actual_free_in_bytes": 24371200,
                           "actual_used": "232.7mb",
                           "actual_used_in_bytes": 244064256,
                           "free": "15.8mb",
                           "free_in_bytes": 16666624,
                           "free_percent": 9,
                           "used": "240.1mb",
                           "used_in_bytes": 251768832,
                           "used_percent": 90
                       },
                       "swap": {
                           "free": "998.2mb",
                           "free_in_bytes": 1046700032,
                           "used": "25.7mb",
                           "used_in_bytes": 27041792
                       },
                       "timestamp": 1441736278715,
                       "uptime": "15.8m",
                       "uptime_in_millis": 949515
                   },
                   "timestamp": 1441736278714,
                   "transport_address": "inet[/10.56.147.224:30121]"
               }
           ],
           "builds": []
       }
   }

Add a new data node to the specified Elasticsearch instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /elasticsearch/<instance_name>/data_nodes/

Response:

.. code-block:: bash

   {
       "data": "55ef26c2cb143c49a5773005"
   }

Get details on the specified Elasticsearch instance's indices
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/<instance_name>/indices/

Response:

.. code-block:: bash

   {
       "data": {
           "_all": {
               "primaries": {},
               "total": {}
           },
           "_shards": {
               "failed": 0,
               "successful": 0,
               "total": 0
           },
           "indices": {}
       }
   }

Get details on the specified Elasticsearch instance's nodes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/<instance_name>/nodes/

Response:

.. code-block:: bash

   {
       "data": {
           "cluster_name": "17fa73756374a77594d094d34d4e87e0",
           "nodes": {
               "-BUyNyJsR3i06mba9CDRIQ": {
                   "attributes": {
                       "data": "false",
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esapp0"
                   },
                   "breakers": {
                       "fielddata": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "604.4mb",
                           "limit_size_in_bytes": 633785548,
                           "overhead": 1.03,
                           "tripped": 0
                       },
                       "parent": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "705.1mb",
                           "limit_size_in_bytes": 739416473,
                           "overhead": 1.0,
                           "tripped": 0
                       },
                       "request": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "402.9mb",
                           "limit_size_in_bytes": 422523699,
                           "overhead": 1.0,
                           "tripped": 0
                       }
                   },
                   "fs": {
                       "data": [],
                       "timestamp": 1441736480984,
                       "total": {}
                   },
                   "host": "iad1esapp0vz114",
                   "http": {
                       "current_open": 2,
                       "total_opened": 1065
                   },
                   "indices": {
                       "completion": {
                           "size_in_bytes": 0
                       },
                       "docs": {
                           "count": 0,
                           "deleted": 0
                       },
                       "fielddata": {
                           "evictions": 0,
                           "memory_size_in_bytes": 0
                       },
                       "filter_cache": {
                           "evictions": 0,
                           "memory_size_in_bytes": 0
                       },
                       "flush": {
                           "total": 0,
                           "total_time_in_millis": 0
                       },
                       "get": {
                           "current": 0,
                           "exists_time_in_millis": 0,
                           "exists_total": 0,
                           "missing_time_in_millis": 0,
                           "missing_total": 0,
                           "time_in_millis": 0,
                           "total": 0
                       },
                       "id_cache": {
                           "memory_size_in_bytes": 0
                       },
                       "indexing": {
                           "delete_current": 0,
                           "delete_time_in_millis": 0,
                           "delete_total": 0,
                           "index_current": 0,
                           "index_time_in_millis": 0,
                           "index_total": 0,
                           "is_throttled": false,
                           "noop_update_total": 0,
                           "throttle_time_in_millis": 0
                       },
                       "merges": {
                           "current": 0,
                           "current_docs": 0,
                           "current_size_in_bytes": 0,
                           "total": 0,
                           "total_docs": 0,
                           "total_size_in_bytes": 0,
                           "total_time_in_millis": 0
                       },
                       "percolate": {
                           "current": 0,
                           "memory_size": "-1b",
                           "memory_size_in_bytes": -1,
                           "queries": 0,
                           "time_in_millis": 0,
                           "total": 0
                       },
                       "query_cache": {
                           "evictions": 0,
                           "hit_count": 0,
                           "memory_size_in_bytes": 0,
                           "miss_count": 0
                       },
                       "recovery": {
                           "current_as_source": 0,
                           "current_as_target": 0,
                           "throttle_time_in_millis": 0
                       },
                       "refresh": {
                           "total": 0,
                           "total_time_in_millis": 0
                       },
                       "search": {
                           "fetch_current": 0,
                           "fetch_time_in_millis": 0,
                           "fetch_total": 0,
                           "open_contexts": 0,
                           "query_current": 0,
                           "query_time_in_millis": 0,
                           "query_total": 0
                       },
                       "segments": {
                           "count": 0,
                           "fixed_bit_set_memory_in_bytes": 0,
                           "index_writer_max_memory_in_bytes": 0,
                           "index_writer_memory_in_bytes": 0,
                           "memory_in_bytes": 0,
                           "version_map_memory_in_bytes": 0
                       },
                       "store": {
                           "size_in_bytes": 0,
                           "throttle_time_in_millis": 0
                       },
                       "suggest": {
                           "current": 0,
                           "time_in_millis": 0,
                           "total": 0
                       },
                       "translog": {
                           "operations": 0,
                           "size_in_bytes": 0
                       },
                       "warmer": {
                           "current": 0,
                           "total": 0,
                           "total_time_in_millis": 0
                       }
                   },
                   "ip": [
                       "inet[/10.56.149.40:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 37,
                               "total_capacity_in_bytes": 7368161,
                               "used_in_bytes": 7368161
                           },
                           "mapped": {
                               "count": 0,
                               "total_capacity_in_bytes": 0,
                               "used_in_bytes": 0
                           }
                       },
                       "gc": {
                           "collectors": {
                               "old": {
                                   "collection_count": 1,
                                   "collection_time_in_millis": 35
                               },
                               "young": {
                                   "collection_count": 52,
                                   "collection_time_in_millis": 451
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 1056309248,
                           "heap_max_in_bytes": 1056309248,
                           "heap_used_in_bytes": 158279424,
                           "heap_used_percent": 14,
                           "non_heap_committed_in_bytes": 47075328,
                           "non_heap_used_in_bytes": 46214696,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 899284992,
                                   "peak_max_in_bytes": 899284992,
                                   "peak_used_in_bytes": 23342440,
                                   "used_in_bytes": 23342440
                               },
                               "survivor": {
                                   "max_in_bytes": 17432576,
                                   "peak_max_in_bytes": 17432576,
                                   "peak_used_in_bytes": 17432568,
                                   "used_in_bytes": 43800
                               },
                               "young": {
                                   "max_in_bytes": 139591680,
                                   "peak_max_in_bytes": 139591680,
                                   "peak_used_in_bytes": 139591680,
                                   "used_in_bytes": 134895296
                               }
                           }
                       },
                       "threads": {
                           "count": 34,
                           "peak_count": 42
                       },
                       "timestamp": 1441736480983,
                       "uptime_in_millis": 949697791
                   },
                   "name": "iad1esapp0vz114",
                   "network": {
                       "tcp": {
                           "active_opens": 167,
                           "attempt_fails": 0,
                           "curr_estab": 318,
                           "estab_resets": 0,
                           "in_errs": 1,
                           "in_segs": 2929397,
                           "out_rsts": 235,
                           "out_segs": 2927635,
                           "passive_opens": 1261,
                           "retrans_segs": 257
                       }
                   },
                   "os": {
                       "cpu": {
                           "idle": 99,
                           "stolen": 0,
                           "sys": 0,
                           "usage": 0,
                           "user": 0
                       },
                       "load_average": [
                           0.01,
                           0.01,
                           0.0
                       ],
                       "mem": {
                           "actual_free_in_bytes": 849420288,
                           "actual_used_in_bytes": 1298063360,
                           "free_in_bytes": 770256896,
                           "free_percent": 39,
                           "used_in_bytes": 1377226752,
                           "used_percent": 60
                       },
                       "swap": {
                           "free_in_bytes": 1073741824,
                           "used_in_bytes": 0
                       },
                       "timestamp": 1441736480982,
                       "uptime_in_millis": 949718
                   },
                   "process": {
                       "cpu": {
                           "percent": 0,
                           "sys_in_millis": 729230,
                           "total_in_millis": 1569370,
                           "user_in_millis": 840140
                       },
                       "mem": {
                           "resident_in_bytes": 1298255872,
                           "share_in_bytes": 21020672,
                           "total_virtual_in_bytes": 3612360704
                       },
                       "open_file_descriptors": 419,
                       "timestamp": 1441736480983
                   },
                   "thread_pool": {
                       "bulk": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "fetch_shard_started": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "fetch_shard_store": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "flush": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "generic": {
                           "active": 0,
                           "completed": 1044348,
                           "largest": 8,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 1
                       },
                       "get": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "index": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "listener": {
                           "active": 0,
                           "completed": 1089,
                           "largest": 1,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 1
                       },
                       "management": {
                           "active": 1,
                           "completed": 173,
                           "largest": 1,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 1
                       },
                       "merge": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "optimize": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "percolate": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "refresh": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "search": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "snapshot": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "suggest": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "warmer": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       }
                   },
                   "timestamp": 1441736480982,
                   "transport": {
                       "rx_count": 1900464,
                       "rx_size_in_bytes": 275314557,
                       "server_open": 156,
                       "tx_count": 1900475,
                       "tx_size_in_bytes": 149575073
                   },
                   "transport_address": "inet[/10.56.149.40:30121]"
               },
               "36KI-d_RSZer8yGV8yTQbA": {
                   "attributes": {
                       "data": "false",
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esapp3"
                   },
                   "breakers": {
                       "fielddata": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "604.4mb",
                           "limit_size_in_bytes": 633785548,
                           "overhead": 1.03,
                           "tripped": 0
                       },
                       "parent": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "705.1mb",
                           "limit_size_in_bytes": 739416473,
                           "overhead": 1.0,
                           "tripped": 0
                       },
                       "request": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "402.9mb",
                           "limit_size_in_bytes": 422523699,
                           "overhead": 1.0,
                           "tripped": 0
                       }
                   },
                   "fs": {
                       "data": [],
                       "timestamp": 1441736480983,
                       "total": {}
                   },
                   "host": "iad1esapp3vz114",
                   "http": {
                       "current_open": 1,
                       "total_opened": 1061
                   },
                   "indices": {
                       "completion": {
                           "size_in_bytes": 0
                       },
                       "docs": {
                           "count": 0,
                           "deleted": 0
                       },
                       "fielddata": {
                           "evictions": 0,
                           "memory_size_in_bytes": 0
                       },
                       "filter_cache": {
                           "evictions": 0,
                           "memory_size_in_bytes": 0
                       },
                       "flush": {
                           "total": 0,
                           "total_time_in_millis": 0
                       },
                       "get": {
                           "current": 0,
                           "exists_time_in_millis": 0,
                           "exists_total": 0,
                           "missing_time_in_millis": 0,
                           "missing_total": 0,
                           "time_in_millis": 0,
                           "total": 0
                       },
                       "id_cache": {
                           "memory_size_in_bytes": 0
                       },
                       "indexing": {
                           "delete_current": 0,
                           "delete_time_in_millis": 0,
                           "delete_total": 0,
                           "index_current": 0,
                           "index_time_in_millis": 0,
                           "index_total": 0,
                           "is_throttled": false,
                           "noop_update_total": 0,
                           "throttle_time_in_millis": 0
                       },
                       "merges": {
                           "current": 0,
                           "current_docs": 0,
                           "current_size_in_bytes": 0,
                           "total": 0,
                           "total_docs": 0,
                           "total_size_in_bytes": 0,
                           "total_time_in_millis": 0
                       },
                       "percolate": {
                           "current": 0,
                           "memory_size": "-1b",
                           "memory_size_in_bytes": -1,
                           "queries": 0,
                           "time_in_millis": 0,
                           "total": 0
                       },
                       "query_cache": {
                           "evictions": 0,
                           "hit_count": 0,
                           "memory_size_in_bytes": 0,
                           "miss_count": 0
                       },
                       "recovery": {
                           "current_as_source": 0,
                           "current_as_target": 0,
                           "throttle_time_in_millis": 0
                       },
                       "refresh": {
                           "total": 0,
                           "total_time_in_millis": 0
                       },
                       "search": {
                           "fetch_current": 0,
                           "fetch_time_in_millis": 0,
                           "fetch_total": 0,
                           "open_contexts": 0,
                           "query_current": 0,
                           "query_time_in_millis": 0,
                           "query_total": 0
                       },
                       "segments": {
                           "count": 0,
                           "fixed_bit_set_memory_in_bytes": 0,
                           "index_writer_max_memory_in_bytes": 0,
                           "index_writer_memory_in_bytes": 0,
                           "memory_in_bytes": 0,
                           "version_map_memory_in_bytes": 0
                       },
                       "store": {
                           "size_in_bytes": 0,
                           "throttle_time_in_millis": 0
                       },
                       "suggest": {
                           "current": 0,
                           "time_in_millis": 0,
                           "total": 0
                       },
                       "translog": {
                           "operations": 0,
                           "size_in_bytes": 0
                       },
                       "warmer": {
                           "current": 0,
                           "total": 0,
                           "total_time_in_millis": 0
                       }
                   },
                   "ip": [
                       "inet[/10.56.149.41:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 39,
                               "total_capacity_in_bytes": 7401473,
                               "used_in_bytes": 7401473
                           },
                           "mapped": {
                               "count": 0,
                               "total_capacity_in_bytes": 0,
                               "used_in_bytes": 0
                           }
                       },
                       "gc": {
                           "collectors": {
                               "old": {
                                   "collection_count": 1,
                                   "collection_time_in_millis": 39
                               },
                               "young": {
                                   "collection_count": 53,
                                   "collection_time_in_millis": 464
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 1056309248,
                           "heap_max_in_bytes": 1056309248,
                           "heap_used_in_bytes": 152458552,
                           "heap_used_percent": 14,
                           "non_heap_committed_in_bytes": 47169536,
                           "non_heap_used_in_bytes": 46457488,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 899284992,
                                   "peak_max_in_bytes": 899284992,
                                   "peak_used_in_bytes": 23392360,
                                   "used_in_bytes": 23392360
                               },
                               "survivor": {
                                   "max_in_bytes": 17432576,
                                   "peak_max_in_bytes": 17432576,
                                   "peak_used_in_bytes": 17432568,
                                   "used_in_bytes": 42240
                               },
                               "young": {
                                   "max_in_bytes": 139591680,
                                   "peak_max_in_bytes": 139591680,
                                   "peak_used_in_bytes": 139591680,
                                   "used_in_bytes": 129024000
                               }
                           }
                       },
                       "threads": {
                           "count": 34,
                           "peak_count": 42
                       },
                       "timestamp": 1441736480983,
                       "uptime_in_millis": 949697790
                   },
                   "name": "iad1esapp3vz114",
                   "network": {
                       "tcp": {
                           "active_opens": 166,
                           "attempt_fails": 0,
                           "curr_estab": 315,
                           "estab_resets": 0,
                           "in_errs": 0,
                           "in_segs": 2928986,
                           "out_rsts": 172,
                           "out_segs": 2927091,
                           "passive_opens": 1252,
                           "retrans_segs": 203
                       }
                   },
                   "os": {
                       "cpu": {
                           "idle": 99,
                           "stolen": 0,
                           "sys": 0,
                           "usage": 0,
                           "user": 0
                       },
                       "load_average": [
                           0.08,
                           0.03,
                           0.01
                       ],
                       "mem": {
                           "actual_free_in_bytes": 849227776,
                           "actual_used_in_bytes": 1298255872,
                           "free_in_bytes": 770347008,
                           "free_percent": 39,
                           "used_in_bytes": 1377136640,
                           "used_percent": 60
                       },
                       "swap": {
                           "free_in_bytes": 1073741824,
                           "used_in_bytes": 0
                       },
                       "timestamp": 1441736480982,
                       "uptime_in_millis": 949718
                   },
                   "process": {
                       "cpu": {
                           "percent": 0,
                           "sys_in_millis": 749880,
                           "total_in_millis": 1622800,
                           "user_in_millis": 872920
                       },
                       "mem": {
                           "resident_in_bytes": 1298591744,
                           "share_in_bytes": 21020672,
                           "total_virtual_in_bytes": 3612364800
                       },
                       "open_file_descriptors": 418,
                       "timestamp": 1441736480982
                   },
                   "thread_pool": {
                       "bulk": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "fetch_shard_started": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "fetch_shard_store": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "flush": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "generic": {
                           "active": 0,
                           "completed": 1044354,
                           "largest": 8,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 1
                       },
                       "get": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "index": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "listener": {
                           "active": 0,
                           "completed": 1079,
                           "largest": 1,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 1
                       },
                       "management": {
                           "active": 1,
                           "completed": 173,
                           "largest": 1,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 1
                       },
                       "merge": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "optimize": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "percolate": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "refresh": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "search": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "snapshot": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "suggest": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "warmer": {
                           "active": 0,
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       }
                   },
                   "timestamp": 1441736480982,
                   "transport": {
                       "rx_count": 1900355,
                       "rx_size_in_bytes": 274900419,
                       "server_open": 156,
                       "tx_count": 1900354,
                       "tx_size_in_bytes": 149606826
                   },
                   "transport_address": "inet[/10.56.149.41:30121]"
               },
               {
                   "..."
               }
           }
       }
   }

Get details on an account's Elasticsearch instances
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/

Response:

.. code-block:: bash

   {
       "data": [
           {
               "api_key": "2f91e30a48d94ef0ba403edf017d9e60",
               "caster": null,
               "connection_strings": {
                   "public": {
                       "http": "http://iad1-10121-0.es.objectrocket.com:10121,http://iad1-10121-1.es.objectrocket.com:10121,http://iad1-10121-2.es.objectrocket.com:10121,http://iad1-10121-3.es.objectrocket.com:10121",
                       "https": "https://iad1-10121-0.es.objectrocket.com:20121,https://iad1-10121-1.es.objectrocket.com:20121,https://iad1-10121-2.es.objectrocket.com:20121,https://iad1-10121-3.es.objectrocket.com:20121",
                       "transport": "iad1-10121-0.es.objectrocket.com:40121,iad1-10121-1.es.objectrocket.com:40121,iad1-10121-2.es.objectrocket.com:40121,iad1-10121-3.es.objectrocket.com:40121"
                   },
                   "servicenet": {
                       "http": "http://iad1-sn-10121-0.es.objectrocket.com:10121,http://iad1-sn-10121-1.es.objectrocket.com:10121,http://iad1-sn-10121-2.es.objectrocket.com:10121,http://iad1-sn-10121-3.es.objectrocket.com:10121",
                       "https": "https://iad1-sn-10121-0.es.objectrocket.com:20121,https://iad1-sn-10121-1.es.objectrocket.com:20121,https://iad1-sn-10121-2.es.objectrocket.com:20121,https://iad1-sn-10121-3.es.objectrocket.com:20121",
                       "transport": "iad1-sn-10121-0.es.objectrocket.com:40121,iad1-sn-10121-1.es.objectrocket.com:40121,iad1-sn-10121-2.es.objectrocket.com:40121,iad1-sn-10121-3.es.objectrocket.com:40121"
                   }
               },
               "created": "2015-08-28 11:32:04",
               "id": "55e0a924cb143c426df6927e",
               "name": "Elasticsearch123",
               "plan": 2,
               "service": "elasticsearch",
               "state": "COMPLETED",
               "type": "elasticsearch",
               "version": "1.6.2",
               "zone": "US-East-IAD1"
           }
       ]
   }

Get a list of all users currently added to the instance specified by name
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/<instance_name>/users/

Response:

.. code-block:: bash

   {
       "data": [
           {
               "role": "admin",
               "username": "username123"
           }
       ]
   }

Create or update a user for the instance specified by name
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /elasticsearch/<instance_name>/users/

.. note::

   The **role** field must be one of the following: admin or readonly.

Request:

.. code-block:: bash

   {
       "password": "password123",
       "role": "admin",
       "username": "username123"
   }

Response:

.. code-block:: bash

   {
       "data": {
           "role": "admin",
           "username": "username123"
       }
   }

Delete a user from the instance specified by name
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   DELETE /elasticsearch/<instance_name>/users/

Request:

.. code-block:: bash

   {
       "username": "username123"
   }

Response:

.. code-block:: bash

   {
       "data": {
           "username": "username123"
       }
   }

