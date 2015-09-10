MongoDB Utilities
=================

You can use almost any of the standard MongoDB utilities with our platform, but here are some examples of how to use the most common. 

mongodump
---------

``mongodump`` is used to create a binary export of your mongodb instance. When run against a sharded instance it's routed through a mongos, or directly from the primary when using a replica set.

We recommend the following when using ``mongodump``:

- Verify connectivity to the instance (ACLs, etc.)
- Match the version of ``mongodump`` against your instance by running ``mongodump --version``
- If your mongo instance is 2.6+ verify the user has the `necessary privileges and roles <http://docs.mongodb.org/manual/reference/built-in-roles/#backup>`_ to perform a backup if you're not on ObjectRocket.
- Specify the location for the output using the ``-o`` flag

.. note:: 
  NOTE! If you don't specify a location when running ``mongodump``, it creates a folder named ``dump`` in your current directory and overwrites anything currently existing in the dump/ folder.

Here's what the basic usage looks like, backing up from the host ``iad-mongos2.objectrocket.com``, on port ``12345``, from the database ``example`` with the username ``example_user``, to the folder named ``backup`` using ``-o``:

.. code-block:: bash 

   $ mongodump --host iad-mongos2.objectrocket.com:12345 -d example_db -u example_user -p -o backup

Now, let's examine some other common flags:

* Backup a single collection within a database using ``-c``
 
.. code-block:: bash

   $ mongodump --host iad-mongos2.objectrocket.com:12345 -d example_db -c coll_example -u example_user -p -o backup

* Backup documents returned by a particular query using ``-q``

.. code-block:: bash
  
   $ mongodump --host iad-mongos2.objectrocket.com:12345 -u example_user -p -d example_db -q '{ _id : { $gte : ObjectId("50ad7bce1a3e927d690385ec") } }'

.. note::
   When using ``-q`` it's very important to wrap the json query in single quotes, (e.g. ``'``) so it doesn't interact with your shell. Sometimes escaping is necessary depending on the query as well.

When you examine the contents of the backup directory you'll see ``.json`` and ``.bson`` files. The ``.bson`` files are binary data, and the ``.json`` files contain metadata. You can compress the backups as expected using ``gzip`` or any preferred method. To perform restores both ``bson`` and ``json`` files are necessary, so be sure to include those in your compressed files.

mongorestore
------------

``mongorestore`` writes data from a backup created by mongodump to a mongodb instance. mongorestore can create a new database or add data to an existing database.

In the example below we're restoring to the host ``syd-mongos0.objectrocket.com``, on port ``12345``, to the database ``usda``, using the ``yoda`` user, from the backup folder of ``dump/usda/``. This will restore everything in that folder to the specified database. In the example we're using the 3.0 binaries, as they restore in parallel, but we always recommend matching the binary you're using with the version you're restoring to.

.. code-block:: bash

   $ mongorestore --host syd-mongos0.objectrocket.com:12345 -d usda -u yoda -p dump/usda/
   2015-08-12T08:41:06.330-0700 building a list of collections to restore from dump/usda/ dir
   2015-08-12T08:41:06.637-0700 reading metadata file from dump/usda/nutrition.metadata.json
   2015-08-12T08:41:06.637-0700 restoring usda.nutrition from file dump/usda/nutrition.bson
   2015-08-12T08:41:09.330-0700 [############............] usda.nutrition 32.0 2015-08-12T08:41:30.330-0700 [########################] usda.nutrition 62.2 MB/62.2 MB (100.0%)
   2015-08-12T08:41:45.330-0700 [########################] usda.nutrition 62.2 MB/62.2 MB (100.0%)
   2015-08-12T08:41:45.895-0700 restoring indexes for collection usda.nutrition from metadata
   2015-08-12T08:41:46.359-0700 finished restoring usda.nutrition 2015-08-12T08:41:46.359-0700 done

.. warning:: 
   ``mongorestore`` will not overwrite existing documents nor update, it will only insert. It also does not wait for a response from the target server, and any insertion failures are logged to the target logs, not to ``STDOUT``.

Here are the common flags used with ``mongorestore``:

* ``--drop`` will drop the collection you're attempting to restore to prior to any inserts.

* ``--noIndexRestore`` will not restore indexes found in the metadata json files.

* ``--stopOnError`` will stop restoring upon an error, rather than continuing silently.

mongoexport
-----------

``mongoexport`` is used for exporting your data to CSV, TSV, or JSON files, which are more human readable and can be used with more applications. It should be noted that unlike ``mongodump`` you cannot export the entirety of a database and must specify a collection.

Here's a basic example, using the host ``hkg-mongos0.objectrocket.com``, the port ``12345``, the database ``zips``, the collection ``zips``, and outputting to a JSON file ``zips.json``.

.. code-block:: bash
   
   $ mongoexport --host hkg-mongos0.objectrocket.com:12345 -d zips -c zips --type json -o zips.json

* By default, mongoexport will use the ``-k`` flag and use any available secondaries.

* When using ``--type`` you'll need to specify either ``json`` or ``csv``. ``json`` is the default and is used when no type is specified. ``csv`` has to be used in conjunction with ``--fields`` or the ``--fieldFile`` option to specify the fields to export from the collection.

Here's an example using ``csv`` and ``--fields``:

.. code-block:: bash

   $ mongoexport --host hkg-mongos0.objectrocket.com:12345 -d zips -c zips --type csv --fields name,address -o zips.csv

As with ``mongodump`` and ``mongorestore`` you're able to specify queries for your export using the ``-q`` argument.

.. code-block:: bash

   $ mongoexport --host hkg-mongos0.objectrocket.com:12345 -d zips -c zips -q '{ zips : { $gt : 60000 } }' -o zips.json

mongoimport
-----------

``mongoimport`` is the opposite of ``mongoexport``, and ingests json or csv into MongoDB.

Here's a basic example importing ``zips.json`` into the ``hkg-mongos0.objectrocket.com`` host, using the ``12345`` port, into the ``zips`` database and collection.

.. code-block:: bash

   $ mongoimport --host hkg-mongos0.objectrocket.com:12345 -d zips -c zips --file zips.json

If the database and collection don't exist on the host you're importing to, mongoimport will create them, just as with mongorestore. 

Here are some of the more important flags to be aware of when using mongoimport:

* ``--fields`` must be used when importing csv that do not include the field names in the header of the file.

* ``--ignoreBlanks`` will ignore empty fields in csv or tsv imports. If not specified, ``mongoimport`` will create fields without values in those documents.

* ``--drop`` will drop the collection you're inserting to before it begins the import.

* ``--stopOnError`` will stop the import upon the first error rather than continuing.

* ``--upsert`` will update existing documents if they match an imported document.

* ``--upsertFields`` lets you specify what to match when using ``--upsert``. The default match when not specified uses ``_id``.

* ``--writeConcern`` lets you specify what writeConcern to use when importing. The normal writeConcern options apply here.
