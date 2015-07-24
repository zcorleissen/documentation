PHP Driver Examples
=======================

The PHP MongoDB driver is an official driver maintained by MongoDB Inc. Complete information for all features of the driver is available in the `Official Documentation`_.


Installation
---------------
To use the PHP driver you'll need to first install it via pecl:
::
 sudo pecl install mongo

Then ensure it's enabled in your php.ini with:
::
 extension=mongo.so

Note that if you've installed the driver via a package manager like yum the configuration may be in a standalone file in your php.d directory or similar.


Connecting
-------------
Connecting to a replica set:
::
   
 <?php
 $connection = new MongoClient("mongodb://sjc-c9-1.objectrocket.com:54074,sjc-c9-0.objectrocket.com:54074/?replicaSet=e0a8d0f797be1b9c4ec7052a7b7484a7");

Connecting to a replica set with SSL:
::
   
 <?php
 $connection = new MongoClient("mongodb://sjc-c9-1.objectrocket.com:54074,sjc-c9-0.objectrocket.com:54074/?replicaSet=e0a8d0f797be1b9c4ec7052a7b7484a7", array("ssl" => true));

Connecting to a sharded instance:
::
   
 <?php
 $connection = new MongoClient("mongodb://iad-mongos0.objectrocket.com:15045");

Connecting to a sharded instance with SSL:
::

 <?php
 $connection = new MongoClient("mongodb://iad-mongos0.objectrocket.com:15045", array("ssl" => true));


Creating a Document
-------------------

PHP representation and inserting the document
::

 <?php

 $doc = array(
    "date" => new MongoDate(strtotime("2014-05-26 02:00:22")),
      "winner" => "Javi",
      "logged" => TRUE,
      "decks" => array( "first" => array("Dinosaurs","Plants"), "second" => array("Spies","Zombies"), "third" => array("Steampunk","Wizards"), "fourth" => array("Shapeshifters", "Ninjas")),
      "prior_winner" => "Castro",
      "points" => array( 24, 20, 20, 18),
      "players" => array( "first" => "Javi", "second" => "Seth", "third" => "Dave", "fourth" => "Castro")
      );

 $connection = new MongoClient("mongodb://myUsername:myPassword@hkg-mongos0.objectrocket.com:31062/myDatabaseName");

 $database = $connection->myDatabaseName;

 $collection = $database->myCollectionName;
 
 $collection->insert( $doc );

 ?>

The resulting document directly from MongoDB
::

 > db.myCollectionName.find().pretty()
 {
	"_id" : ObjectId("55b29160d5d145e1438b4567"),
	"date" : ISODate("2014-05-26T02:00:22Z"),
	"winner" : "Javi",
	"logged" : true,
	"decks" : {
		"first" : [
			"Dinosaurs",
			"Plants"
		],
		"second" : [
			"Spies",
			"Zombies"
		],
		"third" : [
			"Steampunk",
			"Wizards"
		],
		"fourth" : [
			"Shapeshifters",
			"Ninjas"
		]
	},
	"prior_winner" : "Castro",
	"points" : [
		NumberLong(24),
		NumberLong(20),
		NumberLong(20),
		NumberLong(18)
	],
	"players" : {
		"first" : "Javi",
		"second" : "Seth",
		"third" : "Dave",
		"fourth" : "Castro"
	}
 } 






 











.. _Official Documentation: http://docs.mongodb.org/ecosystem/drivers/php/
