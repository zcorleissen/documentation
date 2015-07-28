Ruby Driver Examples
========================

Installation
------------

The Ruby driver is bundled as a gem, and can be installed like so:

.. code-block:: bash

   $ gem install mongo

Authentication
--------------

You can create a connection using the standard MongoDB connection format:

.. code-block:: bash

   mongodb://[username:password@]host1[:port1][,host2[:port2],...[,hostN[:portN]]][/[database][?options]]

Note: When creating a new client connection, debug output will be sent to the console every second, and can make development a bit difficult. This default behavior is currently under review here:

https://jira.mongodb.org/browse/RUBY-893

If you wish to turn this off, you can issue the following command:

.. code-block:: bash

   $ irb(main):001:0> Mongo::Logger.logger.level = Logger::WARN
   => 2

Connecting to a sharded instance:

.. code-block:: bash

   $ irb(main):001:0> require 'mongo'
   => true

   $ irb(main):002:0> client = Mongo::Client.new('mongodb://iad-mongos0.objectrocket.com:15045', :user => 'username', :password => 'password')
   => #<Mongo::Client:0x70360972955500 cluster=iad-mongos0.objectrocket.com:15045>

   $ irb(main):003:0> client.database_names
   => ["test", "config", "admin"]

Create a document
-----------------

...

Read a document
---------------

...

Update a document
-----------------

...

Delete a document
-----------------

...

