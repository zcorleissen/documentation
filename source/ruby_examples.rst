Ruby Driver Examples
====================

.. |checkmark| unicode:: U+2713

The `Ruby driver <https://github.com/mongodb/mongo-ruby-driver>`_ is an official driver maintained by MongoDB. It is written in Ruby, and is currently compatible with the following versions of MongoDB:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :widths: 25 25 25 25
   :class: compatibility

   * - Ruby Driver
     - MongoDB 2.4
     - MongoDB 2.6
     - MongoDB 3.0

   * - 2.0
     - |checkmark|
     - |checkmark|
     - |checkmark|

   * - 1.12
     - |checkmark|
     - |checkmark|
     - |checkmark|

The current version of the Ruby driver supports the following versions of Ruby:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :class: compatibility

   * - Ruby Driver 
     - Ruby 1.8.7
     - Ruby 1.9
     - Ruby 2.0
     - Ruby 2.1
     - JRuby

   * - 2.0
     - 
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|

   * - 1.9
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|

Installation
------------

The Ruby driver is bundled as a gem, and can be installed like so:

.. code-block:: bash

   $ gem install mongo


Example document
----------------

Here's the example document we'll be using:

.. code-block:: javascript

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

.. warning::
  
  When connecting using the MongoDB URI, we highly recommend avoiding usernames with an @ symbol inside. 
  This can break things and cause failures when trying to connect this way.

Connecting to a replica set:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The client has auto-discovery that will find all members of the replica set if not all are provided.

.. code-block:: ruby

   irb(main):001:0> client = Mongo::Client.new(['iad-c17-1.objectrocket.com:49022'],
                             :database => 'db1',
                             :replica_set => '3d62adc37bad4f628cf5e8db921ce445',
                             :user => 'example_username',
                             :password => 'example_password')
   => #<Mongo::Client:0x70225022826660 cluster=iad-c17-1.objectrocket.com:49022, iad-c17-0.objectrocket.com:49022, iad-c17-a.objectrocket.com:49022>

   irb(main):003:0> client.cluster
   => #<Mongo::Cluster:0x70225018290560 servers=[#<Mongo::Server:0x70225014325940 address=iad-c17-0.objectrocket.com:49022>, #<Mongo::Server:0x70225014333140 address=iad-c17-1.objectrocket.com:49022>] topology=Replica Set>

Connecting to a sharded instance with a write concern of 1:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
        
.. code-block:: ruby

   irb(main):004:0> client = Mongo::Client.new(['syd-mongos0.objectrocket.com:35023'],
                             :database => 'db1',
                             :user => 'example_username',
                             :password => 'example_password',
                             :write => { :w => 1 })
   => #<Mongo::Client:0x70225014248860 cluster=syd-mongos0.objectrocket.com:35023>

   irb(main):005:0> client.cluster
   => #<Mongo::Cluster:0x70225022643340 servers=[#<Mongo::Server:0x70225022642320 address=syd-mongos0.objectrocket.com:35023>] topology=Sharded>

Connecting to a sharded instance using SSL:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Make sure to change the port number if using an SSL connection.

.. code-block:: ruby

   irb(main):004:0> client = Mongo::Client.new(['syd-mongos0.objectrocket.com:45023'],
                             :database => 'db1',
                             :user => 'example_username',
                             :password => 'example_password',
                             :ssl => true)
   => #<Mongo::Client:0x70225011707900 cluster=syd-mongos0.objectrocket.com:45023>

   irb(main):005:0> client.cluster
   => #<Mongo::Cluster:0x70225009741280 servers=[#<Mongo::Server:0x70225009738800 address=syd-mongos0.objectrocket.com:45023>] topology=Sharded>

Creating a document
-------------------

Creating and inserting a document:

.. code-block:: ruby



Output from above:

.. code-block:: bash



Reading documents
-----------------

Finding a document with a specific field:

.. code-block:: ruby



Output from above:

.. code-block:: bash



Updating a document
-------------------

Updating a document:

.. code-block:: ruby



Output from above:

.. code-block:: bash



Deleting a document
-------------------

Deleting a document:

.. code-block:: ruby



Output from above:

.. code-block:: bash



Additional reading
------------------

If you need more help with the Ruby driver, links to official documentation are below:

* `Ruby Driver API Documentation <http://api.mongodb.org/ruby/>`_
* `MongoDB Ruby Driver Tutorial <http://docs.mongodb.org/ecosystem/tutorial/ruby-driver-tutorial/>`_
* `Ruby Driver Documentation <http://docs.mongodb.org/ecosystem/drivers/ruby/>`_
* `Ruby Driver Github <https://github.com/mongodb/mongo-ruby-driver>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
