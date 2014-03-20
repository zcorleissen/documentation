ObjectRocket Overview and Concepts
==================================

This guide intended to give an overview of the ObjectRocket service.

ObjectRocket is a Database as a Service based on the popular MongoDB database. The ObjectRocket infrastructure has been specifically designed to enable MongoDB to be scalable, performant, available, and highly supportable.

ObjectRocket allows for easy provisioning of MongoDB instances via the web UI.  Once created, the instance is available via the standard MongoDB connection methods for use.  Each instance has a unique connect string associated with it.  This connect sting can be found on the `instances page`_ and used as any standard MongoDB connect string would be via MongoDB shell or native driver.

.. _instances page: https://app.objectrocket.com/instances

Instances
----------------

Currently there are three types of instances:

- SMALL: instance with a single replica set with up to 5GB of storage.
- MEDIUM: clustered instance, with a single shard to begin with storage equal to the plan size.
- LARGE: clustered instance.  Not available via the website.  Contact sales@objectrocket.com for sizes larger than available on the website.  Generally this is clusters in the 1TB or larger range.

SMALL Instances
~~~~~~~~~~~~~~~~~~~~~~

A SMALL instance is a simple replica set.  It's designed to be simple and easy to use without more complex sharding capabilities. The SMALL plan works great for dev, test or QA instances.

A SMALL instance starts out with a smaller footprint and vertically grows up to a maximum plan size. For instance, a 5GB SMALL plan starts as 1GB and grows as needed up to a maximum of 5GB.

A SMALL plan has:
- SSD storage
- Storage grows
- A replica set with at least two members, one primary, one secondary, and one arbiter.
- An API key, and API access
- Scheduled Backups
- Amazon network access via Direct Connect in our US-West, US-East, and US-East-IAD3 datacenters

More information is available on the `plans and pricing page`_.

.. _plans and pricing page: https://www.objectrocket.com/pricing

MEDIUM Instances
~~~~~~~~~~~~~~~~~~~~~~

MEDIUM instances are clustered instances.  They are designed to be the workhorse of a system.  They are initially provisioned with a single shard, but can grow by adding shards at any time.  A MEDIUM instance is provisioned with all of the required components for the cluster.  The end user need not care about the specifics of the MongoDB sharding components, daemons, etc.

A MEDIUM plan has:
- Redundant MongoS servers
- Redundant config servers
- Load balanced connections to MongoS servers
- SSL termination for SSL connections
- SSD Storage
- Storage grows via adding shards
- A replica set with at three members, one primary and two secondary
- A single shard
- An API key, and API access
- Scheduled Backups
- Amazon network access via Direct Connect in our US-West, US-East, and US-East-IAD3 datacenters

More information is available on the `plans and pricing page`_.

.. _plans and pricing page: https://www.objectrocket.com/pricing


Plans and Shards
----------------

A plan is a unit of storage assigned to a shard. On creation of an instance, a plan size is determined. This is the size that additional shards are added in. Plans range from 5GB up to hundreds of GB. Plans should be chosen with consideration for performance implications. For example, if the workload was very insert intensive, but with a 80GB data set size, choosing a 5GB plan and having 10 shards would work well. However, if there was more data, but less requirements for queries, then a larger size may make more sense, say 100GB.  If the total data size was 2TB with a moderate workload of 1200 OPS then a 250GB shard may be best.

When a shard is added, it's added in the plan size. If the instance is a 5GB plan, then adding another shard will add another 5GB, bringing the total to 10GB of addressable space. When a new shard is added, the balancer will kick off and balance the data between the nodes and keep the workload roughly balanced (by disk space size).

ObjectRocket is based on the native MongoDB sharding design. Thus shard keys must be defined. If a shard key is not defined, then ObjectRocket can't balance the data out, and adding shards won't help and the single shard could fill up. So defining shard keys is an essential component on ObjectRocket. In order to define a shard key, use the web interface to create a collection. The create collection function has a spot to define the key you want to shard on. `Here is a great guide on the topic`_.

.. _Here is a great guide on the topic: http://docs.mongodb.org/manual/tutorial/choose-a-shard-key/  

