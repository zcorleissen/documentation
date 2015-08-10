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
        "_id" : ObjectId("55b29160d5d145e1438b4567"),
        "date" : ISODate("2014-05-26T02:00:22Z"),
        "winner" : "Javi",
        "logged" : true,
        "decks" : {
                "first" : [
                        "Dinosaurs",
                        "Plants"
                ],
                "second" : [
                        "Spies",
                        "Zombies"
                ],
                "third" : [
                        "Steampunk",
                        "Wizards"
                ],
                "fourth" : [
                        "Shapeshifters",
                        "Ninjas"
                ]
        },
        "prior_winner" : "Castro",
        "points" : [
                NumberLong(24),
                NumberLong(20),
                NumberLong(20),
                NumberLong(18)
        ],
        "players" : {

                "first" : "Javi",
                "second" : "Seth",
                "third" : "Dave",
                "fourth" : "Castro"
        }
  }

Connecting
----------

Connecting to a replica set:
::
 
 code

Connecting to a sharded instance:
::

 code

Connecting to a sharded instance using SSL:
::

 code


Creating a document
-------------------

Creating and inserting the document:
::

 code

Output from above:
::
 
 code 

Reading documents
-----------------

Finding all documents with a specific field:
::

 code

Output from above:
::

 code

Updating a document
-------------------

Updating a document:
::

 code

Output from above:
::

 code

Deleting a document
-------------------

Deleting a specific document:
::

 code

Output from above:
::

 code

Additional reading
------------------

If you need more help with `Node.js`, here are some links to more documentation:

* `Node.js driver documentation <http://mongodb.github.io/node-mongodb-native/>`_
* `Node.js driver Github <https://github.com/mongodb/node-mongodb-native>`_
* `Getting Started with MongoDB using Node.js <http://docs.mongodb.org/getting-started/node>`_
* `MongoDB 101JS Node.js Course <https://university.mongodb.com/courses/M101JS/about?jmp=docs>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
