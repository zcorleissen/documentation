Onboarding Checklist
======================================

Overview
--------

This guide is intended to enumerate the questions that need to be answered in order size out and quote a plan size for new custom instance on the ObjectRocket platform.  The following questions need to be answered:

Checklist
---------

MongoDB
^^^^^^^

- What is the MongoDB version of the existing instance?
- Where is the existing instance hosted?

Drivers
^^^^^^^

- What language is the driver(s) being used?
- What version(s)?

Storage Space
^^^^^^^^^^^^^

- Run the following commands in the MongoDB mongos shell:

.. code-block:: javascript

    var arr = db.getMongo().getDBNames();
    for ( i in arr ) {
        c = db.getSiblingDB(arr[i]).stats();
        var r=eval(c);
        printjson(r);
    }

- Run the following commands in the MongoDB shell on each MongoD:

.. code-block:: javascript

    rs.status();

Sharding
^^^^^^^^

- Is the database sharded?  If not, are you planning to?
- Run the following commands in the MongoDB mongos shell:

.. code-block:: javascript

    sh.status();

OpCounters
^^^^^^^^^^

- Run the following commands in the MongoDB shell on each MongoD:

.. code-block:: javascript

    for (var i = 0; i<3; i++) {
        c = db.serverStatus()['opcounters'];
        var r=eval(c);
        printjson(r);
        sleep(10000);
    }

Document Design
^^^^^^^^^^^^^^^

- Run the following commands in the MongoDB mongos shell:

.. code-block:: javascript

    db.system.indexes.find();

.. code-block:: javascript

    db.system.namespaces.find();

