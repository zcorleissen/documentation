Utilities
=========

This page gives a general overview of the tools distributed with MongoDB. We will cover them in order of most popular/useful for our customers.

mongostat
---------

The **mongostat** utility lets you view live MongoDB performance statistics for the entire cluster (mongos and mongod instances). Fields such as inserts/queries/updates/deletes are shown per instance, and in real-time. If you've ever used vmstat, it follows a similar output. Here is an example of how you might use it.

.. code-block:: bash

   $ mongostat --host 'syd-mongos0.objectrocket.com' --port '35023' --username 'dba' --password 'dba' --authenticationDatabase 'admin' --discover

The ``--host`` argument would be the "Connect String" in the Control Panel. The ``--discover`` argument can be very useful, as it will list all nodes of a cluster, instead of just one. For a full reference to all arguments, as well as details on field names, check out the official documentation here:

http://docs.mongodb.org/manual/reference/program/mongostat/

mongodump/mongorestore
----------------------

The **mongodump** utility exports the contents of a database in binary format. This will result in a ``.bson`` and ``.json`` file per collection. If you've ever used mysqldump, it works in a similar fashion. Keep in mind that a similar utility exists with the name of **mongoexport**, which works in a completely different manner (don't use mongoexport for backups!). Here is an example of how one might use mongodump to create a backup of their database.

.. code-block:: bash

   $ mongodump --host <hostname> --out <path> --username <username> --password <password> --port <port> --db <database>

This would result in a folder with the following contents:

.. code-block:: bash

   $ ls -1 /path/to/database/dump/
   collection1.bson
   collection1.metadata.json
   collection2.bson
   collection2.metadata.json
   system.indexes.bson

The **mongorestore** utility imports the contents of a database. Here...

.. code-block:: bash

   $ mongorestore --optionsssss

mongoexport/mongoimport
-----------------------

...

mongoperf
---------

...

mongofiles
----------

...

mongooplog
----------

...

mongorestore
------------

...

mongosniff
----------

...

mongotop
--------

...

bsondump
--------

...

