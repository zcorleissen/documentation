Python Connection Examples
==========================

`PyMongo <http://docs.mongodb.org/ecosystem/drivers/python/>`_ is the recommended Python driver for working with MongoDB. Here's the compatibility breakdown:

.. |checkmark| unicode:: U+2713

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

Here are the recommended driver versions to use with each version of Python:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :class: compatibility-large

   * - Python Driver 
     - Python 2.7, PyPy
     - Python 3.1
     - Python 3.2, PyPy3
     - Python 3.3
     - Python 3.4

   * - 3.0
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


Installation
------------

Installation is simple and uses the expected `pip` command:

.. code-block:: bash

   $ sudo pip install pymongo

However you can also install it using `setuptools`:

.. code-block:: bash
 
   $ sudo easy_install pymongo


Then you can import it like anything else:

.. code-block:: python

   from pymongo import MongoClient


Example document
----------------

Here's the example document we'll be using:

.. code-block:: javascript

  { "start": datetime.utcnow(),
    "end": datetime(2015, 8, 22, 16, 22, 38),
    "location": "Texas",
    "official_game": False,
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

.. warning::
  
  When connecting using the MongoDB URI, we highly recommend avoiding usernames with an @ symbol inside. 
  This can break things and cause failures when trying to connect this way.

Connecting to a replica set:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python

  import pymongo

  settings = {
      'host': 'dfw-c9-1.objectrocket.com:37143,dfw-c9-0.objectrocket.com:37143',
      'database': 'example_db',
      'username': 'example',
      'pnts""Plants""Plants"assword': 'example_pass',
      'options': 'replicaSet=c74b5276378ed3bd70cba37a3ac45fea'
  }

  try:
      conn = pymongo.MongoClient("mongodb://{username}:{password}@{host}/{database}?{options}".format(**settings))
  except Exception as ex:
      print "Error:", ex
      exit('Failed to connect, terminating.')

Connecting to a sharded instance with a write concern of 1:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
        
.. code-block:: python

  import pymongo

  settings = {
      'host': 'iad-mongos0.objectrocket.com:15014/example_db',
      'database': 'example_db',
      'username': 'example',
      'password': 'example_pass',
      'options': 'w=1'
  }
  
  try:
      conn = pymongo.MongoClient("mongodb://{username}:{password}@{host}/{database}?{options}".format(**settings))
  except Exception as ex:
      print "Error:", ex
      exit('Failed to connect, terminating.')

Connecting to a sharded instance using SSL:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python

  import pymongo

  settings = {
      'host': 'iad-mongos0.objectrocket.com:15014',
      'database': 'example_db',
      'username': 'example',
      'password': 'example_pass',
      'options': 'ssl=true'
  }
  try:
      conn = pymongo.MongoClient("mongodb://{username}:{password}@{host}/{database}?{options}".format(**settings))
  except Exception as ex:
      print "Error:", ex
      exit('Failed to connect, terminating.')


Creating a document
-------------------

Creating and inserting a document:

.. code-block:: python

  import pymongo
  from datetime import datetime

  settings = {
      'host': 'iad-mongos0.objectrocket.com:15014',
      'database': 'example_db',
      'username': 'example',
      'password': 'example_pass',
      'options': 'w=1'
  }

  example_doc = { "start": datetime.utcnow(),
      "end": datetime(2015, 8, 22, 16, 22, 38),
      "location": "Texas",
      "official_game": False,
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

  try:
      conn = pymongo.MongoClient("mongodb://{username}:{password}@{host}/{database}?{options}".format(**settings))
  except Exception as ex:
      print "Error:", ex
      exit('Failed to connect, terminating.')

  db = conn.example_db
  collection = db.test_collection

  doc_id = collection.insert_one(example_doc).inserted_id

  print "Here's the _id of the doc I inserted: %s." % doc_id


Output from above:

.. code-block:: bash

  ipython pymongo_example.py

  Here's the _id of the doc I inserted: 55ce1520f643f056fd1c9887.


Reading documents
-----------------

Finding a document with a specific field:

.. code-block:: python

    import pymongo
    from pprint import pprint

    settings = {
        'host': 'iad-mongos0.objectrocket.com:15014',
        'database': 'example_db',
        'username': 'example',
        'password': 'example_pass',
        'options': 'w=1'
    }

    try:
        conn = pymongo.MongoClient("mongodb://{username}:{password}@{host}/{database}?{options}".format(**settings))
    except Exception as ex:
        print "Error:", ex
        exit('Failed to connect, terminating.')

    db = conn.example_db
    collection = db.test_collection
    results = collection.find_one({"winner" : "Javi"})
    print "Here's a doc: "
    pprint(results)

Output from above:

.. code-block:: bash

    Here's a doc:
    {u'_id': ObjectId('55ce1520f643f056fd1c9887'),
     u'end': datetime.datetime(2015, 8, 22, 16, 22, 38),
     u'location': u'Texas',
     u'official_game': False,
     u'players': [{u'decks': [u'Dinosaurs', u'Plants'],
                   u'name': u'Javi',
                   u'place': 1,
                   u'points': 24},
                  {u'decks': [u'Spies', u'Zombies'],
                   u'name': u'Seth',
                   u'place': 2,
                   u'points': 20},
                  {u'decks': [u'Steampunk', u'Wizard'],
                   u'name': u'Dave',
                   u'place': 2,
                   u'points': 20},
                  {u'decks': [u'Shapeshifters', u'Ninjas'],
                   u'name': u'Castro',
                   u'place': 4,
                   u'points': 18}],
     u'start': datetime.datetime(2015, 8, 14, 16, 19, 44, 868000),
     u'winner': u'Javi'}

Updating a document
-------------------

Updating a document:

.. code-block:: python

    import pymongo
    from pprint import pprint

    settings = {
        'host': 'iad-mongos0.objectrocket.com:15014',
        'database': 'example_db',
        'username': 'example',
        'password': 'example_pass',
        'options': 'w=1'
    }

    try:
        conn = pymongo.MongoClient("mongodb://{username}:{password}@{host}/{database}?{options}".format(**settings))
    except Exception as ex:
        print "Error:", ex
        exit('Failed to connect, terminating.')

    db = conn.example_db
    collection = db.test_collection
    results = collection.find_one({"winner" : "Javi"})
    print "Here's the original doc: "
    pprint(results)

    update_doc = collection.update_one({"winner" : "Javi"},{"$set": {"winner" : "Seth"}})
    updated_doc = collection.find_one({"winner" : "Seth"})
    print "Here's how many documents I found: "
    pprint(update_doc.matched_count)
    print "Here's the new doc: "
    pprint(updated_doc)

Output from above:

.. code-block:: bash

    $ ipython update_doc.py
    Here's the original doc:
    {u'_id': ObjectId('55ce1d01f643f05a6ca695d4'),
     u'end': datetime.datetime(2015, 8, 22, 16, 22, 38),
     u'location': u'Texas',
     u'official_game': False,
     u'players': [{u'decks': [u'Dinosaurs', u'Plants'],
                   u'name': u'Javi',
                   u'place': 1,
                   u'points': 24},
                  {u'decks': [u'Spies', u'Zombies'],
                   u'name': u'Seth',
                   u'place': 2,
                   u'points': 20},
                  {u'decks': [u'Steampunk', u'Wizard'],
                   u'name': u'Dave',
                   u'place': 2,
                   u'points': 20},
                  {u'decks': [u'Shapeshifters', u'Ninjas'],
                   u'name': u'Castro',
                   u'place': 4,
                   u'points': 18}],
     u'start': datetime.datetime(2015, 8, 14, 16, 53, 21, 950000),
     u'winner': u'Javi'}
    Here's how many documents I found:
    1
    Here's the new doc:
    {u'_id': ObjectId('55ce1d01f643f05a6ca695d4'),
     u'end': datetime.datetime(2015, 8, 22, 16, 22, 38),
     u'location': u'Texas',
     u'official_game': False,
     u'players': [{u'decks': [u'Dinosaurs', u'Plants'],
                   u'name': u'Javi',
                   u'place': 1,
                   u'points': 24},
                  {u'decks': [u'Spies', u'Zombies'],
                   u'name': u'Seth',
                   u'place': 2,
                   u'points': 20},
                  {u'decks': [u'Steampunk', u'Wizard'],
                   u'name': u'Dave',
                   u'place': 2,
                   u'points': 20},
                  {u'decks': [u'Shapeshifters', u'Ninjas'],
                   u'name': u'Castro',
                   u'place': 4,
                   u'points': 18}],
     u'start': datetime.datetime(2015, 8, 14, 16, 53, 21, 950000),
     u'winner': u'Seth'}

Deleting a document
-------------------

Deleting a document:

.. code-block:: python

    import pymongo
    from pprint import pprint

    settings = {
        'host': 'iad-mongos0.objectrocket.com:15014',
        'database': 'example_db',
        'username': 'example',
        'password': 'example_pass',
        'options': 'w=1'
    }

    try:
        conn = pymongo.MongoClient("mongodb://{username}:{password}@{host}/{database}?{options}".format(**settings))
    except Exception as ex:
        print "Error:", ex
        exit('Failed to connect, terminating.')

    db = conn.example_db
    collection = db.test_collection
    results = collection.find_one({"winner" : "Seth"})
    print "Here's the doc I found: "
    pprint(results)

    deleted = collection.delete_one({"winner" : "Seth"})
    print "Here's how many documents I deleted: "
    pprint(deleted.deleted_count)

Output from above:

.. code-block:: bash

    $ ipython delete_doc.py
    Here is the doc I found:
    {u'_id': ObjectId('55ce1d01f643f05a6ca695d4'),
     u'end': datetime.datetime(2015, 8, 22, 16, 22, 38),
     u'location': u'Texas',
     u'official_game': False,
     u'players': [{u'decks': [u'Dinosaurs', u'Plants'],
                   u'name': u'Javi',
                   u'place': 1,
                   u'points': 24},
                  {u'decks': [u'Spies', u'Zombies'],
                   u'name': u'Seth',
                   u'place': 2,
                   u'points': 20},
                  {u'decks': [u'Steampunk', u'Wizard'],
                   u'name': u'Dave',
                   u'place': 2,
                   u'points': 20},
                  {u'decks': [u'Shapeshifters', u'Ninjas'],
                   u'name': u'Castro',
                   u'place': 4,
                   u'points': 18}],
     u'start': datetime.datetime(2015, 8, 14, 16, 53, 21, 950000),
     u'winner': u'Seth'}
    Here's how many documents I deleted:
    1

Additional reading
------------------

If you need more help with PyMongo, links to official documentation are below:

* `PyMongo Github <https://github.com/mongodb/mongo-python-driver>`_
* `MongoDB Python Driver documentation <http://docs.mongodb.org/ecosystem/drivers/python/>`_
* `MongoDB Python Driver Tutorial <http://api.mongodb.org/python/current/tutorial.html>`_
* `Getting Started with MongoDB (Python Edition) <http://docs.mongodb.org/getting-started/python>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
