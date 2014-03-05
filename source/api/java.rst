Java
====

Overview
--------

The ObjectRocket API is a REST based HTTP API. The API can be used in 
addition to and along side the MongoDB driver to access an 
ObjectRocket instance. The API expects a HTTP POST with a document 
and an API key. The document can be the document to write to the 
database, or it can be a query object in the form of the query's 
predicate. A JSON and HTTP toolkits are needed to work with 
ObjectRocket easily. The following Java examples use json-simple and 
Apache's HTTP client toolkits. Some alternatives for Java JSON 
toolkits are Jackson and Google Gson. An alternative Java toolkit for 
an HTTP client is Jersey. The following steps detail how to setup the 
simple-json and Apache's Client HTTPComponent toolkits in eclipse:

- Download Apache's Client HTTPComponents from 
  HTTP://hc.apache.org/downloads.cgi
- Extract the zip or tarball to a directory and note the path.
- Download the simple-json jar from 
  http://code.google.com/p/json-simple/ and note the path.
- Create a new project in eclipse.
- Right-click the JRE System Library object for the new project in 
  package explorer, select Build Path, then select Configure Build Path.
- Select Add External JARs on the right hand side.
- Browse to the lib directory of the downloaded HTTP client, select all 
  jars in the directory, then click Open.
- Browse to the directory that you downloaded the simple-json jar to 
  and select that jar, then click Open.
- Then click OK and the jars should now be imported so that the current 
  project can use them.

The following is a Java example using Apache's Client HTTPComponents 
and simple-json to perform an ObjectRocket API call and display the 
results of the call. The API operations on the rest of this page will 
be slimmed down snippets that assume the rest of the following 
example's code is in place.

.. code-block:: java

   import java.io.BufferedReader;
   import java.io.IOException;
   import java.io.InputStreamReader;
   import java.net.MalformedURLException;
   import org.apache.http.HttpResponse;
   import org.apache.http.client.methods.HttpPost;
   import org.apache.http.entity.StringEntity;
   import org.apache.http.impl.client.DefaultHttpClient;
   import org.json.simple.JSONObject;
   import org.json.simple.parser.JSONParser;   

   // The following is an ObjectRocket API example where a document is added to the given database in the given collection.
   public class example {   

       public static void main(String[] args) {   

           try{   

               // The name of your database.
               String db = "mydb0";   

               // The name of your collection or table.
               String collection = "mycol0";   

               // The api key of your ObjectRocket user.
               String apiKey = "abcd1234";   

               // The ObjectRocket URL for the API operation that you are attempting to complete.
               String postUrl = "https://api.objectrocket.com/db/" + db + "/collection/" + collection + "/add";   

               // Create a HTTP Post Request.
               HttpPost postRequest = new HttpPost(postUrl);   

               // Set the JSON properties of the object you are adding to the collection.
               JSONObject document = new JSONObject();
               document.put("first_name","Chuck");
               document.put("last_name","Smith");
               document.put("age",35);   

               // Set the post parameters.
               StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey + "&doc=" + document.toJSONString());
               postParamsEntity.setContentType("application/x-www-form-urlencoded");   

               // Add the post parameters to the post request.
               postRequest.setEntity(postParamsEntity);   

               // Create a HTTP Client.
               DefaultHttpClient httpClient = new DefaultHttpClient();   

               // Execute the HTTP POST 
               System.out.println("Executing HTTP Post...\n");
               HttpResponse response = httpClient.execute(postRequest);   

               // Check the HTTP status of the post.
               if (response.getStatusLine().getStatusCode() != 200 && response.getStatusLine().getStatusCode() != 201) {
                   throw new RuntimeException("Failed: HTTP error code: "
                       + response.getStatusLine().getStatusCode());
               }   

               // Create a reader to read in the HTTP post results.
               BufferedReader br = new BufferedReader(
                               new InputStreamReader((response.getEntity().getContent())));   

               // Read in all of the post results into a String.
               String output = ""; Boolean keepGoing = true;
               while(keepGoing){
                   String currentLine = br.readLine();   

                   if(currentLine == null)
                       keepGoing = false;
                   else
                       output += currentLine;
               }   

               System.out.println("Raw string result: \n" + output);   

               // Convert the post results from a String to a JSONObject.  
               JSONObject result = (JSONObject) new JSONParser().parse(output);   

               // Check the ObjectRocket return code.
               if((Long) result.get("rc") != 0){
                   throw new RuntimeException("ObjectRocket HTTP post failure: " + ((String) result.get("rc")));
               }   

               // Print the post results json object.
               System.out.println("JSON object result: \n" + result.toJSONString());   

               // Print the oid of the object that was added to the collection.
               System.out.println("$oid of inserted object: \n" + ((JSONObject) ((JSONObject) result.get("data")).get("_id")).get("$oid"));   

               // Close the http client.
               httpClient.getConnectionManager().shutdown();   

           } catch (MalformedURLException e){
               System.out.println("Caught MalformedURLException: " + e.toString());   

           } catch (IOException e){
               System.out.println("Caught IOException: " + e.toString());   

           } catch (Exception e){
               System.out.println("Caught Exception: " + e.toString());
           }   

       }   

   }

The following is the console output of the above example::

   Executing HTTP Post...

   Raw string result: 
   {    "data": {        "first_name": "Chuck",         "last_name": "Smith",         "age": 35,         "_id": {            "$oid": "50a1c343cb72590157000000"        }    },     "rc": 0}
   JSON object result: 
   {"data":{"first_name":"Chuck","_id":{"$oid":"50a1c343cb72590157000000"},"age":35,"last_name":"Smith"},"rc":0}
   $oid of inserted object: 
   50a1c343cb72590157000000

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
.. code-block:: java


   // The name of your database.
   String db = "mydb0";
   

   // The name of your collection or table.
   String collection = "mycol0";

   // The api key of your ObjectRocket user.
   String apiKey = "abcd1234";

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/db/" + db + "/collection/" + collection + "/add";

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);

   // Set the JSON properties of the object you are adding to the collection.
   JSONObject document = new JSONObject();
   document.put("first_name","Chuck");
   document.put("last_name","Smith");
   document.put("age",35);

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey + "&doc=" + document.toJSONString());
   postParamsEntity.setContentType("application/x-www-form-urlencoded");

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...");
   HttpResponse response = httpClient.execute(postRequest);


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


Example
~~~~~~~
.. code-block:: java


   // The name of your database.
   String db = "mydb0";
   

   // The name of your collection or table.
   String collection = "mycol1";

   // The api key of your ObjectRocket user.
   String apiKey = "abcd1234";

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/db/" + db + "/collection/" + collection + "/add";

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);

   // Set the JSON properties of the object you are adding to the collection.
   JSONObject document = new JSONObject();
   document.put("company_name","Standard Oil");
   document.put("date_founded","1870-01-01T10:00:00.0Z");
   document.put("industry","Oil");

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey + "&doc=" + document.toJSONString());
   postParamsEntity.setContentType("application/x-www-form-urlencoded");

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...");
   HttpResponse response = httpClient.execute(postRequest);


Result
~~~~~~
.. code-block:: json

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
.. code-block:: java


   // The name of your database.
   String db = "mydb0";
   

   // The name of your collection or table.
   String collection = "mycol0";
   

   // The api key of your ObjectRocket user.
   String apiKey = "abcd1234";
   

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/db/" + db + "/collection/" + collection + "/get";
   

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);
   

   // Set the JSON properties of the query.
   JSONObject document = new JSONObject();
   document.put("first_name","Chuck");
   

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey + "&doc=" + document.toJSONString());
   postParamsEntity.setContentType("application/x-www-form-urlencoded");
   

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);
   

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();
   

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...\n");
   HttpResponse response = httpClient.execute(postRequest);


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
.. code-block:: java


   // The name of your database.
   String db = "mydb0";
   

   // The name of your collection or table.
   String collection = "mycol0";

   // The api key of your ObjectRocket user.
   String apiKey = "abcd1234";

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/db/" + db + "/collection/" + collection + "/get";

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);

   // Create an inner JSONObject for the age query.
   JSONObject age = new JSONObject();
   age.put("$lt", 35);

   // Set the JSON properties of the query.
   JSONObject document = new JSONObject();       
   
   document.put("age", age);

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey + "&doc=" + document.toJSONString());
   postParamsEntity.setContentType("application/x-www-form-urlencoded");

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...\n");
   HttpResponse response = httpClient.execute(postRequest);


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
.. code-block:: java

   

   // The name of your collection or table.
   String collection = "mycol0";
   

   // The api key of your ObjectRocket user.
   String apiKey = "abcd1234";
   

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/db/" + db + "/collection/" + collection + "/update";
   

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);
   

   // Set the JSON properties of the object you are replacing in the collection.
   JSONObject document = new JSONObject();
   document.put("first_name","Chuck");
   

   // Create the JSON object for the object that is replacing the object that meets the query object's criteria.
   JSONObject setDocument = new JSONObject();
   setDocument.put("first_name", "Cornelius");
   setDocument.put("last_name", "Vanderbilt");
   setDocument.put("age", 40);
   

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey + "&doc=" + document.toJSONString() + "&set=" + setDocument.toJSONString());
   postParamsEntity.setContentType("application/x-www-form-urlencoded");
   

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);
   

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();
   

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...\n");
   HttpResponse response = httpClient.execute(postRequest);

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
API_KEY - Your ObjectRocket API key.
:QUERY: - A query predicate in the form of a JSON document.
:DB_NAME: - The name of the database that contains the collection that you are deleting the document from.
:COLLECTION_NAME: - The name of the collection or table that you are deleting the document from.

POST URL::

   https://api.objectrocket.com/db/DB_NAME/collection/COLLECTION_NAME/delete

POST Parameter::

   api_key=API_KEY&doc=QUERY The following is an example using the Delete API operation:


Example
~~~~~~~
.. code-block:: java

   // The name of your collection or table.
   String collection = "mycol0";
   

   // The api key of your ObjectRocket user.
   String apiKey = "abcd1234";
   

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/db/" + db + "/collection/" + collection + "/delete";
   

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);
   

   // Create an inner JSONObject for the age query.
   JSONObject age = new JSONObject();
   age.put("$lt", 38);
   

   // Set the JSON properties of the query.
   JSONObject document = new JSONObject();         
   document.put("age", age);
   

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey + "&doc=" + document.toJSONString());
   postParamsEntity.setContentType("application/x-www-form-urlencoded");
   

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);
   

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();
   

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...\n");
   HttpResponse response = httpClient.execute(postRequest);


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
.. code-block:: java

   String apiKey = "abcd1234";
   

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/instance";
   

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);
   

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey);
   postParamsEntity.setContentType("application/x-www-form-urlencoded");
   

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);
   

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();
   

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...\n");
   HttpResponse response = httpClient.execute(postRequest);


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

SERVER STATUS
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
.. code-block:: java

   String apiKey = "abcd1234";
   

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/serverStatus";
   

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);
   

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey);
   postParamsEntity.setContentType("application/x-www-form-urlencoded");
   

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);
   

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();
   

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...\n");
   HttpResponse response = httpClient.execute(postRequest);


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
.. code-block:: java

   String apiKey = "abcd1234";
   

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/spaceusage/get";
   

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);
   

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey);
   postParamsEntity.setContentType("application/x-www-form-urlencoded");
   

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);
   

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();
   

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...\n");
   HttpResponse response = httpClient.execute(postRequest);


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
.. code-block:: java

   String db = "mydb0";
   

   // The name of your collection or table.
   String collection = "mycol0";
   

   // The api key of your ObjectRocket user.
   String apiKey = "abcd1234";
   

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/db/" + db + "/add";
   

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);
   

   // Set the JSON properties of the query.
   JSONObject document = new JSONObject();         
   document.put("myUser123", "myPassword123");
   

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey + "&doc=" + document.toJSONString());
   postParamsEntity.setContentType("application/x-www-form-urlencoded");
   

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);
   

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();
   

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...\n");
   HttpResponse response = httpClient.execute(postRequest);


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

   https://api.objectrocket.com/db

POST Parameter::

   api_key=API_KEY


Example
~~~~~~~
.. code-block:: java

   String apiKey = "abcd1234";
   

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/db";
   

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);
   

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey);
   postParamsEntity.setContentType("application/x-www-form-urlencoded");
   

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);
   

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();
   

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...\n");
   HttpResponse response = httpClient.execute(postRequest);


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
.. code-block:: java

   String apiKey = "abcd1234";
   

   // The ObjectRocket URL for the API operation that you are attempting to complete.
   String postUrl = "https://api.objectrocket.com/profiler/get";
   

   // Create a HTTP Post Request.
   HttpPost postRequest = new HttpPost(postUrl);
   

   // Create an inner JSONObject for the millis query.
   JSONObject millis = new JSONObject();
   millis.put("$gt", 50);
   

   // Set the JSON properties of the query.
   JSONObject document = new JSONObject();         
   document.put("millis", millis);
   

   // Set the post parameters.
   StringEntity postParamsEntity = new StringEntity("api_key=" + apiKey + "&doc=" + document.toJSONString());
   postParamsEntity.setContentType("application/x-www-form-urlencoded");
   

   // Add the post parameters to the post request.
   postRequest.setEntity(postParamsEntity);
   

   // Create the http client.
   DefaultHttpClient httpClient = new DefaultHttpClient();
   

   // Execute the HTTP POST 
   System.out.println("Executing HTTP Post...\n");
   HttpResponse response = httpClient.execute(postRequest);


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
