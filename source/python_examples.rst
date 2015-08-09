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

Older versions of MongoDB aren't supported, so please keep that in mind.

Language Compatibility
~~~~~~~~~~~~~~~~~~~~~~

If you're using a specific version of Python, here are the recommended driver versions to use with each:

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

Installation is simple and uses the expected `pip` command:

.. code-block:: bash

   pip install pymongo

However you can also install it using `setuptools`:

.. code-block:: bash
 
   easy_install pymongo


Then you can import it like anything else:

.. code-block:: python

   from pymongo import MongoClient


Example document
----------------

Here's the example document we'll be using:

.. code-block:: javascript

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

.. code-block:: python
 
   code

Connecting to a sharded instance:

.. code-block:: python

   code

Connecting to a sharded instance using SSL:

.. code-block:: python

   code


Creating a document
-------------------

Creating and inserting a document:

.. code-block:: python

   code

Output from above:

.. code-block:: python

   code

Reading documents
-----------------

Finding all documents with a specific field:

.. code-block:: python

   code

Output from above:

.. code-block:: python

   code

Updating a document
-------------------

Updating a document:

.. code-block:: python

   code

Output from above:

.. code-block:: python

   code

Deleting a document
-------------------

Deleting a document:

.. code-block:: python

   code

Output from above:

.. code-block:: python

   code

Additional reading
------------------

If you need more help with PyMongo, links to official documentation are below:

* `PyMongo Github <https://github.com/mongodb/mongo-python-driver>`_
* `MongoDB Python Driver documentation <http://docs.mongodb.org/ecosystem/drivers/python/>`_
* `MongoDB Python Driver Tutorial <http://api.mongodb.org/python/current/tutorial.html>`_
* `Getting Started with MongoDB (Python Edition) <http://docs.mongodb.org/getting-started/python>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
