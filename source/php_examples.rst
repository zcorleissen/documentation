PHP Connection Examples
=======================

The PHP MongoDB driver is an official driver maintained by MongoDB Inc. Complete information for all features of the driver is available in the `Official Documentation`_.


Installation
---------------
To use the PHP driver you'll need to first install it via pecl:
.. code-block:: bash
		sudo pecl install mongo

Then ensure it's enabled in your php.ini with:
.. code-block:: bash
		extension=mongo.so


Connecting
-------------
Connecting to a replica set:
::
   
 <?php
 $m = new MongoClient("mongodb://sjc-c9-1.objectrocket.com:54074,sjc-c9-0.objectrocket.com:54074/?replicaSet=e0a8d0f797be1b9c4ec7052a7b7484a7");

Connecting to a replica set with SSL:
::
   
 <?php
 $m = new MongoClient("mongodb://sjc-c9-1.objectrocket.com:54074,sjc-c9-0.objectrocket.com:54074/?replicaSet=e0a8d0f797be1b9c4ec7052a7b7484a7", array("ssl" => true));

Connecting to a sharded instance:
::
   
 <?php
 $m = new MongoClient("mongodb://iad-mongos0.objectrocket.com:15045");

Connecting to a sharded instance with SSL:
::

 <?php
 $m = new MongoClient("mongodb://iad-mongos0.objectrocket.com:15045", array("ssl" => true));


















.. _Official Documentation: http://docs.mongodb.org/ecosystem/drivers/php/
