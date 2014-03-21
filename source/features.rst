Features
========


Instance Compaction
-------------------

ObjectRocket provides tools for compacting instances on a per request basis,
as well as weekly compaction. To request compaction for one of your instances,
navigate to the ``/instances`` page and click the ``Compact`` button in the
upper right corner of the instance panel.


Weekly Compaction
^^^^^^^^^^^^^^^^^

To enable weekly compaction, see the settings documentation for
`Weekly Compaction <http://docs.objectrocket.com/settings_guide.html#options>`_


Caveats
^^^^^^^

Compaction will not be requested for an instance under the following
circumstances:

* The instance is currently undergoing compaction.
* The instance plan is 100GB or greater. In this case, contact support.


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
