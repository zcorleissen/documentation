Go Connection Examples
======================

.. |checkmark| unicode:: U+2713

The Go MongoDB driver isn't an officially supported driver at the moment, and as such is maintained by the community. It's called `mgo <http://labix.org/mgo>`_.

`mgo <http://labix.org/mgo>`_ at the time of this writing, `07-10-15`, supports the following versions of MongoDB:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :class: compatibility

   * - Go Driver Version
     - MongoDB 2.4
     - MongoDB 2.6
     - MongoDB 3.0

   * - v2
     - |checkmark|
     - |checkmark|
     - |checkmark|

Here are the current versions of `golang` the driver supports:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :class: compatibility
   :widths: 40 20 20 20 20

   * - Go Driver Version
     - go1.1
     - go1.2
     - go1.3
     - go1.4

   * - v2
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|

Installation
------------

Installing `mgo <http://labix.org/mgo>`_ is simple, using the usual go get procedure:

.. code-block:: bash

   $ go get gopkg.in/mgo.v2

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

.. code-block:: go
 
   code

Connecting to a sharded instance:

.. code-block:: go

   code

Connecting to a sharded instance using SSL:

.. code-block:: go

   code


Creating a document
-------------------

Creating and inserting the document:

.. code-block:: go

   code

Output from above:

.. code-block:: go
 
   code


Reading documents
-----------------

Finding all documents with a specific field:

.. code-block:: go

   code

Output from above:

.. code-block:: go

   code

Updating a document
-------------------

Updating a document:

.. code-block:: go

   code

Output from above:

.. code-block:: go

   code

Deleting a document
-------------------

Deleting a specific document:

.. code-block:: go

   code

Output from above:

.. code-block:: go

   code

Additional reading
------------------

If you need more help with `mgo`, here are some links to more documentation:

* `mgo GoDoc documentation <http://godoc.org/labix.org/v2/mgo>`_
* `mgo Mailing List <https://groups.google.com/forum/#!forum/mgo-users>`_
* `mgo Github <https://github.com/go-mgo/mgo>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
