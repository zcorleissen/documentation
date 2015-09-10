Node.js Connection Examples
===========================

.. |checkmark| unicode:: U+2713

The `ioredis <https://github.com/luin/ioredis>`_ package is the recommended client for Redis when using Node.js.

Installation
------------

Install ioredis at the command prompt if you haven't yet:

.. code-block:: bash

   $ npm install ioredis

Authentication
--------------

.. code-block:: bash

   > var Redis = require('ioredis');
   undefined

   > var redis = new Redis({host: '#####.publb.rackspaceclouddb.com', port: 6379, password: '#####'});
   undefined

C.R.U.D.
--------

Create, read, update and destroy are the four basic functions of persistent storage.

.. code-block:: bash

   > redis.set("best_car_ever", "Tesla Model S", function (err, result) { console.log(result); });
   > OK

   > redis.get("best_car_ever", function (err, result) { console.log(result); });
   > Tesla Model S

   > redis.del("best_car_ever", function (err, result) { console.log(result); });
   > 1

   > redis.get("best_car_ever", function (err, result) { console.log(result); });
   > null

More Information
----------------

If you need additional help with ioredis, here are some useful links:

* `ioredis Official Documentation <https://github.com/luin/ioredis>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
