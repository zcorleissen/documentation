ObjectRocket FAQ
================


General
-------


What is ObjectRocket?
^^^^^^^^^^^^^^^^^^^^^

ObjectRocket is the next generation cloud database. We've built an
Industrial Strength platform specifically for MongoDB using state of the art
hardware like Solid State Disks (SSDs) so that you never have to worry about
performance, geo-diverse colocations so you never have to worry about backups
and instant on capacity so that you can scale instantly.


What do we manage?
^^^^^^^^^^^^^^^^^^

We manage the entire platform including scaling, updating, and replicating your data so
that all you need to focus on is your business. Managing and scaling a
database is hard, and you can spend a lot of time finding the right team and
developing your own platform or you can let us do it for you, as we have years
of experience scaling platforms for fortune 100 companies and startups. We've
spent the time and capital to develop a world class solution and we provide
you a simple interface to manage your individual instances.


What about data portability?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ObjectRocket is built upon MongoDB so your ability to move your data into
or out of ObjectRocket is only limited by your ability to migrate data from
one mongo instance to another.


What time zone is my data in?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

All ObjectRocket systems use PST.


What kind of query functionality does OR support?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ObjectRocket is based on MongoDB and we support all of its functionality.


How can I change my DB password?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You should be able to log in, and change it from the MongoDB command line like
you normally otherwise would:


.. code-block:: javascript

   > use kg
   switched to db kg
   > db.auth("kg","kg");
   1
   > show collections
   foo
   kg_test
   system.indexes
   system.profile
   system.users
   testCollection
   > db.addUser("kg","foooooo");
   {
        …
        "updatedExisting" : true,
        "n" : 1,
        "lastOp" : NumberLong("5820431785665757187"),
        "connectionId" : 1321217,
        "err" : null,
        "ok" : 1
   }
   {
        "_id" : ObjectId("50006b5f16af5eae22111ea2"),
        "pwd" : "c0912c08f9c04eeead65a7dd04ae2703",
        "readOnly" : false,
        "user" : "kg"
   }

Also, feel free to contact `support <mailto:support@objectrocket.com>`_ if you need any assistance.

How is space usage calculated?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Space utilization per instance is measured as follows::


   "Total File Size" = sum( db.stats.fileSize + db.stats.nsfile ) for each DB including admin, local, and config


fileSize includes data size, index size, extent size, some amount of file free
space buffer. "Total File Size" is listed on the
`instances page <https://app.objectrocket.com/instances>`_.

Detailed information about how this is calculated can be found on our blog: `Understanding MongoDB space usage <http://objectrocket.com/blog/how-to/understanding-mongodb-space-usage>`_.


Redundancy, Scalability, Performance
------------------------------------


Where is my data?
^^^^^^^^^^^^^^^^^

Customer data is kept on an instance based on the customers preferred zone.


How much data can I store?
^^^^^^^^^^^^^^^^^^^^^^^^^^

You can store as much data as you like. If you have defined shard keys for
your collections you can grow your data in chunks according to your plan
size. If you haven't defined shard keys then the maximum disk space you
can consume is equal to the size of one plan. It's very important to define
shard keys on the ObjectRocket system. Here is a
:mongo-manual:`good guide </core/sharding-shard-key>`
about choosing shard keys.


How many requests am I allowed?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can execute as many operations per second as needed, however please
contact us if you believe you will need more than 200,000 Operations/sec.


How can I monitor performance / availability?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You have two options for directly monitoring system performance and
availability. The ObjectRocket user interface has an entire page devoted to
performance and availability. Additionally, all performance and availability
metadata is available via the ObjectRocket API so you can easily integrate the
data with your existing systems.


Billing
-------


What are the details of the free promotional offer?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The promotional offer is only available to NEW ObjectRocket for MongoDB customers and/or NEW ObjectRocket for Redis customers. Only 1GB Mongo Replica Sets, 5GB sharded (single shard) Mongo instances, and 500MB Redis instances qualify for this promotional offer.

This promotional offer starts on Sep. 18, 2014 and ends Sep. 30, 2015. Customers that sign up for the ObjectRocket for MongoDB service for the FIRST time during the promotional period will have the option to receive either a single 1GB replica set or a single 5GB shard free of charge for the FIRST 30 days upon sign up. Customers that sign up for the ObjectRocket for Redis service for the FIRST time during the promotional period will receive a 500MB Redis Instance free of charge for the FIRST 30 days upon sign up. After the end of the 30 days or if additional plans are added, standard fees for ObjectRocket services will apply.

Your account is not billed until the end of each 30-day service period, starting from the day you sign up. You can cancel at any time by `emailing support <mailto:support@objectrocket.com>`_. If the account remains open after the 30 day trial period, you will be billed standard fees for the ObjectRocket services. For more information see our `billing information <http://objectrocket.com/pricing>`_.

How much does it cost?
^^^^^^^^^^^^^^^^^^^^^^

Pricing varies per region.  Please refer to the following pricing pages:

`US Pricing <https://www.objectrocket.com/pricing>`_.
`London Pricing <https://www.objectrocket.com/pricing_lon>`_.
`Hong Kong Pricing <https://www.objectrocket.com/pricing_hkg>`_.
`Sydney Pricing <https://www.objectrocket.com/pricing_syd>`_.

When will I be billed?
^^^^^^^^^^^^^^^^^^^^^^

ObjectRocket bills for instance subscription one month in advance. When a change to
your set of instances occurs, an invoice is generated with the prorated increased or decreased amount. That invoice amount is added to your next billing cycle creating an bill for the prorated increase or decrease, plus next months subscription.  Changes can occur when you manually add
instances or shards from our website, or automatically when RocketScale™
adds shards to an instance.

If you reduce your usage but continue to use your account, we'll apply any
credit toward your next bill.


What kinds of payment do you accept?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

We accept Visa, MasterCard, American Express, Diners Club, JCB.


Other Questions
---------------


Where can I find your MongoDB customizations?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ObjectRocket strives to deliver the best hosted MongoDB service possible.
As part of this, we do maintain some customizations to the software itself.
As per the AGPL, we make these available to anyone wishing to examine, run,
or otherwise participate! Find the repository in GitHub at:
https://github.com/objectrocket/mongodb-2.2-objectrocket
