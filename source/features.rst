Features
========


Copying a Remote Database
-------------------------

ObjectRocket provides a database import tool for customers running MongoDB 2.4
and above. It is available for use from your instance's details page.


Arguments
^^^^^^^^^

* Remote Connect String: The host and port of your remote database
  (myhost.com:27017)
* Remote Database Name: The name of your remote database. A database of the
  same name will be created in your ObjectRocket instance.
* Remote Database Username, Password: The username and password we will use
  to copy your database.


Caveats
^^^^^^^

We will not attempt to copy your database if any of the following conditions
are true:

* You have a database of the same name as your remote database in your
  ObjectRocket instance.
* Your remote database is using a version of MongoDB newer than your
  ObjectRocket instance.
* We cannot authenticate against your remote database.
* There isn't enough free space available to store your remote database.
* Your remote database is sharded through mongos.
