MongoDB Resources
=================

Get a list of collection names belonging to the given instance database
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/databases/<database_name>/collections/

Response:

.. code-block:: bash

   {
       "data": [
           "Collection1",
           "Collection2",
           "Collection3"
       ]
   }

Create a new collection in the specified instance database
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /mongodb/<instance_name>/databases/<database_name>/collections/

Request:

.. code-block:: bash

   {
       "name": "Name123",
       "shard_keys": [
           {
               "hashed": true,
               "key": "Key123"
           }
       ]
   }

Response:

.. code-block:: bash

   {
       "data": "Successfully added collection: 'Name123' to database: 'Database123'"
   }

Get details on a collection belonging to the given instance database
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/databases/<database_name>/collections/<collection_name>/

Response:

.. code-block:: bash

   {
       "data": {
           "count": 0,
           "indexSizes": {
               "_id_": 8176
           },
           "lastExtentSize": 8192,
           "nindexes": 1,
           "ns": "Database123.Collection1",
           "numExtents": 1,
           "ok": 1.0,
           "paddingFactor": 1.0,
           "primary": "90a85209de63519f0c04728a1bdb9313",
           "sharded": false,
           "size": 0,
           "storageSize": 8192,
           "systemFlags": 1,
           "totalIndexSize": 8176,
           "userFlags": 0
       }
   }

Get the compaction state of the specified instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/compaction/

Response:

.. code-block:: bash

   {
       "data": {
           "balancer_stopped_by_check": false,
           "shards": [
               {
                   "members": [
                       {
                           "finish": {
                               "$date": 1435767398910
                           },
                           "name": "sydclus2br2vz18.syd.objectrocket.com:31134",
                           "start": {
                               "$date": 1435767133858
                           },
                           "state": "compressed",
                           "updated": "2015-07-01 16:16:38.910703"
                       },
                       {
                           "finish": {
                               "$date": 1435768000703
                           },
                           "name": "sydclus2br1vz18.syd.objectrocket.com:31134",
                           "start": {
                               "$date": 1435767721868
                           },
                           "state": "compressed",
                           "updated": "2015-07-01 16:26:40.703653"
                       }
                   ],
                   "primary_at_stepdown_request_time": "sydclus2br0vz18.syd.objectrocket.com:31134",
                   "shardstr": "5db16d02db25b9673ff2f72440366df0/sydclus2br0vz18.syd.objectrocket.com:31134,sydclus2br1vz18.syd.objectrocket.com:31134,sydclus2br2vz18.syd.objectrocket.com:31134",
                   "start": {
                       "$date": 1435767109046
                   },
                   "state": "stepdown_requested",
                   "updated": "2015-08-27 21:27:03.311787",
                   "updated_ts": 1440710823
               },
               {
                   "members": [
                       {
                           "finish": {
                               "$date": 1435870302785
                           },
                           "name": "sydclus1br1vz10.syd.objectrocket.com:31166",
                           "start": {
                               "$date": 1435869429763
                           },
                           "state": "compressed",
                           "updated": "2015-07-02 20:51:42.785514"
                       },
                       {
                           "finish": {
                               "$date": 1435873901764
                           },
                           "name": "sydclus1br0vz10.syd.objectrocket.com:31166",
                           "start": {
                               "$date": 1435870940030
                           },
                           "state": "compressed",
                           "updated": "2015-07-02 21:51:41.764637"
                       }
                   ],
                   "primary_at_stepdown_request_time": "sydclus1br2vz10.syd.objectrocket.com:31166",
                   "shardstr": "90a85209de63519f0c04728a1bdb9313/sydclus1br0vz10.syd.objectrocket.com:31166,sydclus1br1vz10.syd.objectrocket.com:31166,sydclus1br2vz10.syd.objectrocket.com:31166",
                   "start": {
                       "$date": 1435869401045
                   },
                   "state": "awaiting_stepdown_request",
                   "updated": "2015-07-02 22:06:44.482812",
                   "updated_ts": 1435874804
               }
           ],
           "start": {
               "$date": 1435767108256
           },
           "state": "awaiting_stepdown",
           "updated": "2015-08-27 21:27:03.311798"
       }
   }

Schedule the specified instance for compaction
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /mongodb/<instance_name>/compaction/

Response:

.. code-block:: bash

   {
       "data": "Success"
   }

Get a list of databases and their statistics belonging to the given
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/databases/

Response:

.. code-block:: bash

   {
       "data": [
           {
               "average_object_size_in_bytes": 67.0,
               "collection_count": 3,
               "data_size_in_bytes": 676,
               "file_size_in_bytes": 50331648,
               "index_count": 3,
               "index_size_in_bytes": 24528,
               "name": "Database123",
               "object_count": 10,
               "storage_size_in_bytes": 36864
           },
           {
               "average_object_size_in_bytes": 0.0,
               "collection_count": 0,
               "data_size_in_bytes": 0,
               "file_size_in_bytes": 0,
               "index_count": 0,
               "index_size_in_bytes": 0,
               "name": "database1",
               "object_count": 0,
               "storage_size_in_bytes": 0
           },
           {
               "average_object_size_in_bytes": 62.0,
               "collection_count": 3,
               "data_size_in_bytes": 2700,
               "file_size_in_bytes": 50331648,
               "index_count": 10,
               "index_size_in_bytes": 81760,
               "name": "db1",
               "object_count": 43,
               "storage_size_in_bytes": 36864
           },
           {
               "average_object_size_in_bytes": 0.0,
               "collection_count": 0,
               "data_size_in_bytes": 0,
               "file_size_in_bytes": 0,
               "index_count": 0,
               "index_size_in_bytes": 0,
               "name": "test",
               "object_count": 0,
               "storage_size_in_bytes": 0
           }
       ]
   }

Create a database and user on the specified instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /mongodb/<instance_name>/databases/

Request/Response:

.. code-block:: bash

   $ ERROR

Get details on a database belonging to the given instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/databases/<database_name>/

Response:

.. code-block:: bash

   {
       "data": {
           "avgObjSize": 67.0,
           "dataSize": 676,
           "extentFreeList": {
               "num": 0,
               "totalSize": 0
           },
           "fileSize": 50331648,
           "indexSize": 24528,
           "indexes": 3,
           "nsSize": 16777216,
           "numExtents": 5,
           "objects": 10,
           "ok": 1.0,
           "raw": {
               "90a85209de63519f0c04728a1bdb9313/sydclus1br0vz10.syd.objectrocket.com:31166,sydclus1br1vz10.syd.objectrocket.com:31166,sydclus1br2vz10.syd.objectrocket.com:31166": {
                   "avgObjSize": 67.6,
                   "collections": 5,
                   "dataFileVersion": {
                       "major": 4,
                       "minor": 5
                   },
                   "dataSize": 676,
                   "db": "Database123",
                   "fileSize": 50331648,
                   "indexSize": 24528,
                   "indexes": 3,
                   "nsSizeMB": 16,
                   "numExtents": 5,
                   "objects": 10,
                   "ok": 1.0,
                   "storageSize": 36864
               }
           },
           "storageSize": 36864
       }
   }

Delete a database from the specified instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   DELETE /mongodb/<instance_name>/databases/<database_name>/

Response:

.. code-block:: bash

   {
       "data": "Successfully deleted Database \"Database123\" from Instance \"Test123\"."
   }

Get opcounters per second for the given instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/opcounters/persecond/

.. note::

   Operation may take 30+ seconds to complete (adjust timeout settings if need be).

Response:

.. code-block:: bash

   {
       "data": [
           {
               "5db16d02db25b9673ff2f72440366df0": {
                   "sydclus2br0vz18.syd.objectrocket.com:31134": {
                       "command": 81,
                       "delete": 0,
                       "getmore": 6,
                       "insert": 0,
                       "query": 0,
                       "update": 0
                   },
                   "sydclus2br1vz18.syd.objectrocket.com:31134": {
                       "command": 62,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus2br2vz18.syd.objectrocket.com:31134": {
                       "command": 57,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 0,
                       "update": 0
                   }
               },
               "90a85209de63519f0c04728a1bdb9313": {
                   "sydclus1br0vz10.syd.objectrocket.com:31166": {
                       "command": 71,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus1br1vz10.syd.objectrocket.com:31166": {
                       "command": 77,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus1br2vz10.syd.objectrocket.com:31166": {
                       "command": 83,
                       "delete": 0,
                       "getmore": 8,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   }
               },
               "fc0c163bd79c4de0b3d5127ec9e5156d": {
                   "sydclus2br0vz28.syd.objectrocket.com:32795": {
                       "command": 43,
                       "delete": 0,
                       "getmore": 8,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus2br1vz28.syd.objectrocket.com:32795": {
                       "command": 40,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus2br2vz28.syd.objectrocket.com:32795": {
                       "command": 41,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   }
               }
           },
           {
               "5db16d02db25b9673ff2f72440366df0": {
                   "sydclus2br0vz18.syd.objectrocket.com:31134": {
                       "command": 81,
                       "delete": 0,
                       "getmore": 6,
                       "insert": 0,
                       "query": 0,
                       "update": 0
                   },
                   "sydclus2br1vz18.syd.objectrocket.com:31134": {
                       "command": 62,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus2br2vz18.syd.objectrocket.com:31134": {
                       "command": 57,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 0,
                       "update": 0
                   }
               },
               "90a85209de63519f0c04728a1bdb9313": {
                   "sydclus1br0vz10.syd.objectrocket.com:31166": {
                       "command": 71,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus1br1vz10.syd.objectrocket.com:31166": {
                       "command": 77,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus1br2vz10.syd.objectrocket.com:31166": {
                       "command": 83,
                       "delete": 0,
                       "getmore": 8,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   }
               },
               "fc0c163bd79c4de0b3d5127ec9e5156d": {
                   "sydclus2br0vz28.syd.objectrocket.com:32795": {
                       "command": 43,
                       "delete": 0,
                       "getmore": 8,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus2br1vz28.syd.objectrocket.com:32795": {
                       "command": 40,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus2br2vz28.syd.objectrocket.com:32795": {
                       "command": 41,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   }
               }
           },
           {
               "5db16d02db25b9673ff2f72440366df0": {
                   "sydclus2br0vz18.syd.objectrocket.com:31134": {
                       "command": 81,
                       "delete": 0,
                       "getmore": 6,
                       "insert": 0,
                       "query": 0,
                       "update": 0
                   },
                   "sydclus2br1vz18.syd.objectrocket.com:31134": {
                       "command": 62,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus2br2vz18.syd.objectrocket.com:31134": {
                       "command": 57,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 0,
                       "update": 0
                   }
               },
               "90a85209de63519f0c04728a1bdb9313": {
                   "sydclus1br0vz10.syd.objectrocket.com:31166": {
                       "command": 71,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus1br1vz10.syd.objectrocket.com:31166": {
                       "command": 77,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus1br2vz10.syd.objectrocket.com:31166": {
                       "command": 83,
                       "delete": 0,
                       "getmore": 8,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   }
               },
               "fc0c163bd79c4de0b3d5127ec9e5156d": {
                   "sydclus2br0vz28.syd.objectrocket.com:32795": {
                       "command": 43,
                       "delete": 0,
                       "getmore": 8,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus2br1vz28.syd.objectrocket.com:32795": {
                       "command": 40,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   },
                   "sydclus2br2vz28.syd.objectrocket.com:32795": {
                       "command": 41,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 0,
                       "query": 7,
                       "update": 0
                   }
               }
           }
       ]
   }

Get opcounters for the given instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/opcounters/

Response:

.. code-block:: bash

   {
       "data": [
           {
               "5db16d02db25b9673ff2f72440366df0": {
                   "sydclus2br0vz18.syd.objectrocket.com:31134": {
                       "command": 47303591,
                       "delete": 0,
                       "getmore": 2455092,
                       "insert": 22,
                       "query": 1169077,
                       "update": 52
                   },
                   "sydclus2br1vz18.syd.objectrocket.com:31134": {
                       "command": 11198942,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 1,
                       "query": 363001,
                       "update": 0
                   },
                   "sydclus2br2vz18.syd.objectrocket.com:31134": {
                       "command": 11199560,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 1,
                       "query": 362131,
                       "update": 0
                   }
               },
               "90a85209de63519f0c04728a1bdb9313": {
                   "sydclus1br0vz10.syd.objectrocket.com:31166": {
                       "command": 10905633,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 1,
                       "query": 357189,
                       "update": 0
                   },
                   "sydclus1br1vz10.syd.objectrocket.com:31166": {
                       "command": 10907327,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 1,
                       "query": 356649,
                       "update": 0
                   },
                   "sydclus1br2vz10.syd.objectrocket.com:31166": {
                       "command": 67116108,
                       "delete": 0,
                       "getmore": 17865167,
                       "insert": 2,
                       "query": 1834450,
                       "update": 32
                   }
               }
           },
           {
               "5db16d02db25b9673ff2f72440366df0": {
                   "sydclus2br0vz18.syd.objectrocket.com:31134": {
                       "command": 47303591,
                       "delete": 0,
                       "getmore": 2455092,
                       "insert": 22,
                       "query": 1169077,
                       "update": 52
                   },
                   "sydclus2br1vz18.syd.objectrocket.com:31134": {
                       "command": 11198942,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 1,
                       "query": 363001,
                       "update": 0
                   },
                   "sydclus2br2vz18.syd.objectrocket.com:31134": {
                       "command": 11199560,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 1,
                       "query": 362131,
                       "update": 0
                   }
               },
               "90a85209de63519f0c04728a1bdb9313": {
                   "sydclus1br0vz10.syd.objectrocket.com:31166": {
                       "command": 10905633,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 1,
                       "query": 357189,
                       "update": 0
                   },
                   "sydclus1br1vz10.syd.objectrocket.com:31166": {
                       "command": 10907327,
                       "delete": 0,
                       "getmore": 0,
                       "insert": 1,
                       "query": 356649,
                       "update": 0
                   },
                   "sydclus1br2vz10.syd.objectrocket.com:31166": {
                       "command": 67116108,
                       "delete": 0,
                       "getmore": 17865167,
                       "insert": 2,
                       "query": 1834450,
                       "update": 32
                   }
               }
           }
       ]
   }

Get a list of replica sets belonging to the given instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/replicasets/

Response:

.. code-block:: bash

   {
       "data": [
           {
               "5db16d02db25b9673ff2f72440366df0": [
                   "sydclus2br0vz18.syd.objectrocket.com:31134",
                   "sydclus2br1vz18.syd.objectrocket.com:31134",
                   "sydclus2br2vz18.syd.objectrocket.com:31134"
               ]
           },
           {
               "90a85209de63519f0c04728a1bdb9313": [
                   "sydclus1br0vz10.syd.objectrocket.com:31166",
                   "sydclus1br1vz10.syd.objectrocket.com:31166",
                   "sydclus1br2vz10.syd.objectrocket.com:31166"
               ]
           }
       ]
   }

Get a list of shards belonging to the given instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/shards/

Response:

.. code-block:: bash

   {
       "data": [
           {
               "id": "5db16d02db25b9673ff2f72440366df0",
               "name": "5db16d02db25b9673ff2f72440366df0",
               "plan": 5,
               "shardstr": "5db16d02db25b9673ff2f72440366df0/sydclus2br0vz18.syd.objectrocket.com:31134,sydclus2br1vz18.syd.objectrocket.com:31134,sydclus2br2vz18.syd.objectrocket.com:31134",
               "zone": "AP-Sydney"
           },
           {
               "id": "90a85209de63519f0c04728a1bdb9313",
               "name": "90a85209de63519f0c04728a1bdb9313",
               "plan": 5,
               "shardstr": "90a85209de63519f0c04728a1bdb9313/sydclus1br0vz10.syd.objectrocket.com:31166,sydclus1br1vz10.syd.objectrocket.com:31166,sydclus1br2vz10.syd.objectrocket.com:31166",
               "zone": "AP-Sydney"
           }
       ]
   }

Add a shard to the given instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /mongodb/<instance_name>/shards/

Response:

.. code-block:: bash

   {
       "data": [
           {
               "id": "5db16d02db25b9673ff2f72440366df0",
               "name": "5db16d02db25b9673ff2f72440366df0",
               "plan": 5,
               "shardstr": "5db16d02db25b9673ff2f72440366df0/sydclus2br0vz18.syd.objectrocket.com:31134,sydclus2br1vz18.syd.objectrocket.com:31134,sydclus2br2vz18.syd.objectrocket.com:31134",
               "zone": "AP-Sydney"
           },
           {
               "id": "90a85209de63519f0c04728a1bdb9313",
               "name": "90a85209de63519f0c04728a1bdb9313",
               "plan": 5,
               "shardstr": "90a85209de63519f0c04728a1bdb9313/sydclus1br0vz10.syd.objectrocket.com:31166,sydclus1br1vz10.syd.objectrocket.com:31166,sydclus1br2vz10.syd.objectrocket.com:31166",
               "zone": "AP-Sydney"
           },
           {
               "id": "fc0c163bd79c4de0b3d5127ec9e5156d",
               "name": "fc0c163bd79c4de0b3d5127ec9e5156d",
               "plan": 5,
               "shardstr": "fc0c163bd79c4de0b3d5127ec9e5156d/sydclus2br0vz28.syd.objectrocket.com:32795,sydclus2br1vz28.syd.objectrocket.com:32795,sydclus2br2vz28.syd.objectrocket.com:32795",
               "zone": "AP-Sydney"
           }
       ]
   }

Get space usage statistics from the specified instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/spaceusage/

Response:

.. code-block:: bash

   {
       "data": {
           "maximum_capacity": 10737418240,
           "percentages": {
               "data": 0.00014640390872955322,
               "index": 0.0015990436077117918,
               "ns": 0.9375,
               "remaining": 89.09790970385075,
               "storage": 9.962844848632812
           },
           "total_data_size": 15720,
           "total_file_size": 1308098560,
           "total_index_size": 171696,
           "total_ns_size": 100663296,
           "total_storage_size": 1069752320
       }
   }

Get the current stepdown window configuration of the specified instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/stepdown/

Response:

.. code-block:: bash

   {
       "data": {
           "enabled": false,
           "end": "",
           "ran_in_window": false,
           "requestor": "autocompact",
           "scheduled": true,
           "start": "",
           "weekly": false
       }
   }

Update the stepdown window configuration of the specified instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /mongodb/<instance_name>/stepdown/

.. note::

   The **start** and **end** fields must be a floating point Unix timestamp specified in UTC.

Request:

.. code-block:: bash

   {
       "enabled": "True",
       "end": "1440716239",
       "scheduled": "True",
       "start": "1440715239",
       "weekly": "True"
   }

Response:

.. code-block:: bash

   {
       "data": {
           "enabled": true,
           "end": {
               "$date": 1440715240000
           },
           "ran_in_window": false,
           "requestor": "autocompact",
           "scheduled": true,
           "start": {
               "$date": 1440715239000
           },
           "weekly": true
       }
   }

Get details on backups
~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/backups/

Response:

.. code-block:: bash

   {
       "data": [
           {
               "_id": {
                   "$oid": "55deb5eb5559613b75119698"
               },
               "backup_directory": "/backups/55410c7f5b335278490a5be8/20150827_0001",
               "backup_host": "sydbackups0.syd.objectrocket.com",
               "error_msg": "Successful, completed in 61 seconds",
               "filenames": {
                   "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150827_0001.tgz",
                   "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150827_0001.tgz",
                   "config_server": "config_35023_20150827_0001.tgz"
               },
               "instance_id": {
                   "$oid": "55410c7f5b335278490a5be8"
               },
               "instance_name": "test123",
               "instance_type": "mongodb_sharded",
               "login": "donovan@heydonovan.io",
               "port": 35023,
               "timestamp": {
                   "$date": 1440633661943
               },
               "timestamp_formatted": "2015/08/27 00:01:01"
           },
           {
               "_id": {
                   "$oid": "55dd6a5c555961145f1272c7"
               },
               "backup_directory": "/backups/55410c7f5b335278490a5be8/20150826_0026",
               "backup_host": "sydbackups0.syd.objectrocket.com",
               "error_msg": "Successful, completed in 60 seconds",
               "filenames": {
                   "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150826_0026.tgz",
                   "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150826_0026.tgz",
                   "config_server": "config_35023_20150826_0026.tgz"
               },
               "instance_id": {
                   "$oid": "55410c7f5b335278490a5be8"
               },
               "instance_name": "test123",
               "instance_type": "mongodb_sharded",
               "login": "donovan@heydonovan.io",
               "port": 35023,
               "timestamp": {
                   "$date": 1440548783512
               },
               "timestamp_formatted": "2015/08/26 00:26:23"
           },
           {
               "_id": {
                   "$oid": "55dc14435559616003a3dc09"
               },
               "backup_directory": "/backups/55410c7f5b335278490a5be8/20150825_0006",
               "backup_host": "sydbackups0.syd.objectrocket.com",
               "error_msg": "Successful, completed in 60 seconds",
               "filenames": {
                   "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150825_0006.tgz",
                   "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150825_0006.tgz",
                   "config_server": "config_35023_20150825_0006.tgz"
               },
               "instance_id": {
                   "$oid": "55410c7f5b335278490a5be8"
               },
               "instance_name": "test123",
               "instance_type": "mongodb_sharded",
               "login": "donovan@heydonovan.io",
               "port": 35023,
               "timestamp": {
                   "$date": 1440461206147
               },
               "timestamp_formatted": "2015/08/25 00:06:46"
           },
           {
               "_id": {
                   "$oid": "55dac762555961378eb382c6"
               },
               "backup_directory": "/backups/55410c7f5b335278490a5be8/20150824_0026",
               "backup_host": "sydbackups0.syd.objectrocket.com",
               "error_msg": "Successful, completed in 61 seconds",
               "filenames": {
                   "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150824_0026.tgz",
                   "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150824_0026.tgz",
                   "config_server": "config_35023_20150824_0026.tgz"
               },
               "instance_id": {
                   "$oid": "55410c7f5b335278490a5be8"
               },
               "instance_name": "test123",
               "instance_type": "mongodb_sharded",
               "login": "donovan@heydonovan.io",
               "port": 35023,
               "timestamp": {
                   "$date": 1440375989115
               },
               "timestamp_formatted": "2015/08/24 00:26:29"
           },
           {
               "_id": {
                   "$oid": "55d975bc555961096b58f48e"
               },
               "backup_directory": "/backups/55410c7f5b335278490a5be8/20150823_0025",
               "backup_host": "sydbackups0.syd.objectrocket.com",
               "error_msg": "Successful, completed in 61 seconds",
               "filenames": {
                   "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150823_0025.tgz",
                   "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150823_0025.tgz",
                   "config_server": "config_35023_20150823_0025.tgz"
               },
               "instance_id": {
                   "$oid": "55410c7f5b335278490a5be8"
               },
               "instance_name": "test123",
               "instance_type": "mongodb_sharded",
               "login": "donovan@heydonovan.io",
               "port": 35023,
               "timestamp": {
                   "$date": 1440289550658
               },
               "timestamp_formatted": "2015/08/23 00:25:50"
           },
           {
               "_id": {
                   "$oid": "55d81e9355596154582cb22d"
               },
               "backup_directory": "/backups/55410c7f5b335278490a5be8/20150822_0001",
               "backup_host": "sydbackups0.syd.objectrocket.com",
               "error_msg": "Successful, completed in 61 seconds",
               "filenames": {
                   "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150822_0001.tgz",
                   "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150822_0001.tgz",
                   "config_server": "config_35023_20150822_0001.tgz"
               },
               "instance_id": {
                   "$oid": "55410c7f5b335278490a5be8"
               },
               "instance_name": "test123",
               "instance_type": "mongodb_sharded",
               "login": "donovan@heydonovan.io",
               "port": 35023,
               "timestamp": {
                   "$date": 1440201702535
               },
               "timestamp_formatted": "2015/08/22 00:01:42"
           },
           {
               "_id": {
                   "$oid": "55d6d2cc5559612d0a6568f8"
               },
               "backup_directory": "/backups/55410c7f5b335278490a5be8/20150821_0026",
               "backup_host": "sydbackups0.syd.objectrocket.com",
               "error_msg": "Successful, completed in 60 seconds",
               "filenames": {
                   "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150821_0026.tgz",
                   "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150821_0026.tgz",
                   "config_server": "config_35023_20150821_0026.tgz"
               },
               "instance_id": {
                   "$oid": "55410c7f5b335278490a5be8"
               },
               "instance_name": "test123",
               "instance_type": "mongodb_sharded",
               "login": "donovan@heydonovan.io",
               "port": 35023,
               "timestamp": {
                   "$date": 1440116767655
               },
               "timestamp_formatted": "2015/08/21 00:26:07"
           },
           {
               "_id": {
                   "$oid": "55d581485559617d7142b5bd"
               },
               "backup_directory": "/backups/55410c7f5b335278490a5be8/20150820_0026",
               "backup_host": "sydbackups0.syd.objectrocket.com",
               "error_msg": "Successful, completed in 61 seconds",
               "filenames": {
                   "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150820_0026.tgz",
                   "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150820_0026.tgz",
                   "config_server": "config_35023_20150820_0026.tgz"
               },
               "instance_id": {
                   "$oid": "55410c7f5b335278490a5be8"
               },
               "instance_name": "test123",
               "instance_type": "mongodb_sharded",
               "login": "donovan@heydonovan.io",
               "port": 35023,
               "timestamp": {
                   "$date": 1440030363417
               },
               "timestamp_formatted": "2015/08/20 00:26:03"
           },
           {
               "_id": {
                   "$oid": "55d42fd955596150431970e4"
               },
               "backup_directory": "/backups/55410c7f5b335278490a5be8/20150819_0026",
               "backup_host": "sydbackups0.syd.objectrocket.com",
               "error_msg": "Successful, completed in 61 seconds",
               "filenames": {
                   "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150819_0026.tgz",
                   "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150819_0026.tgz",
                   "config_server": "config_35023_20150819_0026.tgz"
               },
               "instance_id": {
                   "$oid": "55410c7f5b335278490a5be8"
               },
               "instance_name": "test123",
               "instance_type": "mongodb_sharded",
               "login": "donovan@heydonovan.io",
               "port": 35023,
               "timestamp": {
                   "$date": 1439943979791
               },
               "timestamp_formatted": "2015/08/19 00:26:19"
           },
           {
               "_id": {
                   "$oid": "55d2dd5355596121fdca8a0a"
               },
               "backup_directory": "/backups/55410c7f5b335278490a5be8/20150818_0021",
               "backup_host": "sydbackups0.syd.objectrocket.com",
               "error_msg": "Successful, completed in 60 seconds",
               "filenames": {
                   "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150818_0021.tgz",
                   "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150818_0021.tgz",
                   "config_server": "config_35023_20150818_0021.tgz"
               },
               "instance_id": {
                   "$oid": "55410c7f5b335278490a5be8"
               },
               "instance_name": "test123",
               "instance_type": "mongodb_sharded",
               "login": "donovan@heydonovan.io",
               "port": 35023,
               "timestamp": {
                   "$date": 1439857318463
               },
               "timestamp_formatted": "2015/08/18 00:21:58"
           }
       ]
   }

Get log details
~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/logs/

Request/Response:

.. code-block:: bash

   $ ERROR

