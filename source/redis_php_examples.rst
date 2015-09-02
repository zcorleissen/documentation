PHP Connection Examples
========================

.. |checkmark| unicode:: U+2713

The `predis <https://github.com/nrk/predis>`_ package is the recommended client for Redis when using PHP.

Installation
------------

Install predis at the command prompt if you haven't yet:

.. code-block:: bash

   $ composer require predis/predis
   Using version ^1.0 for predis/predis
   ./composer.json has been created
   Loading composer repositories with package information
   Updating dependencies (including require-dev)
     - Installing predis/predis (v1.0.3)
       Loading from cache
   
   predis/predis suggests installing ext-phpiredis (Allows faster serialization and deserialization of the Redis protocol)
   Writing lock file
   Generating autoload files

Authentication
--------------

.. code-block:: bash

   php > require __DIR__ . '/vendor/autoload.php';
   php > $redis = new Predis\Client(['host' => '#####.publb.rackspaceclouddb.com', 'port' => 6379, 'password' => '#####']);

C.R.U.D.
--------

Create, read, update and destroy are the four basic functions of persistent storage.

.. code-block:: bash

   php > echo $redis->set("best_car_ever", "Tesla Model S");
   OK

   php > echo $redis->get("best_car_ever");
   Tesla Model S

   php > echo $redis->del("best_car_ever");
   1

   php > echo $redis->get("best_car_ever");
   php >

More Information
----------------

If you need additional help with predis, here are some useful links:

* `predis Official Documentation <https://github.com/nrk/predis>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
