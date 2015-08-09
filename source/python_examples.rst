Python Connection Examples
==========================

`PyMongo <http://docs.mongodb.org/ecosystem/drivers/python/>`_ is the recommended Python driver for working with MongoDB. Here's the compatibility breakdown:

.. |checkmark| unicode:: U+2713

Python Driver Compatibility
---------------------------

MongoDB Compatibility
~~~~~~~~~~~~~~~~~~~~~

Here are the recommended versions of each driver to use with a specific version of MongoDB:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :widths: 25 25 25 25
   :class: compatibility

   * - Python Driver
     - MongoDB 2.4
     - MongoDB 2.6
     - MongoDB 3.0

   * - 3.0
     - |checkmark|
     - |checkmark|
     - |checkmark|

   * - 2.8
     - |checkmark|
     - |checkmark|
     - |checkmark|

.. include:: /includes/extracts/python-driver-compatibility-full-mongodb.rst

.. include:: /includes/older-server-versions-unsupported.rst

Language Compatibility
``````````````````````

.. include:: /includes/extracts/python-driver-compatibility-matrix-language.rst

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :class: compatibility-large

   * - Python Driver 
     - Python 2.4
     - Python 2.5, Jython 2.5
     - Python 2.6
     - Python 2.7, PyPy
     - Python 3.1
     - Python 3.2, PyPy3
     - Python 3.3
     - Python 3.4

   * - 3.0
     - 
     - 
     - |checkmark|
     - |checkmark|
     - 
     - |checkmark|
     - |checkmark|
     - |checkmark|

   * - 2.8
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|


Installation
------------


::


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

Switching to a shell, the document you instered should look just like the above example.

Reading documents
-----------------

finding all documents with a specific field:
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

Deleting a document
-------------------

Deleting a specific document:
::

 code

Output from above:
::

 code

This is the end, I need official links here, to do later.
