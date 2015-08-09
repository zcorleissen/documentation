C# Connection Examples
======================

.. |checkmark| unicode:: U+2713

The C# MongoDB driver as of version 2.0 is asynchronous and uses the same new style of API as the other official drivers.

`C# <http://docs.mongodb.org/ecosystem/drivers/csharp/>`_ at the time of this writing, `07-10-15`, supports the following versions of MongoDB:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :class: compatibility
   :widths: 25 15 15 15

   * - C#/.NET Driver Version
     - MongoDB 2.4
     - MongoDB 2.6
     - MongoDB 3.0

   * - Version 2.0
     - |checkmark|
     - |checkmark|
     - |checkmark|

   * - Version 1.10
     - |checkmark|
     - |checkmark|
     - |checkmark|


Here are the current versions of `.NET` the driver supports:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :class: compatibility
   :widths: 30 10 10 10 10 10

   * - Driver Version
     - .NET 3.5
     - .NET 4.0
     - .NET 4.5
     - Mono 2.10
     - Mono 3.x

   * - Version 2.0
     - 
     - 
     - |checkmark|
     - 
     - |checkmark|

   * - Version 1.10
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|

Installation
------------

Installing the `C# <http://docs.mongodb.org/ecosystem/drivers/csharp/>`_ is fairly simple, as the recommended way is using `nuget <http://www.nuget.org/>`_ to install the `MongoDB Driver <https://www.nuget.org/packages/MongoDB.Driver/>`_.


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

If you need more help with the `C#` driver, here are some links to more documentation:

* `C# 2.0 Quick Start <http://mongodb.github.io/mongo-csharp-driver/2.0/getting_started/quick_tour/>`_
* `C# Documentation <http://api.mongodb.org/csharp/2.0/html/R_Project_CSharpDriverDocs.htm>`_
* `Getting Started with MongoDB using C#/.NET <http://docs.mongodb.org/getting-started/csharp>`_
