Python
======

Overview
--------

The ObjectRocket API is a REST based HTTP API. The API can be used in 
addition to and along side the MongoDB driver to access an 
ObjectRocket instance. The API expects a HTTP POST with a document 
and an API key. The document can be the document to write to the 
database, or it can be a query object in the form of the query's 
predicate. JSON and HTTP toolkits are needed to work with 
ObjectRocket easily. The following Python examples are written in 
Python 2.7.2 using Eclipse with the PyDev module and the examples use 
json-simple and httplib toolkits. httplib should already be included 
in default Python installations. The following steps detail how to 
setup the simplejson toolkit::

   http://pypi.python.org/pypi/simplejson/ python setup.py build


- Download simple-json from http://pypi.python.org/pypi/simplejson/
- Extract the zip or tarball and change your CLI to the extracted directory.
- Execute "python setup.py build" in the simple-json directory to build the
  toolkit.
- Execute "python setup.py install" in the simple-json directory to install
  the toolkit and the module should now be available for imports.

The following is a Python 2.7.2 example using httplib and simplejson 
to perform an ObjectRocket API call and display the results of the 
call. The API operations on the rest of this page will be slimmed 
down snippets that assume the rest of the following example's code is 
in place.

.. code-block:: python

   import simplejson as json
   import httplib   

   try:

       # The name of your database.
       db = "mydb0";   

       # The name of your collection or table.
       collection = "mycol0";   

       # Define the method for the HTTP POST. In this instance, it is the Add API operation.
       method = "/db/%s/collection/%s/add" % (db, collection)   

       # The api key of your ObjectRocket user.
       apiKey = "abcd1234";   

       # Define the document parameter.
       document = json.dumps({"first_name":"Chuck"})   

       # Define the HTTP POST parameters.
       params = "api_key=%s&doc=%s" % (apiKey,document)   

       print("HTTP POST parameters: \n%s\n" % params)

       # Define the API host server:port and create the http connection to that host.
       host = "api.objectrocket.com:80"
       conn = httplib.HTTPConnection(host)   

       # Define the headers for the HTTP POST.
       headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}   

       # Execute the request property on your HTTP connection.
       conn.request("POST", method, params, headers)   

       # Get the response from the request.
       response = conn.getresponse()   

       # Close the HTTP connection.
       conn.close()   

       print('Response status and response code: \n%s %s\n' % (response.status, response.reason))

       # Read the data in from the HTTP POST.
       data = response.read()   

       # Print the data returned from the HTTP Post
       print('Raw string response: \n%s\n' % data)   

       # Parse the returned string as JSON and retrieve various properties. 
       result = json.loads(data)   

       returncode = result["rc"]

       data = result["data"]

       print('Return code: \n%s\n' % returncode)

       print('Data (raw json): \n%s\n' % data)

       print('_id: \n%s\n' % data["_id"]["$oid"])

   except Exception as e:
       print("Caught exception executing HTTP POST: %s" % e.__str__())


The following is the console output of the above example::

   HTTP POST parameters: 
   api_key=abcd1234&doc={"first_name": "Chuck"}   

   Response status and response code: 
   200 OK


   Raw string response:
   {
       "data": {
           "first_name": "Chuck", 
           "_id": {
               "$oid": "50a49129c3fbcc3828000001"
           }
       }, 
       "rc": 0
   }


   Return code: 
   0


   Data (raw json): 
   {u'first_name': u'Chuck', u'_id': {u'$oid': u'50a49129c3fbcc3828000001'}}


   _id: 
   50a49129c3fbcc3828000001

The API returns a JSON formatted string with a return code and the 
data requested or if the operation fails, a JSON formatted string 
with a return code and a message detailing the cause of the failure. 
The following is an example return of a successful call:

.. code-block:: json

   {
       rc: 0,
       data: data_payload
   }

In the case of an error the format is:

.. code-block:: json

   {
       rc: 1,
       data: returned_message
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
are details about the Add API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:DOCUMENT: - The JSON document that you are adding to the given collection.
:DB_NAME: - The name of the database that contains the collection that you are inserting the document into.
:COLLECTION_NAME: - The name of the collection or table that you are inserting the document into.

POST URL::

   https://api.objectrocket.com/db/DB_NAME/collection/COLLECTION_NAME/add

POST Parameter::

   api_key=API_KEY&doc=DOCUMENT


Example
~~~~~~~
.. code-block:: python

   Example:
   
    # The name of your database.
   db = "mydb0"
   

   # The name of your collection or table.
   collection = "mycol0"

   # Define the method for the HTTP POST.
   method = "/db/%s/collection/%s/add" % (db, collection)

   # The api key of your ObjectRocket user.
   apiKey = "abcd1234"

   # Define the document parameter.
   document = json.dumps({"first_name":"Chuck","last_name":"Smith","age":35})

   # Define the HTTP POST parameters.
   params = "api_key=%s&doc=%s" % (apiKey,document)
   print("HTTP POST parameters: \n%s\n" % params)

   # Define the API host server:port and create the http connection to that host.
   host = "api.objectrocket.com:80"
   conn = httplib.HTTPConnection(host)

   # Define the headers for the HTTP POST.
   headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}

   # Execute the request property on your HTTP connection.
   conn.request("POST", method, params, headers)

   # Get the response from the request.
   response = conn.getresponse()

   # Close the HTTP connection.
   conn.close()


Result
~~~~~~
.. code-block:: json

   
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
   

GET
^^^

The Get API operation returns a set of the document(s) that meet the
given document query (QUERY) from the given collection
(COLLECTION_NAME) in the given database (DB_NAME). The get operation
is analogous to the find MongoDB method. The following are details
about the Get API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:QUERY: - A query predicate in the form of a JSON document.
:DB_NAME: - The name of the database that contains the collection that you are retrieving documents from.
:COLLECTION_NAME: - The name of the collection or table that you are retrieving documents from.

POST URL::

   https://api.objectrocket.com/db/DB_NAME/collection/COLLECTION_NAME/get

POST Parameter::

   api_key=API_KEY&doc=QUERY


Example
~~~~~~~
.. code-block:: python


   # The name of your database.
   db = "mydb0"
   
    # The name of your collection or table.
   collection = "mycol0"
   
    # Define the method for the HTTP POST.
   method = "/db/%s/collection/%s/get" % (db, collection)
   
    # The api key of your ObjectRocket user.
   apiKey = "abcd1234"
   
    # Define the document parameter.
   document = json.dumps({"first_name":"Chuck"})
   
    # Define the HTTP POST parameters.
   params = "api_key=%s&doc=%s" % (apiKey,document)
   
   print("HTTP POST parameters: \n%s\n" % params)
   
    # Define the API host server:port and create the http connection to that host.
   host = "api.objectrocket.com:80"
   conn = httplib.HTTPConnection(host)
   
    # Define the headers for the HTTP POST.
   headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}
   
    # Execute the request property on your HTTP connection.
   conn.request("POST", method, params, headers)
   
    # Get the response from the request.
   response = conn.getresponse()
   
    # Close the HTTP connection.
   conn.close()


Result
~~~~~~
.. code-block:: json

   
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


Example
~~~~~~~
.. code-block:: python


   # The name of your database.
   db = "mydb0"
   

   # The name of your collection or table.
   collection = "mycol0"

   # Define the method for the HTTP POST.
   method = "/db/%s/collection/%s/get" % (db, collection)

   # The api key of your ObjectRocket user.
   apiKey = "abcd1234"

   # Define the document parameter.
   document = json.dumps({"age": {"$lt":36}})

   # Define the HTTP POST parameters.
   params = "api_key=%s&doc=%s" % (apiKey,document)
   print("HTTP POST parameters: \n%s\n" % params)

   # Define the API host server:port and create the http connection to that host.
   host = "api.objectrocket.com:80"
   conn = httplib.HTTPConnection(host)

   # Define the headers for the HTTP POST.
   headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}

   # Execute the request property on your HTTP connection.
   conn.request("POST", method, params, headers)

   # Get the response from the request.
   response = conn.getresponse()

   # Close the HTTP connection.
   conn.close()


Result
~~~~~~
.. code-block:: json

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
multiple documents at one time. The following are the details of the
Update API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:QUERY: - A query predicate in the form of a JSON document.
:NEW_DOCUMENT: - The JSON document that will replace the first instance of the document that meets the query predicate.
:DB_NAME: - The name of the database that contains the collection that you are updating the document in.
:COLLECTION_NAME: - The name of the collection or table that you are updating the document in.

POST URL::

   https://api.objectrocket.com/db/DB_NAME/collection/COLLECTION_NAME/update

POST Parameter::

   api_key=API_KEY&doc=QUERY&set=NEW_DOCUMENT


Example
~~~~~~~
.. code-block:: python


   # The name of your database.
   db = "mydb0"
   
    # The name of your collection or table.
   collection = "mycol0"
   
    # Define the method for the HTTP POST.
   method = "/db/%s/collection/%s/update" % (db, collection)
   
    # The api key of your ObjectRocket user.
   apiKey = "abcd1234"
   
    # Define the document parameter.
   document = json.dumps({"first_name":"Chuck"})
   
    # Define the document for the set parameter.
   setDocument = json.dumps({"first_name":"Cornelius","last_name":"Vanderbilt","age":40})
   
    # Define the HTTP POST parameters.
   params = "api_key=%s&doc=%s&set=%s" % (apiKey,document,setDocument)
   
   print("HTTP POST parameters: \n%s\n" % params)
   
    # Define the API host server:port and create the http connection to that host.
   host = "api.objectrocket.com:80"
   conn = httplib.HTTPConnection(host)
   
    # Define the headers for the HTTP POST.
   headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}
   
    # Execute the request property on your HTTP connection.
   conn.request("POST", method, params, headers)
   
    # Get the response from the request.
   response = conn.getresponse()
   
    # Close the HTTP connection.
   conn.close()


Result
~~~~~~
.. code-block:: json

   
   {
       "rc": 0,
       "n": 1
   }

DELETE
^^^^^^

The Delete API operation deletes all documents in the given collection
(COLLECTION_NAME) in the given database (DB_NAME) that meet the
criteria specified in the query predicate (QUERY). If successful, the
returned data specifies the number of deleted documents. The delete
api operation is analogous to the remove MongoDB method. The following
are details about the Delete API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:QUERY: - A query predicate in the form of a JSON document.
:DB_NAME: - The name of the database that contains the collection that you are deleting the document from.
:COLLECTION_NAME: - The name of the collection or table that you are deleting the document from.

POST URL::

   https://api.objectrocket.com/db/DB_NAME/collection/COLLECTION_NAME/delete

POST Parameter::

   api_key=API_KEY&doc=QUERY


Example
~~~~~~~
.. code-block:: python


   # The name of your database.
   db = "mydb0"
   

   # The name of your collection or table.
   collection = "mycol0"

   # Define the method for the HTTP POST.
   method = "/db/%s/collection/%s/delete" % (db, collection)

   # The api key of your ObjectRocket user.
   apiKey = "abcd1234"

   # Define the document parameter.
   document = json.dumps({"age":{"$lt":36}})

   # Define the HTTP POST parameters.
   params = "api_key=%s&doc=%s" % (apiKey,document)
   print("HTTP POST parameters: \n%s\n" % params)

   # Define the API host server:port and create the http connection to that host.
   host = "api.objectrocket.com:80"
   conn = httplib.HTTPConnection(host)

   # Define the headers for the HTTP POST.
   headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}

   # Execute the request property on your HTTP connection.
   conn.request("POST", method, params, headers)

   # Get the response from the request.
   response = conn.getresponse()

   # Close the HTTP connection.
   conn.close()


Result
~~~~~~
.. code-block:: json

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
The following are details about the Instance Details API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.

POST URL::

   https://api.objectrocket.com/instance

POST Parameter::

   api_key=API_KEY


Example
~~~~~~~
.. code-block:: python


   # Define the method for the HTTP POST.
   method = "/instance"
   

   # The api key of your ObjectRocket user.
   apiKey = "abcd1234"

   # Define the HTTP POST parameters.
   params = "api_key=%s" % apiKey
   print("HTTP POST parameters: \n%s\n" % params)

   # Define the API host server:port and create the http connection to that host.
   host = "api.objectrocket.com:80"
   conn = httplib.HTTPConnection(host)

   # Define the headers for the HTTP POST.
   headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}

   # Execute the request property on your HTTP connection.
   conn.request("POST", method, params, headers)

   # Get the response from the request.
   response = conn.getresponse()

   # Close the HTTP connection.
   conn.close()


Result
~~~~~~
.. code-block:: json

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
operation is required by the rocketstat utility. The following are the
details for the Server Status API Operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.

POST URL::

   https://api.objectrocket.com/serverStatus

POST Parameter::

   api_key=API_KEY


Example
~~~~~~~
.. code-block:: python


   # Define the method for the HTTP POST.
   method = "/serverStatus"
   

   # The api key of your ObjectRocket user.
   apiKey = "abcd1234"

   # Define the HTTP POST parameters.
   params = "api_key=%s" % apiKey
   print("HTTP POST parameters: \n%s\n" % params)

   # Define the API host server:port and create the http connection to that host.
   host = "api.objectrocket.com:80"
   conn = httplib.HTTPConnection(host)

   # Define the headers for the HTTP POST.
   headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}

   # Execute the request property on your HTTP connection.
   conn.request("POST", method, params, headers)

   # Get the response from the request.
   response = conn.getresponse()

   # Close the HTTP connection.
   conn.close()


Result
~~~~~~
.. code-block:: json

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
(API_KEY). The following are details for the Space Usage API
operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.

POST URL::

   https://api.objectrocket.com/spaceusage/get

POST Parameter::

   api_key=API_KEY


Example
~~~~~~~
.. code-block:: python


   # Define the method for the HTTP POST.
   method = "/spaceusage/get"
   

   # The api key of your ObjectRocket user.
   apiKey = "abcd1234"

   # Define the HTTP POST parameters.
   params = "api_key=%s" % apiKey
   print("HTTP POST parameters: \n%s\n" % params)

   # Define the API host server:port and create the http connection to that host.
   host = "api.objectrocket.com:80"
   conn = httplib.HTTPConnection(host)

   # Define the headers for the HTTP POST.
   headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}

   # Execute the request property on your HTTP connection.
   conn.request("POST", method, params, headers)

   # Get the response from the request.
   response = conn.getresponse()

   # Close the HTTP connection.
   conn.close()


Result
~~~~~~
.. code-block:: json

   {
       "data": {
           "total_size": 3946557408.0,
           "index_size": 2884631792.0,
           "data_size": 2998893112.0,
           "file_size": 20224147456.0
       },
       "rc": 0
   }


Add Database / Add User
^^^^^^^^^^^^^^^^^^^^^^^

The Add Database API operation will create a database with the given
name (DB_NAME) and given MongoDB user credentials (USERNAME, PASSWORD)
for the given API key (API_KEY). If the database already exists, a
user can be added to the database by using this operation. The
following are details for the Add Database API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:USERNAME: - The username for the account that will be granted access to the given MongoDB database.
:PASSWORD: - The password for the account that will be granted access to the given MongoDB database.
:DB_NAME: - The name of the database that will be created or if the database already exists, the name of the database that the given account will be granted access to.

POST URL::

   https://api.objectrocket.com/db/DB_NAME/add

POST Parameter::

   api_key=API_KEY&doc={"USERNAME":"PASSWORD"}


Example
~~~~~~~
.. code-block:: python


   # The name of your database.
   db = "mydb0"
   

   # Define the method for the HTTP POST.
   method = "/db/%s/add" % db

   # The api key of your ObjectRocket user.
   apiKey = "abcd1234"

   # Define the document parameter.
   document = json.dumps({"myUsername321":"myPassword321"})

   # Define the HTTP POST parameters.
   params = "api_key=%s&doc=%s" % (apiKey,document)
   print("HTTP POST parameters: \n%s\n" % params)

   # Define the API host server:port and create the http connection to that host.
   host = "api.objectrocket.com:80"
   conn = httplib.HTTPConnection(host)

   # Define the headers for the HTTP POST.
   headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}

   # Execute the request property on your HTTP connection.
   conn.request("POST", method, params, headers)

   # Get the response from the request.
   response = conn.getresponse()

   # Close the HTTP connection.
   conn.close()


Result
~~~~~~
.. code-block:: json

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

POST URL::

   https://api.objectrocket.com/db POST Parameter:

api_key=API_KEY:
The following is an example using the List Databases API operation:
   


Example
~~~~~~~
.. code-block:: python

   

   # The api key of your ObjectRocket user.
   apiKey = "abcd1234"

   # Define the HTTP POST parameters.
   params = "api_key=%s" % apiKey
   print("HTTP POST parameters: \n%s\n" % params)

   # Define the API host server:port and create the http connection to that host.
   host = "api.objectrocket.com:80"
   conn = httplib.HTTPConnection(host)

   # Define the headers for the HTTP POST.
   headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}

   # Execute the request property on your HTTP connection.
   conn.request("POST", method, params, headers)

   # Get the response from the request.
   response = conn.getresponse()

   # Close the HTTP connection.
   conn.close()


Result
~~~~~~
.. code-block:: json

   
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
the given API key. The following are details for the Get Profiler Data
API operation:

Parameters
~~~~~~~~~~

:API_KEY: - Your ObjectRocket API key.
:QUERY: - A query predicate in the form of a JSON document.

POST URL::

   https://api.objectrocket.com/profiler/get

POST Parameter::

   api_key=API_KEY&doc=QUERY


Example
~~~~~~~
.. code-block:: python


   # Define the method for the HTTP POST.
   method = "/profiler/get"
   

   # The api key of your ObjectRocket user.
   apiKey = "abcd1234"

   # Define the document parameter.
   document = json.dumps({"millis": {"$gt":50}})

   # Define the HTTP POST parameters.
   params = "api_key=%s&doc=%s" % (apiKey,document)
   print("HTTP POST parameters: \n%s\n" % params)

   # Define the API host server:port and create the http connection to that host.
   host = "api.objectrocket.com:80"
   conn = httplib.HTTPConnection(host)

   # Define the headers for the HTTP POST.
   headers = {"Content-type": "application/x-www-form-urlencoded","Accept": "text/plain"}

   # Execute the request property on your HTTP connection.
   conn.request("POST", method, params, headers)

   # Get the response from the request.
   response = conn.getresponse()

   # Close the HTTP connection.
   conn.close()


Result
~~~~~~
.. code-block:: json

   
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
