Go Connection Examples
======================

The Go MongoDB driver isn't an officially supported driver at the moment, and as such is maintained by the community. It's called `mgo <http://labix.org/mgo>`_, and as of `07-09-2015` version v2 of the driver supports MongoDB 2.4, 2.6, and 3.0. It does not support older versions of MongoDB.

`mgo <http://labix.org/mgo>`_ v2 is currently compatible with `go1.1`, `go1.2`, `go1.3`, and `go1.4`.

Installation
------------

Installing `mgo <http://labix.org/mgo>`_ is simple, using the usual go get procedure:

::

  go get gopkg.in/mgo.v2

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
