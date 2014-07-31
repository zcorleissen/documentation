ObjectRocket for Redis Migration Guide
======================================

There are two methods to migrate data from one Redis server to another:

1. Download a .rdb dump and upload it to the new instance - Time consuming; keys will be lost during the time taken to upload the RDB file to the new instance; downtime
2. Use the Redis native replication functionality to create a slave, sync with the master and switch to the replica when replication is complete - downtime is kept to a minimum; simple to run 

Steps to Replicate your Redis Data to an ObjectRocket for Redis HA Master
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Redis replication is a very simple to use and configure and allows Redis slave servers to be exact copies of master servers.

Requirements:

* Existing new ObjectRocket for Redis HA setup in place
* "Old" instance reachable from the new setup (specifically the master)
* IP and Port for old instance

Procedure:

* Connect to the new master via the redis-cli (or a client library such as redis-py)
* Issue the SLAVEOF command such as "SLAVEOF existingip:existingport"

At this point the new master will also be a slave of the old master.

.. code-block:: bash

	redis-cli> SLAVEOF 127.0.0.1 6739

If your master has a password via requirepass, you need to configure the slave to use that password in all sync operations. To do it on a running instance, use redis-cli and type:

.. code-block:: bash

	redis-cli> config set masterauth <password>

The larger the dataset the longer the sync will take. One way to monitor it is to check the replication information. It will look something like this:

.. code-block:: bash

	redis-cli> info replication
	# Replication
	role:slave
	master_host:127.0.0.1
	master_port:6379
	master_link_status:up
	master_last_io_seconds_ago:0
	master_sync_in_progress:0
	slave_repl_offset:17887014
	slave_priority:100
	slave_read_only:1
	connected_slaves:0
	master_repl_offset:0
	repl_backlog_active:0
	repl_backlog_size:1048576
	repl_backlog_first_byte_offset:4430626
	repl_backlog_histlen:1048576

The specific value we are looking for here is "master_sync_in_progress". It is an integer version of a boolean where 0 means not currently syncing and 1 means sync is in progress. Once the sync is complete the data has been replicated to the new master (which will also be replicated to the new slave).

You may also wish to run the DBSIZE command to return the number of keys in both databases to check they match:

.. code-block:: bash

	redis-cli> DBSIZE
	(integer) 167,988

Next set a key in the master:

.. code-block:: bash

	redis-cli> SET replicated:test true
	OK

...and check that it replicated to the slave:

.. code-block:: bash

	redis-cli> GET replicated:test
	"true"

Next issue the following on the slave and it will be your new Highly Available ObjectRocket for Redis Master

.. code-block:: bash

	redis-cli> SLAVEOF NO ONE

Don't forget to point your application to this new master instance and destroy the old master at your discretion!
As always, don't hesitate to contact support@objectrocket or create a ticket if you're having issues or need extra guidance when migrating your data.