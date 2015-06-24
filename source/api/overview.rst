The ObjectRocket API
====================

Examples
--------

.. toctree::
   :maxdepth: 1
   :glob:

   *


Overview
--------


The ObjectRocket API is a REST based HTTP API over SSL. The API can be used in
addition and along side the MongoDB driver access into ObjectRocket. Both 
regular data operations like add, get, update, delete are supported against
any collection as well as various metadata operations are supported for
observability and management of the instance.

Any client that supports an HTTP interface should work well with the
ObjectRocket API. Examples of how to use the API exist for
:doc:`python`, :doc:`nodejs`, :doc:`java`, and :doc:`php`.

The API expects a POST with a document, and an API KEY. The document can be
the document to write to the database and optionally, can be a query object
(the predicate for the query). The API then returns a JSON formatted string
with a return code, and the data requested or in the case
of a failure the error msg.

.. code-block:: json

   {
       rc: 0,                  // success
       data: data_payload      // the data or metadata payload returned
   }


In the case of an error the format is:

.. code-block:: json

   {
       rc: 1,                  // a problem occurred
       msg: returned_message   // the error message
   }


Authentication
--------------

In order to use the API you must authenticate using your API key.
A key is a unique key for each customer/instance pair. You can find
your key in the 'API' column at https://app.objectrocket.com/instances.

.. WARNING::

   Your API key allows access to your data on a per instance basis, so this key should not be
   exposed to any untrusted source.


Operations
----------

Add
^^^

Adds data to the database. The returned data is the
primary key of the new document.


:URI: /db/DB/collection/COLLECTION/add
:API Key: POST required
:doc: POST valid document to be inserted
:return key: data
:return value: OID of the document inserted


Example
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=1234&doc={"test":1}' 'https://api.objectrocket.com/db/mydb/collection/mycollection/add'
   {
       "data": {
           "test": 1,
           "_id": {
               "$oid": "50c269235b33521058000000"
           }
       },
       "rc": 0
   }


Get
^^^

Queries data from the database.

:URI: /db/DB/collection/COLLECTION/get
:API Key: POST required
:doc: POST valid for query condition
:return key: data
:return value: array of data


Example
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=1234&doc={"test":1}' 'https://api.objectrocket.com/db/mydb/collection/mycollection/get'
   {
       "data": [
           {
               "test": 1,
               "_id": {
                   "$oid": "50c269235b33521058000000"
               }
           }
       ],
       "rc": 0
   }


Update
^^^^^^

Updates data in the database. The doc parameter is the query predicate, the
set is the new value for the update. This is a single document update, if
multiple documents are returned from the query parameter, only the first
returned document is updated. The returned data is the primary key of the
document updated.

:URI: /db/DB/collection/COLLECTION/update
:API Key: POST required
:doc: POST valid document for query condition
:set: POST valid document for update
:return key: n
:return value: number of documents updated


Example
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=1234&doc={"test":1}&set={"test":2}' 'https://api.objectrocket.com/db/mydb/collection/mycollection/update'
   {
       "rc": 0,
       "n": 1
   }

   $> curl --data 'api_key=1234&doc={"test":2}' 'https://api.objectrocket.com/db/mydb/collection/mycollection/get'
   {
       "data": [
           {
               "test": 2,
               "_id": {
                   "$oid": "50c269235b33521058000000"
               }
           }
       ],
       "rc": 0
   }


Delete
^^^^^^

Deletes data from the database

:URI: /db/DB/collection/COLLECTION/delete
:API Key: POST required
:doc: POST valid document for query condition
:return key: n
:return value: The number of documents removed


Example
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=1234&doc={"test":2}' 'https://api.objectrocket.com/db/mydb/collection/mycollection/delete'
   {
       "rc": 0,
       "n": 1
   }


Metadata Operations
-------------------


Space Usage
^^^^^^^^^^^

Gets space usage for the instance. Good for monitoring.

:Resource: spaceusage
:URI: /spaceusage/get
:API Key: POST required
:doc: POST not required
:return key: data
:return value: document


Example
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=1234' 'https://api.objectrocket.com/spaceusage/get'
   {
       "data": {
           "total_size": 3502624768.0,
           "index_size": 2715290480.0,
           "shards": [
               {
                   "total_size": 8734986096.0,
                   "index_size": 2715167840.0,
                   "file_size": 16635920384.0,
                   "shard": "shard_30013",
                   "data_size": 7130710776.0
               }
           ],
           "data_size": 2459209112.0,
           "file_size": 11269832704.0
       },
       "rc": 0
   }


Server Status
^^^^^^^^^^^^^

Gets performance data for the instance, synonymous with serverStatus().
Good for monitoring and management tools.

:Resource: serverStatus
:URI: /serverStatus
:API Key: POST required
:doc: POST not required
:return key: data
:return value: document


Example
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=1234' 'https://api.objectrocket.com/serverStatus'
   {
       "data": {
           "indexCounters": { "btree": { "missRatio": 0.0, "resets": 0, "hits": 3333114, "misses": 0, "accesses": 3333114 }},
           "connections": { "current": 31, "available": 19969 },
           "plan": 20,
           "cursors": { "clientCursors_size": 2, "timedOut": 43, "totalOpen": 2 },
           "writeBacksQueued": false,
           "globalLock": {
               "totalTime": 3593490152795.0,
               "currentQueue": {
                   "total": 0,
                   "writers": 0,
                   "readers": 0
               },
               "lockTime": 3742748320.0,
               "ratio": 0.001041535710648576,
               "activeClients": {
                   "total": 2,
                   "writers": 0,
                   "readers": 2
               }
           },
           "backgroundFlushing": {
               "last_finished": {
                   "$date": 1354911272239
               },
               "last_ms": 0,
               "flushes": 59891,
               "average_ms": 4.833196974503681,
               "total_ms": 289465
           },
           "opcounters": {
               "getmore": 9622259,
               "insert": 51991653,
               "update": 7388978,
               "command": 42125248,
               "query": 4085462,
               "delete": 40
           },
           "uptime": 3593490.0,
           "ok": 1.0,
           "network": { "numRequests": 111904374, "bytesOut": 23169121531.0, "bytesIn": 9693426113.0 },
           "zone": "US-West",
           "instance": "rocketdemo",
           "version": "2.0.6",
           "asserts": { "msg": 0, "rollovers": 0, "regular": 0, "warning": 12, "user": 297 }
       },
       "rc": 0
   }


Server Status Plus
^^^^^^^^^^^^^^^^^^

Identical to ServerStatus with an additional entry for greatest replication
lag.

:Resource: serverStatusPlus
:URI: /serverStatusPlus
:API Key: POST required
:doc: POST not required
:return key: data
:return value: document


Example
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=1234' 'https://api.objectrocket.com/serverStatusPlus'
   {
       "data": {
           "greatest_rep_lag": 0.2,
           "indexCounters": { "btree": { "missRatio": 0.0, "resets": 0, "hits": 3333114, "misses": 0, "accesses": 3333114 }},
           "connections": { "current": 31, "available": 19969 },
           "plan": 20,
           "cursors": { "clientCursors_size": 2, "timedOut": 43, "totalOpen": 2 },
           "writeBacksQueued": false,
           "globalLock": {
               "totalTime": 3593490152795.0,
               "currentQueue": {
                   "total": 0,
                   "writers": 0,
                   "readers": 0
               },
               "lockTime": 3742748320.0,
               "ratio": 0.001041535710648576,
               "activeClients": {
                   "total": 2,
                   "writers": 0,
                   "readers": 2
               }
           },
           "backgroundFlushing": {
               "last_finished": {
                   "$date": 1354911272239
               },
               "last_ms": 0,
               "flushes": 59891,
               "average_ms": 4.833196974503681,
               "total_ms": 289465
           },
           "opcounters": {
               "getmore": 9622259,
               "insert": 51991653,
               "update": 7388978,
               "command": 42125248,
               "query": 4085462,
               "delete": 40
           },
           "uptime": 3593490.0,
           "ok": 1.0,
           "network": { "numRequests": 111904374, "bytesOut": 23169121531.0, "bytesIn": 9693426113.0 },
           "zone": "US-West",
           "instance": "rocketdemo",
           "version": "2.0.6",
           "asserts": { "msg": 0, "rollovers": 0, "regular": 0, "warning": 12, "user": 297 }
       },
       "rc": 0
   }


Instance Details
^^^^^^^^^^^^^^^^

Gets details for the instance.

:Resource: instance
:URI: /instance
:API Key: POST required
:doc: POST not required
:return key: data
:return value: document


Example
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=1234' 'https://api.objectrocket.com/instance'
   {
       "data": {
           "name": "rocketdemo",
           "zone": "US-West",
           "host": "w-mongos0.objectrocket.com",
           "plan": 20,
           "port": 10013,
           "size": 20.0
       },
       "rc": 0
   }


Database Details
^^^^^^^^^^^^^^^^

Gets all databases for the instance.

:Resource: db
:URI: /db
:API Key: POST required
:doc: POST not required
:return key: data
:return value: array of databases


Example
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=1234' 'https://api.objectrocket.com/db'
   {
       "data": [
           {
               "stats": {
                   "dataSize": 328,
                   "ok": 1.0,
                   "avgObjSize": 54.666666666666664,
                   "indexes": 2,
                   "objects": 6,
                   "fileSize": 50331648,
                   "numExtents": 3,
                   "storageSize": 20480,
                   "indexSize": 16352
               },
               "name": "mytestdb"
           },
           {
               "stats": {
                   "dataSize": 816,
                   "ok": 1.0,
                   "avgObjSize": 58.285714285714285,
                   "indexes": 3,
                   "objects": 14,
                   "fileSize": 50331648,
                   "numExtents": 4,
                   "storageSize": 24576,
                   "indexSize": 24528
               },
               "name": "rocketdemo"
           }
       ],
       "rc": 0
   }


Collection Details
^^^^^^^^^^^^^^^^^^

Gets details for a collection

:Resource: stats
:URI: /db/db/collection/collection/stats/get
:API Key: POST required
:doc: POST not required
:return key: data
:return value: document


Example
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=1234' 'https://api.objectrocket.com/db/mydb/collection/mycollection/stats/get'
   {
      "data":{
         "shardkey":{
            "unique":false,
            "lastmod":{
               "$date":1361375853
            },
            "key":"username"
         },
         "sharded":true,
         "chunks":[
            {
               "_id":"kg.test1-username_MinKey",
               "min":{
                  "$minKey":1
               },
               "max":{
                  "$maxKey":1
               },
               "shard":"30013",
               "ns":"kg.test1",
               "lastmod":{
                  "i":0,
                  "t":1
               }
            }
         ],
         "numExtents":1,
         "storageSize":8192,
         "indexSizes":{
            "_id_":8176,
            "username_1":8176
         },
         "size":0,
         "count":0,
         "totalIndexSize":16352,
         "ok":1.0,
         "avgObjSize":0.0,
         "nchunks":1,
         "shards":{
            "30013":{
               "count":0,
               "storageSize":8192,
               "ok":1.0,
               "lastExtentSize":8192,
               "totalIndexSize":16352,
               "flags":1,
               "numExtents":1,
               "nindexes":2,
               "ns":"kg.test1",
               "indexSizes":{
                  "_id_":8176,
                  "username_1":8176
               },
               "paddingFactor":1.0,
               "size":0
            }
         },
         "flags":1,
         "nindexes":2,
         "ns":"kg.test1"
      },
      "rc":0
   }


Get Logs
^^^^^^^^

Gets logs for the instance.

:Resource: logs
:URI: /logs/get
:API Key: POST required
:doc: POST not required
:return key: data
:return value: array of shard hosts, containing log entries for each host


Example
~~~~~~~

.. code-block:: bash

   $>curl --data 'api_key=1234' 'https://api.objectrocket.com/logs/get'
   {
       "data": {
           "server0": [
               {
                   "syslog_tag": "mongod.30047[4052]:",
                   "time_rcvd": {
                       "$date": 1373653720338
                   },
                   "syslog_fac": 1,
                   "procid": "mongod.30047",
                   "level": "INFO",
                   "pid": "4052",
                   "sys": "server0",
                   "syslog_sever": 6,
                   "time": {
                       "$date": 1373653754000
                   },
                   "msg": "Fri Jul 12 11:29:14 Log entry here",
                   "_id": {
                       "$oid": "51e04afaf27a12257526bd4a"
                   }
               }
           ],
       },
       "rc": 0
   }


Get Profiler Data
^^^^^^^^^^^^^^^^^

Gets profiler data for all db's in the instance. Synonymous with
showProfile().

:Resource: profiler
:URI: /profiler/get
:API Key: POST required
:doc: POST valid document with query parameter document
:return key: data
:return value: array of profiler documents


Example
~~~~~~~

.. code-block:: bash

   $>curl --data 'api_key=1234&doc={"millis":{"$gt":10}}' 'https://api.objectrocket.com/profiler/get'
   {
       "data": [
           {
               "ns": "mydb0.mycol0",
               "millis": 54,
               "ts": {
                   "$date": 1351058243597
               },
               "client": "10.48.2.30",
               "user": "",
               "query": {
                   "first_name": "Chuck"
               },
               "updateobj": {
                   "first_name": "Cornelius",
                   "last_name": "Vanderbilt"
               },
               "nscanned": 1,
               "op": "update"
           }
       ],
       "rc": 0
   }
   

Get Profiling Levels
^^^^^^^^^^^^^^^^^^^^

Gets the profiling levels for all dbs in an instance.

:Resource: profiler
:URI: /profiling_level/get
:API Key: POST required
:doc: POST not required
:return key: data
:return value: document


Example
~~~~~~~

.. code-block:: bash

   $>curl --data 'api_key=1234' 'https://api.objectrocket.com/profiling_level/get'
   {
       "data": {
           "44c9fd0f3fb1450795824740a94d29f4": {
               "mydb": 1,
               "yourdb": 1,
               "slowms": 90
           }
       },
       "rc": 0
   }


Set Profiling Levels
^^^^^^^^^^^^^^^^^^^^

Sets the profiling levels for one or more dbs in an instance.

:Resource: profiler
:URI: /profiling_level/set
:API Key: POST required
:doc: POST valid document with query parameter document
:return key: data
:return value: document


Examples
~~~~~~~~


Set profiling level 2 for all databases in the instance:
""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block:: bash

   $> curl --data 'api_key=1234&doc={"level":2}' 'https://api.objectrocket.com/profiling_level/set'
   {
       "data": {
           "44c9fd0f3fb1450795824740a94d29f4": {
               "mydb": 2,
               "yourdb": 2
           }
       },
       "rc": 0
   }


Set profiling level 0 for database 'mydb':
""""""""""""""""""""""""""""""""""""""""""

.. code-block:: bash

   $> curl --data 'api_key=1234&doc={"db":"mydb", "level":0}' 'https://api.objectrocket.com/profiling_level/set'
   {
       "data": {
           "44c9fd0f3fb1450795824740a94d29f4": {
               "mydb": 0
           }
       },
       "rc": 0
   }


Set slow operation threshold for profiling:
"""""""""""""""""""""""""""""""""""""""""""

.. WARNING::

   This setting is global to the instance, and requires you set a profile level

.. code-block:: bash

   $> curl --data 'api_key=1234&doc={"level":1, "slowms":120}' 'https://api.objectrocket.com/profiling_level/set'
   {
       "data": {
           "44c9fd0f3fb1450795824740a94d29f4": {
               "mydb": 1,
               "yourdb": 1,
               "slowms": 120
           }
       },
       "rc": 0
   }

Get ACL
^^^^^^^

Get current ACLs for an instance.

:Resource: acl
:URI: /acl/get
:API Key: POST required
:doc: POST not required
:return key: data
:return value: Informational message


Example
~~~~~~~

.. code-block:: bash

  $>curl --data 'api_key=1234' 'https://api.objectrocket.com/acl/get'
  {
      "data": [
          {
              "cidr_mask": "1.2.3.4/32",
              "description": "Development Server in VA"
          },
          {
              "cidr_mask": "5.6.7.8/24",
              "description": "QA Lab in San Jose"
          }
      ],
      "rc": 0
  }


Add ACL
^^^^^^^

Add a new ACL for an instance.

:Resource: acl
:URI: /acl/add
:API Key: POST required
:doc: POST valid document with query parameter document
:return key: data
:return value: Informational message


Example
~~~~~~~

.. code-block:: bash

  $>curl --data 'api_key=1234&doc={"cidr_mask": "1.2.3.4/32", "description": "Development Server in VA"}' 'https://api.objectrocket.com/acl/add'
  {
      "data": "ACL added successfully",
      "rc": 0
  }


Delete ACL
^^^^^^^^^^

Delete an ACL for an instance.

:Resource: acl
:URI: /acl/delete
:API Key: POST required
:doc: POST valid document with query parameter document
:return key: data
:return value: Informational message


Example
~~~~~~~

.. code-block:: bash

  $>curl --data 'api_key=1234&doc={"cidr_mask": "1.2.3.4/32"}' 'https://api.objectrocket.com/acl/delete'
  {
      "data": "ACL removed successfully",
      "rc": 0
  }
