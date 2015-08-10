ObjectRocket FAQ
================

General
-------

What is ObjectRocket?
~~~~~~~~~~~~~~~~~~~~~

ObjectRocket is our Industrial Strength platform for MongoDB and Redis. 
We're leveraging state of the art hardware to bring you a performant, 
fault-tolerant infrastructure in geo-diverse colocations so you can
be sure to be as close to your app as possible. We handle backups automatically,
offer instant on capacity to allow immediate scaling, and fine tune the entire
stack to make sure it's as performant as possible, letting you focus on
what's important, your business and your customers.


What do we manage?
~~~~~~~~~~~~~~~~~~

We manage the entire platform including scaling, updating, and replicating your data so
that all you need to focus on is your business. Managing and scaling a
database is hard, and you can spend a lot of time finding the right team and
developing your own platform or you can let us do it for you, as we have years
of experience scaling platforms for fortune 100 companies and startups. We've
spent the time and capital to develop a world class solution and we provide
a simple interface to manage your individual instances.


What about data portability?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ObjectRocket is built upon MongoDB and Redis, so your ability to move your data 
into or out of ObjectRocket is only limited by your ability to migrate data from
one mongo or redis instance to another.


What time zone is my data in?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

All ObjectRocket systems use PST.


What kind of query functionality does OR support?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We support all normal MongoDB and Redis functionality. The only exception being
functionality which requires direct server access, like server side functions.
Please contact our `support team <mailto:support@objectrocket.com>`_ if you need
something like this and we'll be happy to help figure it out!


How can I change my DB password?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You should be able to log in and change it from the MongoDB command line like
you normally otherwise would:


.. code-block:: javascript

   > use kg
   switched to db kg
   > db.auth( "kg" , "kg" );
   1
   > show collections
   kg_test
   system.indexes
   system.profile
   system.users
   testCollection
   > db.changeUserPassword( "kg" , "kgs_new_password");
   Updated 1 existing record(s) in 35ms
   > db.auth("kg","kg");
   Error: 18 { code: 18, ok: 0.0, errmsg: "auth fails" }
   0
   > db.auth( "kg" , "kgs_new_password" );
   1


Also, feel free to contact our `support team <mailto:support@objectrocket.com>`_ if you need any help!

How is space usage calculated?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Space utilization per instance is measured as follows::


   "Total File Size" = sum( db.stats.fileSize + db.stats.nsfile ) for each DB including admin, local, and config


fileSize includes data size, index size, extent size, some amount of file free
space buffer. "Total File Size" is listed on the 
`instances page <https://app.objectrocket.com/instances>`_.

Detailed information about how this is calculated can be found on our blog: `Understanding MongoDB space usage <http://objectrocket.com/blog/how-to/understanding-mongodb-space-usage>`_.


Redundancy, Scalability, Performance
------------------------------------


Where is my data?
~~~~~~~~~~~~~~~~~

Customer data is kept on an instance based on the customers preferred zone.


How much data can I store?
~~~~~~~~~~~~~~~~~~~~~~~~~~

You can store as much data as you like. If you have defined shard keys for
your collections you can grow your data according to your plan size. 
If you haven't defined shard keys then the maximum disk space you can 
consume is equal to the size of one plan. It's very important to define
shard keys on the ObjectRocket system. Here is a :mongo-manual:`good guide </core/sharding-shard-key>`
about choosing shard keys.


How many requests am I allowed?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can execute as many operations per second as needed, however please
contact our `support team <mailto:support@objectrocket.com>`_ if you believe
you will need more than 200,000 Operations/sec.


How can I monitor performance / availability?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You have two options for directly monitoring system performance and
availability. The ObjectRocket user interface has an entire page devoted to
performance, availability, and statistics, and you can also use our 
`New Relic integration <https://app.objectrocket.com/external/new_relic>`_ 
to view them there.

