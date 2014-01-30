Data Access and Connectivity
=======================

Overview
----------------

Each ObjectRocket instance has it's own unique connect string as shown on the `instances`_ page.  Connect strings are shown for standard and SSL based connections.  For sharded instance plans, the connect string maps to a ObjectRocket load balancer, and thus specifying a array of MongoS server strings is not required for high availability.  Applications can simply know about the very simple single connect string and availability and scalability is handled on the ObjectRocket service.

Shell Access
----------------

Shell access is just like any other MongoDB system.  Use the connect string as an argument to the mongo shell.  Pass the database, user, and password for authentication.

For example:

.. code-block:: javascript

    $>mongo w-mongos0.objectrocket.com:99929/users -u testuser -p mytestpassword
    >db.users.insert({ login: 'bob', password: 'secret' });
    >db.users.update({ login: 'bob'},{ $set: {'password': 'notsosecret'});
    >db.users.findOne({ login: 'bob'});

or another example:

.. code-block:: javascript

    $>mongo w-mongos0.objectrocket.com:99929
    >use users
    >db.auth("testuser","mytestpassword");
    >db.users.insert({ login: 'bob', password: 'secret' });
    >db.users.update({ login: 'bob'},{ $set: {'password': 'notsosecret'});
    >db.users.findOne({ login: 'bob'});

Native Drivers
----------------

ObjectRocket supports ALL native MongoDB driver access.  Simply use the connect string in the application.

For example, in python:

.. code-block:: python

    import pprint
    import pymongo, pymongo.objectid
    import sys

    ## Connect string
    ## Server: "w-mongos0.objectrocket.com:99929",
    ## Database: "users"
    ## Write concern: 1 (acknowledge writes)
    db = 'mongodb://testuser:mytestpassword@w-mongos0.objectrocket.com:99929/users?w=1'

    ## Connect to MongoDB, create a handle for the "users" database
    try:
        connection = pymongo.Connection(db)
        db = connection['users']
    except Exception, ex:
        print "Couldn't connect, exception is: %s" % ex
        sys.exit(1)

    ## Define a simple document
    doc = {'login': 'bob',
           'password': 'secret'}

    ## Insert this document into the "accounts" collection
    try:
      db.accounts.insert(doc)
    except Exception, ex:
      print "Unable to insert, exception is: %s" % ex

    ## Update the user's password
    db.accounts.update({'login': 'bob'},
                       {"$set": {'password': 'notsosecret'}})

    ## Find our user and store the returned document to variable "a"
    user = db.accounts.find_one({'login': 'bob'})

    ## Pretty-print JSON document returned from MongoDB
    pprint.pprint(user)

    ## Remove our user's document by _id
    db.accounts.remove({"_id": pymongo.objectid.ObjectId(user['_id'])})

Or in node.js:

.. code-block:: node.js

    var Server = require('mongodb').Server;
    var Db = require('mongodb').Db;

    new Db('users',
    new Server("w-mongos0.objectrocket.com", 99929, {auto_reconnect:true}), {safe:true}).open(function(err, db) {
        if (err) throw err;

        db.authenticate('testuser', 'mytestpassword', function(autherr, result) {
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

Data Migration
--------------

Not all projects start with an empty database on ObjectRocket, thus migration of data from another MongoDB database is key. Data may be migrated to ObjectRocket in a variety of ways:

Copy Database
~~~~~~~~~~~~~

Copy Database is a unique feature to ObjectRocket. A request is made via the web UI and an agent process kicks off a copy database in the background.  This option is very easy to use. The application accessing the data would not be able to access the data during this process.

Mongorestore
~~~~~~~~~~~~

Data may be dumped from a source system using mongodump, then restored to the ObjectRocket system via mongorestore.  This option has the benefit of being able to copy over multiple databases at once. The application accessing the data would not be able to access the data during this process.

Replica Migration
~~~~~~~~~~~~~~~~~

This mechanism is used in conjunction with the support team.  The process ensures very very low amounts of interruption to the system for the cutover to ObjectRocket.  Contact support@objectrocket for details on using this approach.

Customer
~~~~~~~~

Many customers have facilities in thier applications to have two systems running in parallel using various schemes.  These processes are unique to each customer.  ObjectRocket provides a new instance and the customer is generally responsible for ensuring the data migration is completed properly.



