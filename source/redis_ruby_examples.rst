Ruby Connection Examples
========================

.. |checkmark| unicode:: U+2713

The `redis-rb <https://github.com/redis/redis-rb>`_ gem is the recommended client for Redis when using Ruby.

Installation
------------

Install redis-rb at the command prompt if you haven't yet:

.. code-block:: bash

   $ gem install redis

Authenticate/Connect
--------------------

.. code-block:: ruby

   irb(main):001:0> require 'redis'
   => true

   irb(main):002:0> redis = Redis.new(:host => "###.publb.rackspaceclouddb.com", :port => 6379, :password => "###")
   => #<Redis client v3.2.1 for redis://###.publb.rackspaceclouddb.com:6379/0>

SET (Create a key)
------------------

.. code-block:: ruby

   irb(main):003:0> redis.set("best_car_ever", "Tesla Model S")
   => "OK"

GET (Retrieve a key)
--------------------

.. code-block:: ruby

   irb(main):004:0> redis.get("best_car_ever")
   => "Tesla Model S"

DEL (Delete a key)
------------------

.. code-block:: ruby

   irb(main):005:0> redis.del("best_car_ever")
   => 1

   irb(main):006:0> redis.get("best_car_ever")
   => nil

More Information
----------------

If you need additional help with redis-rb, here are some useful links:

* `redis-rb Official Documentation <http://www.rubydoc.info/github/redis/redis-rb/>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
