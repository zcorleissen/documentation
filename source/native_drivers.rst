Connecting via Native MongoDB Drivers
=====================================

Overview
--------

ObjectRocket allows for access via native MongoDB drivers just like 
any other MongoDB database. ObjectRocket also terminates SSL 
connections so clients compiled with SSL support can access the 
service via SSL as well.

Each instance has its own unique connect string. The connect string 
assigned to the instance can be found in the 'driver' column at 
https://app.objectrocket.com/instances/. A unique 
port is assigned for the plain text and SSL drivers. The SSL port is 
always 10000 higher than the plain text port.


Python
------

.. code-block:: python

   import pprint
   import pymongo
   import sys

   ## Connect string
   ## Server: "localhost:27017",
   ## Database: "users"
   db_uri = 'mongodb://rocketuser:rocketpass@localhost:27017/users'

   ## Connect to MongoDB, create a handle for the "users" database
   try:
       connection = pymongo.MongoClient(db_uri)
       db = connection['users']
   except Exception as ex:
       print("Couldn't connect, exception is: %s" % ex)
       sys.exit(1)

   ## Define a simple document
   doc = {'login': 'bob',
          'password': 'secret'}

   ## Insert this document into the "accounts" collection
   db.accounts.insert(doc)

   ## Update the user's password
   db.accounts.update({'login': 'bob'},
                      {"$set": {'password': 'notsosecret'}})

   ## Find our user and store the returned document to variable "a"
   user = db.accounts.find_one({'login': 'bob'})

   ## Pretty-print JSON document returned from MongoDB
   pprint.pprint(user)

   ## Remove our user's document by _id
   db.accounts.remove({"_id": user['_id']})


Node.js
-------

.. code-block:: javascript

   var Server = require('mongodb').Server;
   var Db = require('mongodb').Db;   

   new Db('users',
     new Server("localhost", 27017, {auto_reconnect:true}), {safe:true}).open(function(err, db) {
       if (err) throw err;   

       db.authenticate('rocketuser', 'rocketpass', function(autherr, result) {
         if (autherr) throw autherr;   

         db.collection('accounts', function(colerr, collection) {
             if (colerr) throw colerr;   

             // Define a simple JSON document
             var doc = {'login': 'bob', 'password': 'secret'}   

             // Insert our document
             collection.insert(doc, {}, function(){});   

             // Change our password
             collection.update({'login': 'bob'}, 
                               {'$set': {'password': 'notsosecret'}}, 
                               function(){});   

             // Retrieve our document
             collection.findOne({}, function(finderr, docs) {
               if (finderr) {
                 console.log(finderr);
               } else {
                 return console.log(docs);
               };
             });   

         });   

       });   

   });


C#
--

Getting the Driver
^^^^^^^^^^^^^^^^^^

The official C# driver for MongoDB can be obtained as an exe or msi 
at http://driver-downloads.mongodb.org/dotnet/index.html

You can also grab it from within Visual Studio using
`NuGet <http://nuget.codeplex.com/wikipage?title=Getting%20Started>`_
by either using the graphical tool and searching for "mongocsharpdriver"
or opening the Package Manager Console and 
executing::

   Install-Package mongocsharpdriver

If you're a `Chocolatey <http://chocolatey.org/>`_ user, it's available with::

   c:\> cinst mongodb

For advanced use cases, or to modify the driver, you can also download
`the source code <https://github.com/mongodb/mongo-csharp-driver>`_.

Connection String
^^^^^^^^^^^^^^^^^

C# uses a standard connection string as shown in the example below

.. code-block:: c#

   var connectionString = "mongodb://bob:supersecretpassword@e-mongos0.objectrocket.com:10892/csharptest";

bob is our username and supersecretpassword is our password. You can 
create a new user and password to connect with by navigating to your 
`instance <https://app.objectrocket.com/instances>`_, selecting the
database you would like to work with, and  clicking the Users tab.

e-mongos0.objectrocket.com is the hostname and :10892 denotes the port.
These can both be found by navigating to your
`instances page <https://app.objectrocket.com/instances>`_.

/chsarptest will be the name of the database you would like to connect to.

Code Example
^^^^^^^^^^^^

.. code-block:: c#

   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using System.Threading.Tasks;
   using MongoDB.Bson;
   using MongoDB.Driver;
   using MongoDB.Driver.Builders;   

   namespace ConsoleApplication1
   {
       public class Person
       {
           public ObjectId Id { get; set; }
           public string Name { get; set; }
           public string Job { get; set; }
       }   
   
   

       class Program
       {
           static void Main(string[] args)
           {   
   

               /// Connect to the csharptest database on my objectrocket instance 
               var connectionString = "mongodb://bob:supersecretpassword@e-mongos0.objectrocket.com:10892/csharptest";
               var client = new MongoClient(connectionString);
               var server = client.GetServer();
               var database = server.GetDatabase("csharptest");
               var collection = database.GetCollection("people");   

               /// Add a new document to the "people" collection with Name : Alice
               var person = new Person { Name = "Alice" };
               collection.Insert(person);
               var id = person.Id;   

               /// Query for just one result based on the ID of person  (Alice )       
               var query = Query.EQ(e => e.Id, id);
               person = collection.FindOne(query);   

               /// Add the Job key to the Alice document with a value of courier
               person.Job = "courier";
               collection.Save(person);   

               /// Update the the Name value to Bob 
               var update = Update.Set(e => e.Name, "Bob");
               collection.Update(query, update);   

               /// Drops ( deletes ) the people collection
              collection.Drop();   
   

           }
       }
   }

Additional Resources
^^^^^^^^^^^^^^^^^^^^

As the C# Driver is officially supported by the folks over at 10Gen, 
you'll find a wealth of additional documentation on its
`official page <http://docs.mongodb.org/ecosystem/drivers/csharp/>`_.
Some great places to get started digging deeper are:

`Getting Started Guide <http://docs.mongodb.org/ecosystem/tutorial/getting-started-with-csharp-driver/>`_

`Official Driver API Documentation <http://api.mongodb.org/csharp/current/>`_

`Serializing Documents With The Driver <http://docs.mongodb.org/ecosystem/tutorial/serialize-documents-with-the-csharp-driver/#serialize-documents-with-the-csharp-driver>`_

For complex questions that are not covered in the basic documentation,
you may want to ask in the very active
`Google Group <https://groups.google.com/forum/?fromgroups#!forum/mongodb-user>`_
for the project.
