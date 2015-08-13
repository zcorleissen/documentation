Ruby Driver Examples
===================

.. |checkmark| unicode:: U+2713

The `Ruby driver https://github.com/mongodb/mongo-ruby-driver`_ is an official driver maintained by MongoDB. It is written in Ruby, and is currently compatible with the following versions of MongoDB:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :widths: 25 25 25 25
   :class: compatibility

   * - Ruby Driver
     - MongoDB 2.4
     - MongoDB 2.6
     - MongoDB 3.0

   * - 2.0
     - |checkmark|
     - |checkmark|
     - |checkmark|

   * - 1.12
     - |checkmark|
     - |checkmark|
     - |checkmark|

The current version of the Ruby driver supports the following versions of Ruby:

.. list-table::
   :header-rows: 1
   :stub-columns: 1
   :class: compatibility

   * - Ruby Driver 
     - Ruby 1.8.7
     - Ruby 1.9
     - Ruby 2.0
     - Ruby 2.1
     - JRuby

   * - 2.0
     - 
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|

   * - 1.9
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|
     - |checkmark|

Installation
------------

The Ruby driver is bundled as a gem, and can be installed like so:

.. code-block:: bash

   $ gem install mongo


Example document
----------------

Here's the example document we'll be using:

.. code-block:: javascript

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

Connecting
----------

Connecting to a replica set:

.. code-block:: php
   
 <?php
 $connection = new MongoClient("mongodb://sjc-c9-1.objectrocket.com:54074,sjc-c9-0.objectrocket.com:54074/?replicaSet=e0a8d0f797be1b9c4ec7052a7b7484a7");
 ?>

Connecting to a sharded instance:

.. code-block:: php

 <?php
 $connection = new MongoClient("mongodb://iad-mongos0.objectrocket.com:15045");
 ?>

Connecting to a sharded instance with SSL:

.. code-block:: php

 <?php
 $connection = new MongoClient("mongodb://iad-mongos0.objectrocket.com:15045", array("ssl" => true));
 ?>

Creating a Document
-------------------

Creating and inserting the document:

.. code-block:: php

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

The resulting document seen through the MongoDB shell:

.. code-block:: javascript

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
-----------------

Finding all documents with a specific field:

.. code-block:: php

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


Output from above:

.. code-block:: php
   
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


Updating a document
-------------------

Updating a document:

.. code-block:: php

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


The resulting document as seen from the MongoDB shell:

.. code-block:: javascript

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


Deleting a document
-------------------

Deleting a document:

.. code-block:: php

 <?php

 $connection = new MongoClient("mongodb://myUsername:myPassword@hkg-mongos0.objectrocket.com:31062/myDatabaseName");

 $database = $connection->myDatabaseName;

 $collection = $database->myCollectionName;


 $query = array("winner" => "Castro");

 $retval = $collection->remove($query);

 var_dump($retval);

 ?>


Output from above:

.. code-block:: php

 array(6) {
  ["singleShard"]=>
  string(161) "0c86375ef57646f094a0a27164679c33/hkgclus1br0vz17.hkg.objectrocket.com:32728,hkgclus1br1vz17.hkg.objectrocket.com:32728,hkgclus1br2vz17.hkg.objectrocket.com:32728"
  ["n"]=>
  int(1)
  ["lastOp"]=>
  object(MongoTimestamp)#6 (2) {
    ["sec"]=>
    int(1437769866)
    ["inc"]=>
    int(1)
  }
  ["connectionId"]=>
  int(64925)
  ["err"]=>
  NULL
  ["ok"]=>
  float(1)
 }

Additional reading
------------------

If you need more help with the PHP driver, links to official documentation are below:

* `PHP Driver Documentation <http://docs.mongodb.org/ecosystem/drivers/php/>`_
* `MongoDB for the PHP Mind, Part 1 <http://blog.mongodb.org/post/24960636131/mongodb-for-the-php-mind-part-1>`_
* `PHP.net MongoDB Driver documentation <http://us2.php.net/mongo>`_
* `MongoDB PHP Driver Github <https://github.com/mongodb/mongo-php-driver>`_
