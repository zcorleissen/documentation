Node.js Connection Examples
===========================

.. |checkmark| unicode:: U+2713

The `Node.js driver <https://github.com/mongodb/node-mongodb-native>`_ for MongoDB is an officially supported driver as of Spring 2012. It's written in JavaScript and was designed with simplicity in mind. It can be used on it's own, but is commonly used in conjunction with an object mapping library like `Mongoose <http://mongoosejs.com/>`_.

The `Node.js driver <https://github.com/mongodb/node-mongodb-native>`_ at the time of this writing, `07-10-15`, supports the following versions of MongoDB:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :widths: 25 25 25 25
   :class: compatibility

   * - Node.js Driver
     - MongoDB 2.4
     - MongoDB 2.6
     - MongoDB 3.0

   * - >=2.0.14
     - |checkmark|
     - |checkmark|
     - |checkmark|

   * - >=1.4.29
     - |checkmark|
     - |checkmark|
     - |checkmark|

Here are the current versions of `Node.js` the driver supports:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :class: compatibility

   * - Node.js Driver 
     - Node.js v0.8.X
     - Node.js v0.10.X
     - Node.js v0.11.X unstable

   * - 2.0.X
     - |checkmark|
     - |checkmark|
     - |checkmark|

   * - >=1.4.18
     - |checkmark|
     - |checkmark|
     - |checkmark|

Installation
------------

Installing the `Node.js driver <https://github.com/mongodb/node-mongodb-native>`_ is simple, using the usual npm install procedure:

::

  npm install mongodb

Example document
----------------

Here's the example document we'll be using:
::

   {
       "start": "2015-09-02T22:46:30.782Z",
       "end": "2016-09-02T22:46:30.782Z",
       "location": "Texas",
       "official_game": false,
       "winner": "Javi",
       "players": [
           {
               "name": "Javi",
               "decks": [
                   "Dinosaurs",
                   "Plants"
               ],
               "points": 24,
               "place": 1
           },
           {
               "name": "Seth",
               "decks": [
                   "Spies",
                   "Zombies"
               ],
               "points": 20,
               "place": 2
           },
           {
               "name": "Dave",
               "decks": [
                   "Steampunk",
                   "Wizard"
               ],
               "points": 20,
               "place": 2
           },
           {
               "name": "Castro",
               "decks": [
                   "Shapeshifters",
                   "Ninjas"
               ],
               "points": 18,
               "place": 4
           }
       ]
   }

Connecting
----------

Connecting to a replica set:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: javascript

  // Require mongodb
  var MongoClient = require('mongodb').MongoClient;

  // Connect
  MongoClient.connect('mongodb://example:example_pass@dfw-c9-1.objectrocket.com:37143,dfw-c9-0.objectrocket.com:37143/example_db?replicaSet=c74b5276378ed3bd70cba37a3ac45fea', function(err, db) {
    if(!err) {
      console.log("We are connected");
    } else {
      console.log(err);
    }
    process.exit();
  });

Output from above:

.. code-block:: bash

  $ node repl_connect_example.js
  We are connected

Connecting to a sharded instance:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: javascript

  // Require mongodb
  var MongoClient = require('mongodb').MongoClient;

  // Connect
  MongoClient.connect("mongodb://example:example_pass@iad-mongos0.objectrocket.com:15014/example_db", function(err, db) {
    if(!err) {
      console.log("We are connected");
    } else {
      console.log(err);
    }
    process.exit();
  });

Output from above:

.. code-block:: bash

  $ node sharded_connect_example.js
  We are connected

Connecting to a sharded instance with SSL:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: javascript

  // Require mongodb
  var MongoClient = require('mongodb').MongoClient;

  // Connect
  MongoClient.connect("mongodb://example:example_pass@iad-mongos0.objectrocket.com:25014/example_db?ssl=true", function(err, db) {
    if(!err) {
      console.log("We are connected");
    } else {
      console.log(err);
    }
    process.exit();
  });

Output from above:

.. code-block:: bash

  $ node ssl_sharded_connect_example.js
  We are connected


Creating a document
-------------------

Creating and inserting the document:

.. code-block:: javascript

  // Require mongodb
  var MongoClient = require('mongodb').MongoClient;

  // Connect
  MongoClient.connect("mongodb://example:example_pass@iad-mongos0.objectrocket.com:15014/example_db", function(err, db) {
    if(!err) {
      console.log("We are connected");
    } else {
      return console.dir(err);
    };
    var example_doc = {
    "start" : new Date(),
    "end" : new Date(2015, 9, 28, 14, 17, 23, 0),
    "location" : "Texas",
    "official_game" : false,
    "Winner" : "Javi",
    "players" : [
          {
      "name": "Javi",
              "decks": [
                  "Dinosaurs",
                  "Plants"
              ],
              "points": 24,
              "place": 1
          },
          {
              "name": "Seth",
              "decks": [
                  "Spies",
                  "Zombies"
              ],
              "points": 20,
              "place": 2
          },
          {
              "name": "Dave",
              "decks": [
                  "Steampunk",
                  "Wizard"
              ],
              "points": 20,
              "place": 2
          },
          {
              "name": "Castro",
              "decks": [
                  "Shapeshifters",
                  "Ninjas"
              ],
              "points": 18,
              "place": 4
          }
      ]
    };
    var collection = db.collection('example_collection');
    collection.insert(example_doc, {w:1}, function(err, result) {
      if(!err) {
        console.log("Inserted a doc!");
        process.exit();
      } else {
        return console.dir(err);
      }
    });
  });

Output from above:

.. code-block:: bash
 
 $ node inserting_doc.js
 We are connected
 Inserted a doc!

Reading documents
-----------------

Finding all documents with a specific field:

.. code-block:: javascript

 code

Output from above:

.. code-block:: bash

 code

Updating a document
-------------------

Updating a document:

.. code-block:: javascript

 code

Output from above:

.. code-block:: bash

 code

Deleting a document
-------------------

Deleting a specific document:

.. code-block:: javascript

 code

Output from above:

.. code-block:: bash

 code

Additional reading
------------------

If you need more help with `Node.js`, here are some links to more documentation:

* `Node.js driver documentation <http://mongodb.github.io/node-mongodb-native/>`_
* `Node.js driver Github <https://github.com/mongodb/node-mongodb-native>`_
* `Getting Started with MongoDB using Node.js <http://docs.mongodb.org/getting-started/node>`_
* `MongoDB 101JS Node.js Course <https://university.mongodb.com/courses/M101JS/about?jmp=docs>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
