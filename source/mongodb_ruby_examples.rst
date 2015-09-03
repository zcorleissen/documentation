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

   #!/usr/bin/env ruby
   require 'mongo'
   
   # Turn off debug-mode
   Mongo::Logger.logger.level = Logger::WARN
   
   client_host = ['iad-c17-1.objectrocket.com:12345']
   client_options = {
     database: 'db1',
     replica_set: '3d62adc37bad4f628cf5e8db921ce445',
     user: 'example_username',
     password: 'example_password'
   }
   
   client = Mongo::Client.new(client_host, client_options)
   
   puts('Client Connection: ')
   puts(client.cluster.inspect)
   puts
   puts('Collection Names: ')
   puts(client.database.collection_names)

Output from above:

.. code-block:: bash

   Client Connection:
   #<Mongo::Cluster:0x70194211277920 servers=[#<Mongo::Server:0x70194203419280 address=iad-c17-0.objectrocket.com:12345>, #<Mongo::Server:0x70194203425760 address=iad-c17-1.objectrocket.com:49022>] topology=Replica Set>
   
   Collection Names:
   objectrocket.init
   collection_1
   collection_2

Connecting to a sharded instance with a write concern of 1:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: ruby

   #!/usr/bin/env ruby
   require 'mongo'
   
   # Turn off debug-mode
   Mongo::Logger.logger.level = Logger::WARN
   
   client_host = ['syd-mongos0.objectrocket.com:12345']
   client_options = {
     database: 'db1',
     user: 'example_username',
     password: 'example_password',
     write: { w: 1 }
   }
   
   client = Mongo::Client.new(client_host, client_options)
   
   puts('Client Connection: ')
   puts(client.cluster.inspect)
   puts
   puts('Collection Names: ')
   puts(client.database.collection_names)

Output from above:

.. code-block:: bash

  Client Connection:
  #<Mongo::Cluster:0x70257105430280 servers=[#<Mongo::Server:0x70257105429580 address=syd-mongos0.objectrocket.com:12345>] topology=Sharded>

  Collection Names:
  objectrocket.init
  collection_1
  collection_2

Connecting to a sharded instance using SSL:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Make sure to change the port number when using an SSL connection.

.. code-block:: ruby

   #!/usr/bin/env ruby
   require 'mongo'
   
   # Turn off debug-mode
   Mongo::Logger.logger.level = Logger::WARN
   
   client_host = ['syd-mongos0.objectrocket.com:12345']
   client_options = {
     database: 'db1',
     user: 'example_username',
     password: 'example_password',
     ssl: true
   }
   
   client = Mongo::Client.new(client_host, client_options)
   
   puts('Client Connection: ')
   puts(client.cluster.inspect)
   puts
   puts('Collection Names: ')
   puts(client.database.collection_names)

Output from above:

.. code-block:: bash

   Client Connection:
  #<Mongo::Cluster:0x70323940844040 servers=[#<Mongo::Server:0x70323945742140 address=syd-mongos0.objectrocket.com:12345>] topology=Sharded>

  Collection Names:
  objectrocket.init
  collection_1
  collection_2

Creating a document
-------------------

Creating and inserting a document:

.. code-block:: ruby

   #!/usr/bin/env ruby
   require 'mongo'
   
   # Turn off debug-mode
   Mongo::Logger.logger.level = Logger::WARN
   
   client_host = ['iad-c17-1.objectrocket.com:12345']
   client_options = {
     database: 'db1',
     user: 'example_username',
     password: 'example_password'
   }
   
   client = Mongo::Client.new(client_host, client_options)
  
   example_doc = {
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
   
   # Insert our example_doc
   result = client[:pokemon].insert_one(example_doc)
   
   puts("There was #{result.n} document inserted")
   puts("The _id of the new document is: #{result.inserted_id}")

Output from above:

.. code-block:: bash

   There was 1 document inserted
   The _id of the new document is: 55e8a17b4d61639133000000

Reading documents
-----------------

Finding documents with a specific field:

.. code-block:: ruby

   #!/usr/bin/env ruby
   require 'mongo'
   require 'neatjson'
   
   # Turn off debug-mode
   Mongo::Logger.logger.level = Logger::WARN
   
   client_host = ['iad-c17-1.objectrocket.com:12345']
   client_options = {
     database: 'db1',
     user: 'example_username',
     password: 'example_password'
   }
   
   client = Mongo::Client.new(client_host, client_options)
   
   # Find the documents that match our query below
   result = client[:pokemon].find({"winner":"Javi"})
   
   # Iterate through each of the results
   result.each do |document|
     puts JSON.neat_generate(document)
   end

Output from above:

.. code-block:: bash

   {
     "start":"2015-09-02T22:46:30.782Z",
     "end":"2016-09-02T22:46:30.782Z",
     "location":"Texas",
     "official_game":false,
     "winner":"Javi",
     "players":[
       {"name":"Javi","decks":["Dinosaurs","Plants"],"points":24,"place":1},
       {"name":"Seth","decks":["Spies","Zombies"],"points":20,"place":2},
       {"name":"Dave","decks":["Steampunk","Wizard"],"points":20,"place":2},
       {"name":"Castro","decks":["Shapeshifters","Ninjas"],"points":18,"place":4}
     ],
     "_id":{  "$oid":"55e8a02f4d616390ce000000"}
   }

Updating a document
-------------------

Updating a document:

.. code-block:: ruby

   #!/usr/bin/env ruby
   require 'mongo'
   require 'neatjson'
   
   # Turn off debug-mode
   Mongo::Logger.logger.level = Logger::WARN
   
   client_host = ['iad-c17-1.objectrocket.com:12345']
   client_options = {
     database: 'db1',
     user: 'example_username',
     password: 'example_password'
   }
   
   client = Mongo::Client.new(client_host, client_options)
   
   # Update the document that matches our query below
   result = client[:dont_tell_me_what_to_do].find(winner: 'Javi').update_one('$set' => { winner: 'Seth' })
   
   # Iterate through each of the results
   result.each do |document|
     puts JSON.neat_generate(document)
   end

Output from above:

.. code-block:: bash

   {
     "ok":1,
     "nModified":1,
     "n":1,
     "lastOp":{  "t":1441313472,  "i":1},
     "electionId":{  "$oid":"55e73f85fcfd98f64182f341"}
   }

Deleting a document
-------------------

Deleting a document:

.. code-block:: ruby

   #!/usr/bin/env ruby
   require 'mongo'
   require 'neatjson'
   
   # Turn off debug-mode
   Mongo::Logger.logger.level = Logger::WARN
   
   client_host = ['iad-c17-1.objectrocket.com:12345']
   client_options = {
     database: 'db1',
     user: 'example_username',
     password: 'example_password'
   }
   
   client = Mongo::Client.new(client_host, client_options)
   
   # Delete the document that matches our query below
   result = client[:dont_tell_me_what_to_do].find(winner: 'Seth').delete_one
   
   # Iterate through each of the results
   result.each do |document|
     puts JSON.neat_generate(document)
   end

Output from above:

.. code-block:: bash

   {
     "ok":1,
     "n":1,
     "lastOp":{  "t":1441313712,  "i":1},
     "electionId":{  "$oid":"55e73f85fcfd98f64182f341"}
   }

Additional reading
------------------

If you need more help with the Ruby driver, links to official documentation are below:

* `Ruby Driver API Documentation <http://api.mongodb.org/ruby/>`_
* `MongoDB Ruby Driver Tutorial <http://docs.mongodb.org/ecosystem/tutorial/ruby-driver-tutorial/>`_
* `Ruby Driver Documentation <http://docs.mongodb.org/ecosystem/drivers/ruby/>`_
* `Ruby Driver Github <https://github.com/mongodb/mongo-ruby-driver>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
