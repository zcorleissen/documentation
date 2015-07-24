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


Reading documents
-------------------

Finding all documents searching by a specific field
::

 <?php

 $connection = new MongoClient("mongodb://myUsername:myPassword@hkg-mongos0.objectrocket.com:31062/myDatabaseName");

 $database = $connection->myDatabaseName;

 $collection = $database->myCollectionName;


 $query = array("winner" => "Javi");

 $cursor = $collection->find($query);
 foreach ($cursor as $doc) {
    var_dump($doc);
 }

 ?>


Console output for the above code
::
   
 array(8) {
  ["_id"]=>
  object(MongoId)#7 (1) {
    ["$id"]=>
    string(24) "55b29160d5d145e1438b4567"
  }
  ["date"]=>
  object(MongoDate)#8 (2) {
    ["sec"]=>
    int(1401069622)
    ["usec"]=>
    int(0)
  }
  ["winner"]=>
  string(4) "Javi"
  ["logged"]=>
  bool(true)
  ["decks"]=>
  array(4) {
    ["first"]=>
    array(2) {
      [0]=>
      string(9) "Dinosaurs"
      [1]=>
      string(6) "Plants"
    }
    ["second"]=>
    array(2) {
      [0]=>
      string(5) "Spies"
      [1]=>
      string(7) "Zombies"
    }
    ["third"]=>
    array(2) {
      [0]=>
      string(9) "Steampunk"
      [1]=>
      string(7) "Wizards"
    }
    ["fourth"]=>
    array(2) {
      [0]=>
      string(13) "Shapeshifters"
      [1]=>
      string(6) "Ninjas"
    }
  }
  ["prior_winner"]=>
  string(6) "Castro"
  ["points"]=>
  array(4) {
    [0]=>
    int(24)
    [1]=>
    int(20)
    [2]=>
    int(20)
    [3]=>
    int(18)
  }
  ["players"]=>
  array(4) {
    ["first"]=>
    string(4) "Javi"
    ["second"]=>
    string(4) "Seth"
    ["third"]=>
    string(4) "Dave"
    ["fourth"]=>
    string(6) "Castro"
  }
 }


Updating a Document
-------------------

Updating a document
::

 <?php

 $connection = new MongoClient("mongodb://myUsername:myPassword@hkg-mongos0.objectrocket.com:31062/myDatabaseName");

 $database = $connection->myDatabaseName;

 $collection = $database->myCollectionName;


 $retval = $collection->findAndModify(
    array("winner" => "Javi", "logged" => TRUE),
    array('$set' => array("winner" => "Castro", "logged" => FALSE, "players.first" => "Castro", "players.fourth" => "Javi")),
    null,
    array("new" => TRUE)
 );

 ?>


The resulting document directly from MongoDB
::

 > db.myCollectionName.find().pretty()
 {
	"_id" : ObjectId("55b29b5ed5d145014f8b4567"),
	"date" : ISODate("2014-05-26T02:00:22Z"),
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
	"logged" : false,
	"players" : {
		"first" : "Castro",
		"fourth" : "Javi",
		"second" : "Seth",
		"third" : "Dave"
	},
	"points" : [
		NumberLong(24),
		NumberLong(20),
		NumberLong(20),
		NumberLong(18)
	],
	"prior_winner" : "Castro",
	"winner" : "Castro"
 }








.. _Official Documentation: http://docs.mongodb.org/ecosystem/drivers/php/
