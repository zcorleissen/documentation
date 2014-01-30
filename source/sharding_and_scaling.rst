Sharding and Scaling Guide
================

ObjectRocket implements standard MongoDB sharding (for plans that are sharded), but hides the complexity of all the components into an easy to use cloud based service.  The stardard components are all automatically provisioned.  The MongoDB balancer is used to keep data between shards at an even level.  For more information about the MongoDB sharding architecture check out `this guide`_.

.. _this guide: http://docs.mongodb.com/sharding

Shard keys
----------------

Keys must be defined for how data will be split among the shards.  There are two ways to achieve this on the ObjectRocket platform:

1. Manual shard key definition
2. Automated shard key definition

Manual shard key definition
~~~~~~~~~~~~~~~~~~~~~~

Shard keys may be defined in the web UI.  This is done for existing collections on a collection by collection basis by navigating to the instance, database, and collection to be sharded and selecting the 'shard key' tab.  Click the 'add shard key' button to define the key.

For new collections by navigating to the instance then database, and then selecting the 'add collection' button a dialog will prompt for the collection name, and it's shard key.

Shard key selection
----------------

Choosing the proper shard key is critical to performance and scalability.  MongoDB inc has written a good primer `here`_.

.. _here: http://docs.mongodb.com/selecting+good+shard+keys

Automated shard key definition
~~~~~~~~~~~~~~~~~~~~~~

ObjectRocket also has the unique ability to automate the process of creating shard keys (in MongoDB 2.4+ only).  This is done via an agent that watches each and every ObjectRocket instance, and when the criteria is met for adding keys, the agent defines hash keys on _id for each collection that doesn't already have a shard key defined.  This setting gives true 'set and forget' sharding capabilites.  The potential downside is a hashed shard key on _id may not be optimal.

In order to enable this feature all of the following must be true:

- auto_hash_shard_key on the settings tab is set to ON
- instances has > 256MB of data in it.

Or the following must be true:

- auto_hash_shard_key on the settings page is set to ON
- a shard is added via Rocketscale or manually.

Scaling (adding a shard)
----------------

Scaling on the ObjectRocket platform is easy.  To scale an instance a shard is added, the balancer then moves some of the existing data to this new shard thus giving more compute and storage to the cluster.

Shards can seamlessly be added to an instance at any time.  To add a shard click the 'add shard' button on the `cluster page`_.  This will add a shard in the plan size of the instance.

.. _cluster page: https://app.objectrocket.com/cluster

Additionally, if auto_add_shard_threshold is nonzero and not null, Rocketscale may automatically add a shard.

RocketScale
----------------

Rocketscale is an agent unique to ObjectRocket that scales sharded instances in an automated fashion as the instance grows.  Rocketscale watches each instance, and when auto_add_shard_threshold on the settings page is exceeded it adds a shard to the instance.

The auto_add_shard_threshold is based on total % of storage consumed on the cluster.  The current storage usage is viewable on the `instances`_ page.  For instance, if the plan is 20GB, and there are currently 2 shards for a total available storage space of 40GB, and Rocketscale is set to 50(%), then when the storage usage reaches 20GB a shard will be added.

.. _instances: https://app.objectrocket.com/instances

Rocketscale may be turned off by setting it to 0 (zero) or removing any value from the setting (null) on the settings page.

Balancer
----------------

ObjectRocket utilizes the MongoDB Inc balancer.  The balancer by default is in the ON state.  If the balancer is impacting performance it can be turned OFF or alternatively, windows can be defined for when the balancer may run.  Defining balancer windows is done in the web UI under the settings tab.  In general it's not recommended to turn the balancer off, this may effect the ability of the system to scale.

The `cluster page`_ in the web UI shows the current balance of the cluster by % of total.

.. _cluster page: https://app.objectrocket.com/cluster

The balancer status is viewable on the instance settings page. Either Stopped or Running.






