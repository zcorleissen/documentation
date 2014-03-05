cURL
====


Overview
--------

The ObjectRocket API is a REST based HTTP API. The API can be used in
addition to and along side the MongoDB driver to access an
ObjectRocket instance. The API expects a HTTP POST with a document and
an API key. The document can be the document to write to the database,
or it can be a query object in the form of the query's predicate. The
following is an example cURL HTTP POST where API_KEY is your API key,
DB_NAME is your database name, COLLECTION_NAME is the name of your
collection or table, and API_OPERATION is the method or operation that
you are attempting to execute.

.. code-block:: bash

   $> curl --data 'api_key=API_KEY&doc={"name":"Chuck"}' 'https://api.objectrocket.com/db/DB_NAME/collection/COLLECTION_NAME/API_OPERATION'

The API then returns a JSON formatted string with a return code and 
the data requested or a message if the operation failed. The 
following is an example return of a successful call:

.. code-block:: json

   {
       rc: 0,
       data: data_payload
   }

In the case of an error the format is:

.. code-block:: json

   {
       rc: 1,
       msg: returned_message
   }


MongoDB Document Manipulation and Retrieval Operations
------------------------------------------------------

The following section contains details and examples about how to 
manipulate and retrieve documents from an ObjectRocket instance.


ADD
^^^

The Add API operation inserts a document into the given collection
(COLLECTION_NAME) in the given database (DB_NAME). If the insert is
successful, the object is returned with a primary key (_id). The add
api operation is analogous to the save MongoDB method. The following
is the format of a cURL HTTP POST for the Add API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:DOCUMENT: - The JSON document that you are adding to the given collection.
:DB_NAME: - The name of the database that contains the collection that you are inserting the document into.
:COLLECTION_NAME: - The name of the collection or table that you are inserting the document into.

Command
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=API_KEY&doc=DOCUMENT' 'https://api.objectrocket.com/db/DB_NAME/collection/COLLECTION_NAME/add'

Examples
~~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=abcd1234&doc={"first_name":"Chuck", "last_name":"Smith", "age":35}' 'https://api.objectrocket.com/db/mydb0/collection/mycol0/add'
   {
      "data": {
        "first_name": "Chuck",
        "last_name": "Smith",
        "age": 35,
        "_id": {
          "$oid": "50876f83cb72593131000000"
        }
      },
      "rc": 0
   }

   
.. code-block:: bash

   $> curl --data 'api_key=abcd1234&doc={"first_name":"Bob", "last_name":"O'"'"'Doyle", "age":40}' 'https://api.objectrocket.com/db/mydb0/collection/mycol0/add'
   {
      "data": {
        "first_name": "Bob",
        "last_name": "O'Doyle",
        "age": 40,
        "_id": {
          "$oid": "5087759e5b33524255000000"
        }
      },
      "rc": 0
   }

.. code-block:: bash

   $> curl --data 'api_key=abcd1234&doc={"company_name":"Standard Oil", "date_founded":"1870-01-01T10:00:00.0Z", "industry":"Oil"}' 'https://api.objectrocket.com/db/mydb0/collection/mycol1/add'
   {
      "data": {
        "industry": "Oil",
        "date_founded": "1870-01-01T10:00:00.0Z",
        "_id": {
          "$oid": "5087774d845eb57f7c000000"
        },
        "company_name": "Standard Oil"
      },
      "rc": 0
   }

   
GET
^^^

The Get API operation returns a set of the document(s) that meet the
given document query (QUERY) from the given collection
(COLLECTION_NAME) in the given database (DB_NAME). The get operation
is analogous to the find MongoDB method. The following is the format
of a cURL HTTP POST for the Get API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:QUERY: - A query predicate in the form of a JSON document.
:DB_NAME: - The name of the database that contains the collection that you are retrieving documents from.
:COLLECTION_NAME: - The name of the collection or table that you are retrieving documents from.

Command
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=API_KEY&doc=QUERY' 'https://api.objectrocket.com/db/DB_NAME/collection/COLLECTION_NAME/get'

Examples
~~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=abcd1234&doc={"first_name": "Chuck"}' 'https://api.objectrocket.com/db/mydb0/collection/mycol0/get'
   {
      "data": [
        {
          "last_name": "Smith",
          "first_name": "Chuck",
          "_id": {
            "$oid": "50876f83cb72593131000000"
          },
          "age": 35
        }
      ],
      "rc": 0
   }

.. code-block:: bash

   $> curl --data 'api_key=abcd1234&doc={"age": {"$lt":35}}' 'https://api.objectrocket.com/db/mydb0/collection/mycol0/get'
   {
      "data": [
        {
          "last_name": "Rockefeller",
          "middle_ini": "D",
          "age": 33,
          "_id": {
            "$oid": "5087760e845eb56e8b000000"
          },
          "first_name": "John"
        },
        {
          "last_name": "Welch",
          "first_name": "Jack",
          "_id": {
            "$oid": "508776985b33524256000000"
          },
          "age": 33,
          "married": true
        }
      ],
      "rc": 0
   }


UPDATE
^^^^^^

The Update API operation will update the first document in the given
collection (COLLECTION_NAME) in the given database (DB_NAME) that
matches the given query predicate (QUERY) and set all of that
document's values to that which are specified in the set
(NEW_DOCUMENT) clause. Fields that are omitted in the set operation
will be removed from the updated document. If successful, the returned
data will specify the number of affected documents. The update api
operation is similar to the update MongoDB method, except for the fact
that the Update API operation only updates the first document that
meets the query predicate's criteria, where as the MongoDB method can
accept an optional argument that will allow the method to update
multiple documents at one time. The following is the format of a cURL
HTTP POST for the Update API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:QUERY: - A query predicate in the form of a JSON document.
:NEW_DOCUMENT: - The JSON document that will replace the first instance of the document that meets the query predicate.
:DB_NAME: - The name of the database that contains the collection that you are updating the document in.
:COLLECTION_NAME: - The name of the collection or table that you are updating the document in.

Command
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=API_KEY&doc=DOCUMENT&set=NEW_DOCUMENT' 'https://api.objectrocket.com/db/DB_NAME/collection/COLLECTION_NAME/update'

Examples
~~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=abcd1234&doc={"first_name": "Teddy"}&set={"first_name":"Cornelius", "last_name":"Vanderbilt", "age":40}' 'https://api.objectrocket.com/db/mydb0/collection/mycol0/update'
   {
       "rc": 0,
       "n": 1
   }
   
.. code-block:: bash

   $> curl --data 'api_key=abcd1234&doc={"first_name": "Bob"}&set={"first_name":"Cornelius", "last_name":"Vanderbilt", "age":41}' 'https://api.objectrocket.com/db/mydb0/collection/mycol0/update'
   {
       "rc": 0,
       "n": 0
   }


DELETE
^^^^^^

The Delete API operation deletes all documents in the given collection
(COLLECTION_NAME) in the given database (DB_NAME) that meet the
criteria specified in the query predicate (QUERY). If successful, the
returned data specifies the number of deleted documents. The delete
api operation is analogous to the remove MongoDB method. The following
is the format of a cURL HTTP POST for the Delete API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:QUERY: - A query predicate in the form of a JSON document.
:DB_NAME: - The name of the database that contains the collection that you are deleting the document from.
:COLLECTION_NAME: - The name of the collection or table that you are deleting the document from.

Command
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=API_KEY&doc=QUERY' 'https://api.objectrocket.com/db/DB_NAME/collection/COLLECTION_NAME/delete'

Examples
~~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=abcd1234&doc={"age": {"$lt":41}}' 'https://api.objectrocket.com/db/mydb0/collection/mycol0/delete'
   {
       "rc": 0,
       "n": 4
   }


MongoDB Instance Management Operations
--------------------------------------

Instance Details
^^^^^^^^^^^^^^^^

The Instance Details API operation returns details about all
ObjectRocket instances associated with the given API key (API_KEY).
The following is the format of a cURL HTTP POST for the Instance
Details API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.

Command
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=API_KEY' 'https://api.objectrocket.com/instance'

Examples
~~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=abcd1234' 'https://api.objectrocket.com/instance'
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


Server Status
^^^^^^^^^^^^^

The Server Status API operation returns an object of type ServerStatus
showing counters for various operations for the instances of the given
API key (API_KEY). The output returned by the Server Status API
operation is required by the rocketstat utility. The following is the
format of a cURL HTTP POST for the Server Status API Operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.

Command
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=API_KEY' 'https://api.objectrocket.com/serverStatus'

Examples
~~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=abcd1234' 'https://api.objectrocket.com/serverStatus'
   {
       "data": {
           "indexCounters": {
               "btree": {
                   "missRatio": 0.0,
                   "resets": 0,
                   "hits": 1884749,
                   "misses": 0,
                   "accesses": 1884749
               }
           },
           "connections": {
               "current": 31,
               "available": 19969
           },
           "plan": 20,
           "cursors": {
               "clientCursors_size": 2,
               "timedOut": 33,
               "totalOpen": 2
           },
           "writeBacksQueued": false,
           "globalLock": {
               "totalTime": 4522903384036.0,
               "currentQueue": {
                   "total": 0,
                   "writers": 0,
                   "readers": 0
               },
               "lockTime": 3967860394.0,
               "ratio": 0.0008772817053764459,
               "activeClients": {
                   "total": 2,
                   "writers": 0,
                   "readers": 2
               }
           },
           "backgroundFlushing": {
               "last_finished": {
                   "$date": 1350873424334
               },
               "last_ms": 1,
               "flushes": 75381,
               "average_ms": 0.9229381409108396,
               "total_ms": 69572
           },
           "opcounters": {
               "getmore": 4261495,
               "insert": 51104017,
               "update": 4015099,
               "command": 22168920,
               "query": 2669,
               "delete": 3
           },
           "uptime": 4522903.0,
           "ok": 1.0,
           "network": {
               "numRequests": 77676659,
               "bytesOut": 18977925411.0,
               "bytesIn": 6275223047.0
           },
           "zone": "US-West",
           "instance": "rocketdemo",
           "version": "2.0.6",
           "asserts": {
               "msg": 0,
               "rollovers": 0,
               "regular": 0,
               "warning": 31,
               "user": 435
           }
       },
       "rc": 0
   }

   
Space Usage
^^^^^^^^^^^

The Space Usage API operation returns a summary of disk space usage in
bytes for each of the ObjectRocket instances for the given API key
(API_KEY).

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.

Command
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=API_KEY' 'https://api.objectrocket.com/spaceusage/get'

Examples
~~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=abcd1234' 'https://api.objectrocket.com/spaceusage/get'
   {
       "data": {
           "total_size": 3946557408.0,
           "index_size": 2884631792.0,
           "data_size": 2998893112.0,
           "file_size": 20224147456.0
       },
       "rc": 0
   }


Add Database and Add User
^^^^^^^^^^^^^^^^^^^^^^^^^

The Add Database API operation will create a database with the given
name (DB_NAME) and given MongoDB user credentials (USERNAME, PASSWORD)
for the given API key (API_KEY). If the database already exists, a
user can be added to the database by using this operation. The
following is the format of a cURL HTTP POST for the Add Database API
operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:USERNAME: - The username for the account that will be granted access to the given MongoDB database.
:PASSWORD: - The password for the account that will be granted access to the given MongoDB database.
:DB_NAME: - The name of the database that will be created or if the database already exists, the name of the database that the given account will be granted access to.

Command
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=API_KEY&doc={"USERNAME":"PASSWORD"}' 'https://api.objectrocket.com/db/DB_NAME/add'

Examples
~~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=abcd1234&doc={"user0":"p4ssw0rd"}' 'https://api.objectrocket.com/db/mydb0/add'
   {
       "data": "OK",
       "rc": 0
   }


List Databases
^^^^^^^^^^^^^^

The List Databases API operation will return statistics about all
databases owned by the given API key (API_KEY). The following is the
format of a cURL HTTP POST for the List Databases API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.

Command
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=API_KEY' 'https://api.objectrocket.com/db'

Examples
~~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=abcd1234' 'https://api.objectrocket.com/db'
   {
       "data": [
           {
               "stats": {
                   "dataSize": 328,
                   "ok": 1.0,
                   "avgObjSize": 46.857142857142854,
                   "indexes": 1,
                   "objects": 7,
                   "fileSize": 50331648,
                   "numExtents": 4,
                   "storageSize": 1064960,
                   "indexSize": 8176
               },
               "name": "mydb"
           },
           {
               "stats": {
                   "dataSize": 448,
                   "ok": 1.0,
                   "avgObjSize": 64.0,
                   "indexes": 1,
                   "objects": 7,
                   "fileSize": 50331648,
                   "numExtents": 4,
                   "storageSize": 1069056,
                   "indexSize": 8176
               },
               "name": "mydb0"
           },
       ],
       "rc": 0
   }


Get Profiler Data
^^^^^^^^^^^^^^^^^

The Get Profiler Data API operation returns standard MongoDB profiler
output for all queries that meet the given criteria on all shards for
the given API key. The following is the format of a cURL HTTP POST for
the Get Profiler Data API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:QUERY: - A query predicate in the form of a JSON document.

Command
~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=API_KEY&doc=QUERY' 'https://api.objectrocket.com/profiler/get'

Examples
~~~~~~~~

.. code-block:: bash

   $> curl --data 'api_key=abcdef&doc={"millis":{"$gt":100}}' 'https://api.objectrocket.com/profiler/get'
   {
       "data": [
           {
               "responseLength": 389,
               "millis": 120809,
               "ts": {
                   "$date": 1349471397058
               },
               "client": "10.48.2.30",
               "command": {
                   "listDatabases": 1
               },
               "user": "",
               "ntoreturn": 1,
               "ns": "admin.$cmd",
               "op": "command"
           },
           {
               "responseLength": 389,
               "millis": 116905,
               "ts": {
                   "$date": 1349471397059
               },
               "client": "10.48.2.32",
               "command": {
                   "listDatabases": 1
               },
               "user": "",
               "ntoreturn": 1,
               "ns": "admin.$cmd",
               "op": "command"
           },
       ],
       "rc": 0
   }
