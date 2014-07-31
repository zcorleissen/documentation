ObjectRocket for Redis FAQ
==========================

What is ObjectRocket for Redis?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ObjectRocket for Redis simplifies application development by offering pre-configured, high performance, highly available Redis instances in the cloud.

Simple provisioning, configuration and administration capabilities make it easy for developers to integrate Redis into their application stack


Is ObjectRocket for Redis highly available?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Yes - Customers can instantly deploy highly available Redis Instances featuring seamless, instantaneous automatic failover of the Redis master to a slave in the event of a master node failure.

What size plans do you offer?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

All plans are sold as useable memory.
500MB; 1GB; 2.5GB; 5GB; 10GB; 20GB; 50GB

If you require a larger instance size then please contact us.

What kind of support should I expect from the ObjectRocket Support Team?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ObjectRocket for Redis is backed by Redis Specialists 24/7/365 to proactively monitor and fix issues with customer instances or infrastructure, assist with data migrations and fine-tune Redis configurations. These specialists also provide architecture advice and data structure best practices, as well as helping integrate Redis with other services including Mongo, Sidekiq and Magento.

Will you help migrate my data to an ObjectRocket for Redis instance?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

We will offer migration assistance to customers using the 20GB and larger plans. You can find instructions on how to migrate your data here.

What software is being used?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The offering is based on Redis 2.8.13 with Sentinel for high availability. All instances are Highly Available, and all instances persist to disk.

What does the system architecture look like?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* Our Redis environment utilizes 2 node clusters and 3-Sentinels. One Redis node is master, one node is a slave. 
* Every aspect of the stack has been optimized specifically for Redis.

  * All services are containerized, which provides guaranteed resources (memory, CPU, disk I/O) and prevents “noisy-neighbor” problems and eliminates the performance bottlenecks of traditional hardware virtualization.
  * The service runs on performance-optimized infrastructure to make Redis run as fast as possible.

* AWS users will automatically use dedicated 10Gbit AWS Direct Connect circuits for very high throughput, low latency connectivity to ObjectRocket for Redis. 

What version of Redis is supported?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

As of 7/28/2014 ObjectRocket supports 2.8.13

What other features do you offer?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ObjectRocket for Redis also features Public IP Access & ACLs; AWS Direct Connect and Configuration Edits. 

Do you support Redis Cluster?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

No - it’s not stable for production today. 

How much does ObjectRocket for Redis cost per month?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Please see our main pricing page: http://objectrocket.com/pricing#redis

How does billing work?
^^^^^^^^^^^^^^^^^^^^^^
Please refer to our main FAQ: http://docs.objectrocket.com/faq.html#billing

