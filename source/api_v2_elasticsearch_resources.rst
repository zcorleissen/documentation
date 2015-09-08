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
               "3jmRQ_-nQq-C555e_Kzn4w": {
                   "attributes": {
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esdn7"
                   },
                   "breakers": {
                       "fielddata": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "74.2mb",
                           "limit_size_in_bytes": 77856768,
                           "overhead": 1.03,
                           "tripped": 0
                       },
                       "parent": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "86.6mb",
                           "limit_size_in_bytes": 90832896,
                           "overhead": 1.0,
                           "tripped": 0
                       },
                       "request": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "49.5mb",
                           "limit_size_in_bytes": 51904512,
                           "overhead": 1.0,
                           "tripped": 0
                       }
                   },
                   "fs": {
                       "data": [
                           {
                               "available_in_bytes": 2043478016,
                               "dev": "/dev/simfs",
                               "free_in_bytes": 2043478016,
                               "mount": "/data0",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total_in_bytes": 2046640128,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736481238,
                       "total": {
                           "available_in_bytes": 2043478016,
                           "free_in_bytes": 2043478016,
                           "total_in_bytes": 2046640128
                       }
                   },
                   "host": "iad1esdn7vz22",
                   "http": {
                       "current_open": 0,
                       "total_opened": 1054
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
                       "inet[/10.56.148.13:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 32,
                               "total_capacity_in_bytes": 7079788,
                               "used_in_bytes": 7079788
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
                                   "collection_time_in_millis": 18
                               },
                               "young": {
                                   "collection_count": 205,
                                   "collection_time_in_millis": 581
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 129761280,
                           "heap_max_in_bytes": 129761280,
                           "heap_used_in_bytes": 43166032,
                           "heap_used_percent": 33,
                           "non_heap_committed_in_bytes": 46473216,
                           "non_heap_used_in_bytes": 45777336,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 89522176,
                                   "peak_max_in_bytes": 89522176,
                                   "peak_used_in_bytes": 19178184,
                                   "used_in_bytes": 19178184
                               },
                               "survivor": {
                                   "max_in_bytes": 4456448,
                                   "peak_max_in_bytes": 4456448,
                                   "peak_used_in_bytes": 4456448,
                                   "used_in_bytes": 8832
                               },
                               "young": {
                                   "max_in_bytes": 35782656,
                                   "peak_max_in_bytes": 35782656,
                                   "peak_used_in_bytes": 35782656,
                                   "used_in_bytes": 23979016
                               }
                           }
                       },
                       "threads": {
                           "count": 29,
                           "peak_count": 36
                       },
                       "timestamp": 1441736481237,
                       "uptime_in_millis": 942263955
                   },
                   "name": "iad1esdn7vz22",
                   "network": {
                       "tcp": {
                           "active_opens": 159,
                           "attempt_fails": 0,
                           "curr_estab": 313,
                           "estab_resets": 0,
                           "in_errs": 0,
                           "in_segs": 2962918,
                           "out_rsts": 1,
                           "out_segs": 2929975,
                           "passive_opens": 1213,
                           "retrans_segs": 247
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
                           0.04,
                           0.01,
                           0.0
                       ],
                       "mem": {
                           "actual_free_in_bytes": 25477120,
                           "actual_used_in_bytes": 242958336,
                           "free_in_bytes": 15228928,
                           "free_percent": 9,
                           "used_in_bytes": 253206528,
                           "used_percent": 90
                       },
                       "swap": {
                           "free_in_bytes": 1021513728,
                           "used_in_bytes": 52228096
                       },
                       "timestamp": 1441736481236,
                       "uptime_in_millis": 942277
                   },
                   "process": {
                       "cpu": {
                           "percent": 0,
                           "sys_in_millis": 728800,
                           "total_in_millis": 1524980,
                           "user_in_millis": 796180
                       },
                       "mem": {
                           "resident_in_bytes": 251736064,
                           "share_in_bytes": 15183872,
                           "total_virtual_in_bytes": 2649571328
                       },
                       "open_file_descriptors": 402,
                       "timestamp": 1441736481237
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
                           "completed": 1036142,
                           "largest": 6,
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
                           "completed": 1054,
                           "largest": 1,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 1
                       },
                       "management": {
                           "active": 1,
                           "completed": 31580,
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
                   "timestamp": 1441736481235,
                   "transport": {
                       "rx_count": 1916515,
                       "rx_size_in_bytes": 275041422,
                       "server_open": 156,
                       "tx_count": 1916514,
                       "tx_size_in_bytes": 159298640
                   },
                   "transport_address": "inet[/10.56.148.13:30121]"
               },
               "88Oi2D4DTnaLS1J4r1pm-A": {
                   "attributes": {
                       "data": "false",
                       "master": "true",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esmst1"
                   },
                   "breakers": {
                       "fielddata": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "297.2mb",
                           "limit_size_in_bytes": 311663001,
                           "overhead": 1.03,
                           "tripped": 0
                       },
                       "parent": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "346.7mb",
                           "limit_size_in_bytes": 363606835,
                           "overhead": 1.0,
                           "tripped": 0
                       },
                       "request": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "198.1mb",
                           "limit_size_in_bytes": 207775334,
                           "overhead": 1.0,
                           "tripped": 0
                       }
                   },
                   "fs": {
                       "data": [
                           {
                               "available_in_bytes": 3641090048,
                               "dev": "/dev/simfs",
                               "free_in_bytes": 3641090048,
                               "mount": "/",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total_in_bytes": 4294967296,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736480984,
                       "total": {
                           "available_in_bytes": 3641090048,
                           "free_in_bytes": 3641090048,
                           "total_in_bytes": 4294967296
                       }
                   },
                   "host": "iad1esmst1vz114",
                   "http": {
                       "current_open": 0,
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
                       "inet[/10.56.149.39:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 41,
                               "total_capacity_in_bytes": 7084630,
                               "used_in_bytes": 7084630
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
                                   "collection_time_in_millis": 46
                               },
                               "young": {
                                   "collection_count": 279,
                                   "collection_time_in_millis": 1213
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 519438336,
                           "heap_max_in_bytes": 519438336,
                           "heap_used_in_bytes": 66746224,
                           "heap_used_percent": 12,
                           "non_heap_committed_in_bytes": 49000448,
                           "non_heap_used_in_bytes": 48176952,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 362414080,
                                   "peak_max_in_bytes": 362414080,
                                   "peak_used_in_bytes": 23400280,
                                   "used_in_bytes": 23400280
                               },
                               "survivor": {
                                   "max_in_bytes": 17432576,
                                   "peak_max_in_bytes": 17432576,
                                   "peak_used_in_bytes": 17432560,
                                   "used_in_bytes": 19648
                               },
                               "young": {
                                   "max_in_bytes": 139591680,
                                   "peak_max_in_bytes": 139591680,
                                   "peak_used_in_bytes": 139591680,
                                   "used_in_bytes": 43326296
                               }
                           }
                       },
                       "threads": {
                           "count": 32,
                           "peak_count": 42
                       },
                       "timestamp": 1441736480983,
                       "uptime_in_millis": 949697770
                   },
                   "name": "iad1esmst1vz114",
                   "network": {
                       "tcp": {
                           "active_opens": 173,
                           "attempt_fails": 0,
                           "curr_estab": 313,
                           "estab_resets": 0,
                           "in_errs": 0,
                           "in_segs": 25782930,
                           "out_rsts": 1,
                           "out_segs": 25865057,
                           "passive_opens": 1247,
                           "retrans_segs": 0
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
                           0.0,
                           0.0,
                           0.0
                       ],
                       "mem": {
                           "actual_free_in_bytes": 382390272,
                           "actual_used_in_bytes": 691351552,
                           "free_in_bytes": 355352576,
                           "free_percent": 35,
                           "used_in_bytes": 718389248,
                           "used_percent": 64
                       },
                       "swap": {
                           "free_in_bytes": 2147483648,
                           "used_in_bytes": 0
                       },
                       "timestamp": 1441736480982,
                       "uptime_in_millis": 949718
                   },
                   "process": {
                       "cpu": {
                           "percent": 0,
                           "sys_in_millis": 1249050,
                           "total_in_millis": 2457480,
                           "user_in_millis": 1208430
                       },
                       "mem": {
                           "resident_in_bytes": 695611392,
                           "share_in_bytes": 16560128,
                           "total_virtual_in_bytes": 3064881152
                       },
                       "open_file_descriptors": 402,
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
                           "completed": 95049,
                           "largest": 6,
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
                           "completed": 10708,
                           "largest": 1,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 1
                       },
                       "management": {
                           "active": 1,
                           "completed": 63490,
                           "largest": 2,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 2
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
                           "completed": 33,
                           "largest": 1,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 1
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
                       "rx_count": 17180522,
                       "rx_size_in_bytes": 1373771161,
                       "server_open": 156,
                       "tx_count": 17180521,
                       "tx_size_in_bytes": 2471789419
                   },
                   "transport_address": "inet[/10.56.149.39:30121]"
               },
               "JSwkmSTLR6G2Y8CLhkGxDQ": {
                   "attributes": {
                       "data": "false",
                       "master": "true",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esmst2"
                   },
                   "breakers": {
                       "fielddata": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "297.2mb",
                           "limit_size_in_bytes": 311663001,
                           "overhead": 1.03,
                           "tripped": 0
                       },
                       "parent": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "346.7mb",
                           "limit_size_in_bytes": 363606835,
                           "overhead": 1.0,
                           "tripped": 0
                       },
                       "request": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "198.1mb",
                           "limit_size_in_bytes": 207775334,
                           "overhead": 1.0,
                           "tripped": 0
                       }
                   },
                   "fs": {
                       "data": [
                           {
                               "available_in_bytes": 3641126912,
                               "dev": "/dev/simfs",
                               "free_in_bytes": 3641126912,
                               "mount": "/",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total_in_bytes": 4294967296,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736481313,
                       "total": {
                           "available_in_bytes": 3641126912,
                           "free_in_bytes": 3641126912,
                           "total_in_bytes": 4294967296
                       }
                   },
                   "host": "iad1esmst2vz114",
                   "http": {
                       "current_open": 0,
                       "total_opened": 1059
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
                       "inet[/10.56.149.38:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 33,
                               "total_capacity_in_bytes": 7080418,
                               "used_in_bytes": 7080418
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
                                   "collection_time_in_millis": 40
                               },
                               "young": {
                                   "collection_count": 53,
                                   "collection_time_in_millis": 284
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 519438336,
                           "heap_max_in_bytes": 519438336,
                           "heap_used_in_bytes": 109351952,
                           "heap_used_percent": 21,
                           "non_heap_committed_in_bytes": 46993408,
                           "non_heap_used_in_bytes": 45960032,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 362414080,
                                   "peak_max_in_bytes": 362414080,
                                   "peak_used_in_bytes": 22800312,
                                   "used_in_bytes": 22800312
                               },
                               "survivor": {
                                   "max_in_bytes": 17432576,
                                   "peak_max_in_bytes": 17432576,
                                   "peak_used_in_bytes": 17432568,
                                   "used_in_bytes": 65184
                               },
                               "young": {
                                   "max_in_bytes": 139591680,
                                   "peak_max_in_bytes": 139591680,
                                   "peak_used_in_bytes": 139591680,
                                   "used_in_bytes": 86486456
                               }
                           }
                       },
                       "threads": {
                           "count": 29,
                           "peak_count": 40
                       },
                       "timestamp": 1441736481312,
                       "uptime_in_millis": 949698108
                   },
                   "name": "iad1esmst2vz114",
                   "network": {
                       "tcp": {
                           "active_opens": 174,
                           "attempt_fails": 0,
                           "curr_estab": 313,
                           "estab_resets": 0,
                           "in_errs": 0,
                           "in_segs": 2925734,
                           "out_rsts": 2,
                           "out_segs": 2924058,
                           "passive_opens": 1245,
                           "retrans_segs": 93
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
                           0.0,
                           0.0,
                           0.0
                       ],
                       "mem": {
                           "actual_free_in_bytes": 377749504,
                           "actual_used_in_bytes": 695992320,
                           "free_in_bytes": 350588928,
                           "free_percent": 35,
                           "used_in_bytes": 723152896,
                           "used_percent": 64
                       },
                       "swap": {
                           "free_in_bytes": 2147483648,
                           "used_in_bytes": 0
                       },
                       "timestamp": 1441736481311,
                       "uptime_in_millis": 949718
                   },
                   "process": {
                       "cpu": {
                           "percent": 0,
                           "sys_in_millis": 618330,
                           "total_in_millis": 1308000,
                           "user_in_millis": 689670
                       },
                       "mem": {
                           "resident_in_bytes": 700530688,
                           "share_in_bytes": 16510976,
                           "total_virtual_in_bytes": 3062788096
                       },
                       "open_file_descriptors": 402,
                       "timestamp": 1441736481311
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
                           "completed": 1044420,
                           "largest": 6,
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
                           "completed": 1059,
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
                   "timestamp": 1441736481311,
                   "transport": {
                       "rx_count": 1900151,
                       "rx_size_in_bytes": 273643541,
                       "server_open": 156,
                       "tx_count": 1900150,
                       "tx_size_in_bytes": 149938112
                   },
                   "transport_address": "inet[/10.56.149.38:30121]"
               },
               "MxuHzXqaRk29rnmc8UJDBw": {
                   "attributes": {
                       "data": "false",
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esapp2"
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
                       "timestamp": 1441736481049,
                       "total": {}
                   },
                   "host": "iad1esapp2vz114",
                   "http": {
                       "current_open": 1,
                       "total_opened": 1064
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
                       "inet[/10.56.149.43:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 37,
                               "total_capacity_in_bytes": 7366857,
                               "used_in_bytes": 7366857
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
                                   "collection_time_in_millis": 38
                               },
                               "young": {
                                   "collection_count": 52,
                                   "collection_time_in_millis": 430
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 1056309248,
                           "heap_max_in_bytes": 1056309248,
                           "heap_used_in_bytes": 128158016,
                           "heap_used_percent": 12,
                           "non_heap_committed_in_bytes": 46653440,
                           "non_heap_used_in_bytes": 45863472,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 899284992,
                                   "peak_max_in_bytes": 899284992,
                                   "peak_used_in_bytes": 22931576,
                                   "used_in_bytes": 22931576
                               },
                               "survivor": {
                                   "max_in_bytes": 17432576,
                                   "peak_max_in_bytes": 17432576,
                                   "peak_used_in_bytes": 17432576,
                                   "used_in_bytes": 33144
                               },
                               "young": {
                                   "max_in_bytes": 139591680,
                                   "peak_max_in_bytes": 139591680,
                                   "peak_used_in_bytes": 139591680,
                                   "used_in_bytes": 105193296
                               }
                           }
                       },
                       "threads": {
                           "count": 34,
                           "peak_count": 41
                       },
                       "timestamp": 1441736481048,
                       "uptime_in_millis": 949697853
                   },
                   "name": "iad1esapp2vz114",
                   "network": {
                       "tcp": {
                           "active_opens": 166,
                           "attempt_fails": 0,
                           "curr_estab": 315,
                           "estab_resets": 0,
                           "in_errs": 0,
                           "in_segs": 2928572,
                           "out_rsts": 100,
                           "out_segs": 2926514,
                           "passive_opens": 1244,
                           "retrans_segs": 211
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
                           0.1,
                           0.04,
                           0.01
                       ],
                       "mem": {
                           "actual_free_in_bytes": 868167680,
                           "actual_used_in_bytes": 1279315968,
                           "free_in_bytes": 789073920,
                           "free_percent": 40,
                           "used_in_bytes": 1358409728,
                           "used_percent": 59
                       },
                       "swap": {
                           "free_in_bytes": 1073741824,
                           "used_in_bytes": 0
                       },
                       "timestamp": 1441736481047,
                       "uptime_in_millis": 949718
                   },
                   "process": {
                       "cpu": {
                           "percent": 0,
                           "sys_in_millis": 739190,
                           "total_in_millis": 1539790,
                           "user_in_millis": 800600
                       },
                       "mem": {
                           "resident_in_bytes": 1279623168,
                           "share_in_bytes": 21020672,
                           "total_virtual_in_bytes": 3611320320
                       },
                       "open_file_descriptors": 418,
                       "timestamp": 1441736481047
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
                           "completed": 1044372,
                           "largest": 7,
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
                           "completed": 1074,
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
                   "timestamp": 1441736481047,
                   "transport": {
                       "rx_count": 1900223,
                       "rx_size_in_bytes": 274381281,
                       "server_open": 156,
                       "tx_count": 1900222,
                       "tx_size_in_bytes": 149648454
                   },
                   "transport_address": "inet[/10.56.149.43:30121]"
               },
               "hqC9t45pQ1ac1Jve3bzeiA": {
                   "attributes": {
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esdn4"
                   },
                   "breakers": {
                       "fielddata": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "74.2mb",
                           "limit_size_in_bytes": 77856768,
                           "overhead": 1.03,
                           "tripped": 0
                       },
                       "parent": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "86.6mb",
                           "limit_size_in_bytes": 90832896,
                           "overhead": 1.0,
                           "tripped": 0
                       },
                       "request": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "49.5mb",
                           "limit_size_in_bytes": 51904512,
                           "overhead": 1.0,
                           "tripped": 0
                       }
                   },
                   "fs": {
                       "data": [
                           {
                               "available_in_bytes": 2043478016,
                               "dev": "/dev/simfs",
                               "free_in_bytes": 2043478016,
                               "mount": "/data0",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total_in_bytes": 2046640128,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736481106,
                       "total": {
                           "available_in_bytes": 2043478016,
                           "free_in_bytes": 2043478016,
                           "total_in_bytes": 2046640128
                       }
                   },
                   "host": "iad1esdn4vz25",
                   "http": {
                       "current_open": 0,
                       "total_opened": 1060
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
                       "inet[/10.56.147.224:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 32,
                               "total_capacity_in_bytes": 7079788,
                               "used_in_bytes": 7079788
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
                                   "collection_time_in_millis": 12
                               },
                               "young": {
                                   "collection_count": 207,
                                   "collection_time_in_millis": 579
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 129761280,
                           "heap_max_in_bytes": 129761280,
                           "heap_used_in_bytes": 26109880,
                           "heap_used_percent": 20,
                           "non_heap_committed_in_bytes": 46694400,
                           "non_heap_used_in_bytes": 45868984,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 89522176,
                                   "peak_max_in_bytes": 89522176,
                                   "peak_used_in_bytes": 19393544,
                                   "used_in_bytes": 19393544
                               },
                               "survivor": {
                                   "max_in_bytes": 4456448,
                                   "peak_max_in_bytes": 4456448,
                                   "peak_used_in_bytes": 4456448,
                                   "used_in_bytes": 134688
                               },
                               "young": {
                                   "max_in_bytes": 35782656,
                                   "peak_max_in_bytes": 35782656,
                                   "peak_used_in_bytes": 35782656,
                                   "used_in_bytes": 6586328
                               }
                           }
                       },
                       "threads": {
                           "count": 29,
                           "peak_count": 37
                       },
                       "timestamp": 1441736481105,
                       "uptime_in_millis": 949697901
                   },
                   "name": "iad1esdn4vz25",
                   "network": {
                       "tcp": {
                           "active_opens": 163,
                           "attempt_fails": 0,
                           "curr_estab": 313,
                           "estab_resets": 0,
                           "in_errs": 1,
                           "in_segs": 2987002,
                           "out_rsts": 2,
                           "out_segs": 2953753,
                           "passive_opens": 1226,
                           "retrans_segs": 231
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
                           0.0,
                           0.0,
                           0.0
                       ],
                       "mem": {
                           "actual_free_in_bytes": 25853952,
                           "actual_used_in_bytes": 242581504,
                           "free_in_bytes": 15380480,
                           "free_percent": 9,
                           "used_in_bytes": 253054976,
                           "used_percent": 90
                       },
                       "swap": {
                           "free_in_bytes": 1045958656,
                           "used_in_bytes": 27783168
                       },
                       "timestamp": 1441736481105,
                       "uptime_in_millis": 949718
                   },
                   "process": {
                       "cpu": {
                           "percent": 0,
                           "sys_in_millis": 683380,
                           "total_in_millis": 1634430,
                           "user_in_millis": 951050
                       },
                       "mem": {
                           "resident_in_bytes": 249479168,
                           "share_in_bytes": 15925248,
                           "total_virtual_in_bytes": 2650624000
                       },
                       "open_file_descriptors": 402,
                       "timestamp": 1441736481105
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
                           "completed": 1044343,
                           "largest": 7,
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
                           "completed": 1060,
                           "largest": 1,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 1
                       },
                       "management": {
                           "active": 1,
                           "completed": 31833,
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
                   "timestamp": 1441736481105,
                   "transport": {
                       "rx_count": 1931651,
                       "rx_size_in_bytes": 277265184,
                       "server_open": 156,
                       "tx_count": 1931650,
                       "tx_size_in_bytes": 160608630
                   },
                   "transport_address": "inet[/10.56.147.224:30121]"
               },
               "kABYN4O0QCiQti05G_Zgcg": {
                   "attributes": {
                       "data": "false",
                       "master": "true",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esmst0"
                   },
                   "breakers": {
                       "fielddata": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "297.2mb",
                           "limit_size_in_bytes": 311663001,
                           "overhead": 1.03,
                           "tripped": 0
                       },
                       "parent": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "346.7mb",
                           "limit_size_in_bytes": 363606835,
                           "overhead": 1.0,
                           "tripped": 0
                       },
                       "request": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "198.1mb",
                           "limit_size_in_bytes": 207775334,
                           "overhead": 1.0,
                           "tripped": 0
                       }
                   },
                   "fs": {
                       "data": [
                           {
                               "available_in_bytes": 3641126912,
                               "dev": "/dev/simfs",
                               "free_in_bytes": 3641126912,
                               "mount": "/",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total_in_bytes": 4294967296,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736481498,
                       "total": {
                           "available_in_bytes": 3641126912,
                           "free_in_bytes": 3641126912,
                           "total_in_bytes": 4294967296
                       }
                   },
                   "host": "iad1esmst0vz114",
                   "http": {
                       "current_open": 0,
                       "total_opened": 1085
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
                       "inet[/10.56.149.45:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 33,
                               "total_capacity_in_bytes": 7080418,
                               "used_in_bytes": 7080418
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
                                   "collection_time_in_millis": 46
                               },
                               "young": {
                                   "collection_count": 53,
                                   "collection_time_in_millis": 299
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 519438336,
                           "heap_max_in_bytes": 519438336,
                           "heap_used_in_bytes": 134589832,
                           "heap_used_percent": 25,
                           "non_heap_committed_in_bytes": 47255552,
                           "non_heap_used_in_bytes": 46475784,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 362414080,
                                   "peak_max_in_bytes": 362414080,
                                   "peak_used_in_bytes": 22977224,
                                   "used_in_bytes": 22977224
                               },
                               "survivor": {
                                   "max_in_bytes": 17432576,
                                   "peak_max_in_bytes": 17432576,
                                   "peak_used_in_bytes": 17432560,
                                   "used_in_bytes": 54352
                               },
                               "young": {
                                   "max_in_bytes": 139591680,
                                   "peak_max_in_bytes": 139591680,
                                   "peak_used_in_bytes": 139591680,
                                   "used_in_bytes": 111558256
                               }
                           }
                       },
                       "threads": {
                           "count": 29,
                           "peak_count": 43
                       },
                       "timestamp": 1441736481497,
                       "uptime_in_millis": 949698289
                   },
                   "name": "iad1esmst0vz114",
                   "network": {
                       "tcp": {
                           "active_opens": 197,
                           "attempt_fails": 1,
                           "curr_estab": 313,
                           "estab_resets": 0,
                           "in_errs": 0,
                           "in_segs": 2926157,
                           "out_rsts": 1,
                           "out_segs": 2924584,
                           "passive_opens": 1271,
                           "retrans_segs": 105
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
                           0.0,
                           0.0,
                           0.0
                       ],
                       "mem": {
                           "actual_free_in_bytes": 391561216,
                           "actual_used_in_bytes": 682180608,
                           "free_in_bytes": 363900928,
                           "free_percent": 36,
                           "used_in_bytes": 709840896,
                           "used_percent": 63
                       },
                       "swap": {
                           "free_in_bytes": 2147483648,
                           "used_in_bytes": 0
                       },
                       "timestamp": 1441736481496,
                       "uptime_in_millis": 949718
                   },
                   "process": {
                       "cpu": {
                           "percent": 0,
                           "sys_in_millis": 549690,
                           "total_in_millis": 1218500,
                           "user_in_millis": 668810
                       },
                       "mem": {
                           "resident_in_bytes": 686649344,
                           "share_in_bytes": 16506880,
                           "total_virtual_in_bytes": 3068624896
                       },
                       "open_file_descriptors": 402,
                       "timestamp": 1441736481496
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
                           "completed": 1044430,
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
                           "completed": 1085,
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
                   "timestamp": 1441736481496,
                   "transport": {
                       "rx_count": 1900192,
                       "rx_size_in_bytes": 273630436,
                       "server_open": 156,
                       "tx_count": 1900191,
                       "tx_size_in_bytes": 149959766
                   },
                   "transport_address": "inet[/10.56.149.45:30121]"
               },
               "kFLxmPa-QIegWZdC2oJKNA": {
                   "attributes": {
                       "data": "false",
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esapp1"
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
                   "host": "iad1esapp1vz114",
                   "http": {
                       "current_open": 1,
                       "total_opened": 1063
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
                       "inet[/10.56.149.44:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 39,
                               "total_capacity_in_bytes": 7418098,
                               "used_in_bytes": 7418098
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
                                   "collection_time_in_millis": 38
                               },
                               "young": {
                                   "collection_count": 53,
                                   "collection_time_in_millis": 456
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 1056309248,
                           "heap_max_in_bytes": 1056309248,
                           "heap_used_in_bytes": 114727880,
                           "heap_used_percent": 10,
                           "non_heap_committed_in_bytes": 47235072,
                           "non_heap_used_in_bytes": 46575096,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 899284992,
                                   "peak_max_in_bytes": 899284992,
                                   "peak_used_in_bytes": 23220648,
                                   "used_in_bytes": 23220648
                               },
                               "survivor": {
                                   "max_in_bytes": 17432576,
                                   "peak_max_in_bytes": 17432576,
                                   "peak_used_in_bytes": 17432560,
                                   "used_in_bytes": 42384
                               },
                               "young": {
                                   "max_in_bytes": 139591680,
                                   "peak_max_in_bytes": 139591680,
                                   "peak_used_in_bytes": 139591680,
                                   "used_in_bytes": 91464848
                               }
                           }
                       },
                       "threads": {
                           "count": 34,
                           "peak_count": 42
                       },
                       "timestamp": 1441736480982,
                       "uptime_in_millis": 949697799
                   },
                   "name": "iad1esapp1vz114",
                   "network": {
                       "tcp": {
                           "active_opens": 166,
                           "attempt_fails": 0,
                           "curr_estab": 315,
                           "estab_resets": 0,
                           "in_errs": 2,
                           "in_segs": 2929300,
                           "out_rsts": 217,
                           "out_segs": 2927517,
                           "passive_opens": 1257,
                           "retrans_segs": 224
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
                           0.05,
                           0.03,
                           0.0
                       ],
                       "mem": {
                           "actual_free_in_bytes": 854319104,
                           "actual_used_in_bytes": 1293164544,
                           "free_in_bytes": 775475200,
                           "free_percent": 39,
                           "used_in_bytes": 1372008448,
                           "used_percent": 60
                       },
                       "swap": {
                           "free_in_bytes": 1073741824,
                           "used_in_bytes": 0
                       },
                       "timestamp": 1441736480981,
                       "uptime_in_millis": 949718
                   },
                   "process": {
                       "cpu": {
                           "percent": 0,
                           "sys_in_millis": 754200,
                           "total_in_millis": 1587070,
                           "user_in_millis": 832870
                       },
                       "mem": {
                           "resident_in_bytes": 1293377536,
                           "share_in_bytes": 21020672,
                           "total_virtual_in_bytes": 3612368896
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
                           "completed": 1044353,
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
                           "completed": 1086,
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
                   "timestamp": 1441736480981,
                   "transport": {
                       "rx_count": 1900444,
                       "rx_size_in_bytes": 275234728,
                       "server_open": 156,
                       "tx_count": 1900443,
                       "tx_size_in_bytes": 149582724
                   },
                   "transport_address": "inet[/10.56.149.44:30121]"
               },
               "nTTBnF7HRDuJb3vfMNtv8A": {
                   "attributes": {
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esdn7"
                   },
                   "breakers": {
                       "fielddata": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "74.2mb",
                           "limit_size_in_bytes": 77856768,
                           "overhead": 1.03,
                           "tripped": 0
                       },
                       "parent": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "86.6mb",
                           "limit_size_in_bytes": 90832896,
                           "overhead": 1.0,
                           "tripped": 0
                       },
                       "request": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "49.5mb",
                           "limit_size_in_bytes": 51904512,
                           "overhead": 1.0,
                           "tripped": 0
                       }
                   },
                   "fs": {
                       "data": [
                           {
                               "available_in_bytes": 2043478016,
                               "dev": "/dev/simfs",
                               "free_in_bytes": 2043478016,
                               "mount": "/data0",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total_in_bytes": 2046640128,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736481722,
                       "total": {
                           "available_in_bytes": 2043478016,
                           "free_in_bytes": 2043478016,
                           "total_in_bytes": 2046640128
                       }
                   },
                   "host": "iad1esdn7vz21",
                   "http": {
                       "current_open": 0,
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
                       "inet[/10.56.148.12:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 32,
                               "total_capacity_in_bytes": 7079788,
                               "used_in_bytes": 7079788
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
                                   "collection_time_in_millis": 26
                               },
                               "young": {
                                   "collection_count": 207,
                                   "collection_time_in_millis": 567
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 129761280,
                           "heap_max_in_bytes": 129761280,
                           "heap_used_in_bytes": 31771616,
                           "heap_used_percent": 24,
                           "non_heap_committed_in_bytes": 46931968,
                           "non_heap_used_in_bytes": 46148840,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 89522176,
                                   "peak_max_in_bytes": 89522176,
                                   "peak_used_in_bytes": 16548872,
                                   "used_in_bytes": 14218368
                               },
                               "survivor": {
                                   "max_in_bytes": 4456448,
                                   "peak_max_in_bytes": 4456448,
                                   "peak_used_in_bytes": 4456448,
                                   "used_in_bytes": 8288
                               },
                               "young": {
                                   "max_in_bytes": 35782656,
                                   "peak_max_in_bytes": 35782656,
                                   "peak_used_in_bytes": 35782656,
                                   "used_in_bytes": 17544960
                               }
                           }
                       },
                       "threads": {
                           "count": 29,
                           "peak_count": 36
                       },
                       "timestamp": 1441736481721,
                       "uptime_in_millis": 949698527
                   },
                   "name": "iad1esdn7vz21",
                   "network": {
                       "tcp": {
                           "active_opens": 165,
                           "attempt_fails": 0,
                           "curr_estab": 313,
                           "estab_resets": 0,
                           "in_errs": 1,
                           "in_segs": 2987148,
                           "out_rsts": 1,
                           "out_segs": 2953844,
                           "passive_opens": 1227,
                           "retrans_segs": 282
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
                           0.0,
                           0.0,
                           0.0
                       ],
                       "mem": {
                           "actual_free_in_bytes": 20168704,
                           "actual_used_in_bytes": 248266752,
                           "free_in_bytes": 11051008,
                           "free_percent": 7,
                           "used_in_bytes": 257384448,
                           "used_percent": 92
                       },
                       "swap": {
                           "free_in_bytes": 1033236480,
                           "used_in_bytes": 40505344
                       },
                       "timestamp": 1441736481721,
                       "uptime_in_millis": 949718
                   },
                   "process": {
                       "cpu": {
                           "percent": 0,
                           "sys_in_millis": 728400,
                           "total_in_millis": 1524700,
                           "user_in_millis": 796300
                       },
                       "mem": {
                           "resident_in_bytes": 254992384,
                           "share_in_bytes": 15065088,
                           "total_virtual_in_bytes": 2649845760
                       },
                       "open_file_descriptors": 402,
                       "timestamp": 1441736481721
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
                           "completed": 1044384,
                           "largest": 6,
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
                           "completed": 1061,
                           "largest": 1,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 1
                       },
                       "management": {
                           "active": 1,
                           "completed": 31833,
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
                   "timestamp": 1441736481719,
                   "transport": {
                       "rx_count": 1931719,
                       "rx_size_in_bytes": 277294563,
                       "server_open": 156,
                       "tx_count": 1931718,
                       "tx_size_in_bytes": 160582279
                   },
                   "transport_address": "inet[/10.56.148.12:30121]"
               },
               "w66J0I4ITOWufukPBbXCZQ": {
                   "attributes": {
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esdn0"
                   },
                   "breakers": {
                       "fielddata": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "74.2mb",
                           "limit_size_in_bytes": 77856768,
                           "overhead": 1.03,
                           "tripped": 0
                       },
                       "parent": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "86.6mb",
                           "limit_size_in_bytes": 90832896,
                           "overhead": 1.0,
                           "tripped": 0
                       },
                       "request": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "49.5mb",
                           "limit_size_in_bytes": 51904512,
                           "overhead": 1.0,
                           "tripped": 0
                       }
                   },
                   "fs": {
                       "data": [
                           {
                               "available_in_bytes": 2043478016,
                               "dev": "/dev/simfs",
                               "free_in_bytes": 2043478016,
                               "mount": "/data0",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total_in_bytes": 2046640128,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736481426,
                       "total": {
                           "available_in_bytes": 2043478016,
                           "free_in_bytes": 2043478016,
                           "total_in_bytes": 2046640128
                       }
                   },
                   "host": "iad1esdn0vz16",
                   "http": {
                       "current_open": 0,
                       "total_opened": 0
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
                       "inet[/10.56.145.94:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 20,
                               "total_capacity_in_bytes": 4980736,
                               "used_in_bytes": 4980736
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
                                   "collection_time_in_millis": 11
                               },
                               "young": {
                                   "collection_count": 4,
                                   "collection_time_in_millis": 51
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 129761280,
                           "heap_max_in_bytes": 129761280,
                           "heap_used_in_bytes": 32607408,
                           "heap_used_percent": 25,
                           "non_heap_committed_in_bytes": 43655168,
                           "non_heap_used_in_bytes": 42907472,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 89522176,
                                   "peak_max_in_bytes": 89522176,
                                   "peak_used_in_bytes": 15662224,
                                   "used_in_bytes": 10916784
                               },
                               "survivor": {
                                   "max_in_bytes": 4456448,
                                   "peak_max_in_bytes": 4456448,
                                   "peak_used_in_bytes": 4456448,
                                   "used_in_bytes": 4456448
                               },
                               "young": {
                                   "max_in_bytes": 35782656,
                                   "peak_max_in_bytes": 35782656,
                                   "peak_used_in_bytes": 35782656,
                                   "used_in_bytes": 17234176
                               }
                           }
                       },
                       "threads": {
                           "count": 28,
                           "peak_count": 36
                       },
                       "timestamp": 1441736481423,
                       "uptime_in_millis": 850171
                   },
                   "name": "iad1esdn0vz16",
                   "network": {
                       "tcp": {
                           "active_opens": 159,
                           "attempt_fails": 0,
                           "curr_estab": 313,
                           "estab_resets": 0,
                           "in_errs": 1,
                           "in_segs": 4379,
                           "out_rsts": 0,
                           "out_segs": 3931,
                           "passive_opens": 158,
                           "retrans_segs": 30
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
                           0.0,
                           0.0,
                           0.0
                       ],
                       "mem": {
                           "actual_free_in_bytes": 26841088,
                           "actual_used_in_bytes": 241594368,
                           "free_in_bytes": 17072128,
                           "free_percent": 9,
                           "used_in_bytes": 251363328,
                           "used_percent": 90
                       },
                       "swap": {
                           "free_in_bytes": 1056591872,
                           "used_in_bytes": 17149952
                       },
                       "timestamp": 1441736481423,
                       "uptime_in_millis": 864
                   },
                   "process": {
                       "cpu": {
                           "percent": 0,
                           "sys_in_millis": 870,
                           "total_in_millis": 7590,
                           "user_in_millis": 6720
                       },
                       "mem": {
                           "resident_in_bytes": 248532992,
                           "share_in_bytes": 15982592,
                           "total_virtual_in_bytes": 2647474176
                       },
                       "open_file_descriptors": 402,
                       "timestamp": 1441736481423
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
                           "completed": 951,
                           "largest": 6,
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
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "management": {
                           "active": 1,
                           "completed": 32,
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
                   "timestamp": 1441736481415,
                   "transport": {
                       "rx_count": 1727,
                       "rx_size_in_bytes": 254968,
                       "server_open": 156,
                       "tx_count": 1726,
                       "tx_size_in_bytes": 151961
                   },
                   "transport_address": "inet[/10.56.145.94:30121]"
               },
               "wtYhqzpASYqyO_Q6geHl6g": {
                   "attributes": {
                       "master": "false",
                       "max_local_storage_nodes": "1",
                       "phy_host": "iad1esdn0"
                   },
                   "breakers": {
                       "fielddata": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "74.2mb",
                           "limit_size_in_bytes": 77856768,
                           "overhead": 1.03,
                           "tripped": 0
                       },
                       "parent": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "86.6mb",
                           "limit_size_in_bytes": 90832896,
                           "overhead": 1.0,
                           "tripped": 0
                       },
                       "request": {
                           "estimated_size": "0b",
                           "estimated_size_in_bytes": 0,
                           "limit_size": "49.5mb",
                           "limit_size_in_bytes": 51904512,
                           "overhead": 1.0,
                           "tripped": 0
                       }
                   },
                   "fs": {
                       "data": [
                           {
                               "available_in_bytes": 2043478016,
                               "dev": "/dev/simfs",
                               "free_in_bytes": 2043478016,
                               "mount": "/data0",
                               "path": "/data0/elasticsearch/17fa73756374a77594d094d34d4e87e0/nodes/0",
                               "total_in_bytes": 2046640128,
                               "type": "simfs"
                           }
                       ],
                       "timestamp": 1441736480994,
                       "total": {
                           "available_in_bytes": 2043478016,
                           "free_in_bytes": 2043478016,
                           "total_in_bytes": 2046640128
                       }
                   },
                   "host": "iad1esdn0vz17",
                   "http": {
                       "current_open": 0,
                       "total_opened": 0
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
                       "inet[/10.56.145.95:30121]",
                       "NONE"
                   ],
                   "jvm": {
                       "buffer_pools": {
                           "direct": {
                               "count": 19,
                               "total_capacity_in_bytes": 4456448,
                               "used_in_bytes": 4456448
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
                                   "collection_time_in_millis": 18
                               },
                               "young": {
                                   "collection_count": 4,
                                   "collection_time_in_millis": 73
                               }
                           }
                       },
                       "mem": {
                           "heap_committed_in_bytes": 129761280,
                           "heap_max_in_bytes": 129761280,
                           "heap_used_in_bytes": 29725280,
                           "heap_used_percent": 22,
                           "non_heap_committed_in_bytes": 42344448,
                           "non_heap_used_in_bytes": 41671912,
                           "pools": {
                               "old": {
                                   "max_in_bytes": 89522176,
                                   "peak_max_in_bytes": 89522176,
                                   "peak_used_in_bytes": 16364072,
                                   "used_in_bytes": 14584040
                               },
                               "survivor": {
                                   "max_in_bytes": 4456448,
                                   "peak_max_in_bytes": 4456448,
                                   "peak_used_in_bytes": 4456448,
                                   "used_in_bytes": 4456448
                               },
                               "young": {
                                   "max_in_bytes": 35782656,
                                   "peak_max_in_bytes": 35782656,
                                   "peak_used_in_bytes": 35782656,
                                   "used_in_bytes": 10684792
                               }
                           }
                       },
                       "threads": {
                           "count": 31,
                           "peak_count": 35
                       },
                       "timestamp": 1441736480992,
                       "uptime_in_millis": 44675
                   },
                   "name": "iad1esdn0vz17",
                   "network": {
                       "tcp": {
                           "active_opens": 159,
                           "attempt_fails": 0,
                           "curr_estab": 313,
                           "estab_resets": 0,
                           "in_errs": 0,
                           "in_segs": 1280,
                           "out_rsts": 0,
                           "out_segs": 1113,
                           "passive_opens": 157,
                           "retrans_segs": 20
                       }
                   },
                   "os": {
                       "cpu": {
                           "idle": 96,
                           "stolen": 0,
                           "sys": 0,
                           "usage": 2,
                           "user": 2
                       },
                       "load_average": [
                           0.03,
                           0.01,
                           0.0
                       ],
                       "mem": {
                           "actual_free_in_bytes": 20828160,
                           "actual_used_in_bytes": 247607296,
                           "free_in_bytes": 17694720,
                           "free_percent": 7,
                           "used_in_bytes": 250740736,
                           "used_percent": 92
                       },
                       "swap": {
                           "free_in_bytes": 1038741504,
                           "used_in_bytes": 35000320
                       },
                       "timestamp": 1441736480990,
                       "uptime_in_millis": 69
                   },
                   "process": {
                       "cpu": {
                           "percent": 6,
                           "sys_in_millis": 410,
                           "total_in_millis": 5060,
                           "user_in_millis": 4650
                       },
                       "mem": {
                           "resident_in_bytes": 258953216,
                           "share_in_bytes": 15413248,
                           "total_virtual_in_bytes": 2646421504
                       },
                       "open_file_descriptors": 402,
                       "timestamp": 1441736480991
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
                           "completed": 66,
                           "largest": 5,
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
                           "completed": 0,
                           "largest": 0,
                           "queue": 0,
                           "rejected": 0,
                           "threads": 0
                       },
                       "management": {
                           "active": 1,
                           "completed": 2,
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
                   "timestamp": 1441736480981,
                   "transport": {
                       "rx_count": 87,
                       "rx_size_in_bytes": 18727,
                       "server_open": 156,
                       "tx_count": 86,
                       "tx_size_in_bytes": 8724
                   },
                   "transport_address": "inet[/10.56.145.95:30121]"
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

