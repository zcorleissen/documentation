General Resources
=================

Get details on all plans.
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /plans/

Response:

.. code-block:: bash

   {
       "data": [
           {
               "cost": 1900,
               "id": "5286929405533c1306c1cf79",
               "instance_type": "mongodb_replica_set",
               "region": "US",
               "service_type": "mongodb",
               "size": "RS"
           },
           {
               "cost": 2500,
               "id": "52debc5024815a22d1097237",
               "instance_type": "mongodb_replica_set",
               "region": "LON",
               "service_type": "mongodb",
               "size": "RS"
           },
           {
               "cost": 19000,
               "id": "52debc5024815a22d1097238",
               "instance_type": "mongodb_sharded",
               "region": "LON",
               "service_type": "mongodb",
               "size": "5"
           },
           {
               "cost": 50000,
               "id": "52debc5024815a22d1097239",
               "instance_type": "mongodb_sharded",
               "region": "LON",
               "service_type": "mongodb",
               "size": "20"
           },
           {
               "cost": 112500,
               "id": "52debc5024815a22d109723a",
               "instance_type": "mongodb_sharded",
               "region": "LON",
               "service_type": "mongodb",
               "size": "50"
           },
           {
               "cost": 200000,
               "id": "52debc5124815a22d109723b",
               "instance_type": "mongodb_sharded",
               "region": "LON",
               "service_type": "mongodb",
               "size": "100"
           },
           {
               "cost": 470000,
               "id": "52debc5124815a22d109723c",
               "instance_type": "mongodb_sharded",
               "region": "LON",
               "service_type": "mongodb",
               "size": "250"
           },
           {
               "cost": 14900,
               "id": "52debc5224815a22d109723e",
               "instance_type": "mongodb_sharded",
               "region": "US",
               "service_type": "mongodb",
               "size": "5"
           },
           {
               "cost": 39900,
               "id": "52debc5224815a22d109723f",
               "instance_type": "mongodb_sharded",
               "region": "US",
               "service_type": "mongodb",
               "size": "20"
           },
           {
               "cost": 89900,
               "id": "52debc5224815a22d1097240",
               "instance_type": "mongodb_sharded",
               "region": "US",
               "service_type": "mongodb",
               "size": "50"
           },
           {
               "cost": 369900,
               "id": "52debc5924815a22d1097241",
               "instance_type": "mongodb_sharded",
               "region": "US",
               "service_type": "mongodb",
               "size": "250"
           },
           {
               "cost": 159900,
               "id": "52debc7b24815a22d1097242",
               "instance_type": "mongodb_sharded",
               "region": "US",
               "service_type": "mongodb",
               "size": "100"
           },
           {
               "cost": 2500,
               "id": "530fc393ac74068a95d783fa",
               "instance_type": "mongodb_replica_set",
               "region": "HKG",
               "service_type": "mongodb",
               "size": "RS"
           },
           {
               "cost": 19500,
               "id": "530fc393ac74068a95d783fb",
               "instance_type": "mongodb_sharded",
               "region": "HKG",
               "service_type": "mongodb",
               "size": "5"
           },
           {
               "cost": 52500,
               "id": "530fc393ac74068a95d783fc",
               "instance_type": "mongodb_sharded",
               "region": "HKG",
               "service_type": "mongodb",
               "size": "20"
           },
           {
               "cost": 117500,
               "id": "530fc393ac74068a95d783fd",
               "instance_type": "mongodb_sharded",
               "region": "HKG",
               "service_type": "mongodb",
               "size": "50"
           },
           {
               "cost": 207500,
               "id": "530fc394ac74068a95d783fe",
               "instance_type": "mongodb_sharded",
               "region": "HKG",
               "service_type": "mongodb",
               "size": "100"
           },
           {
               "cost": 485000,
               "id": "530fc394ac74068a95d783ff",
               "instance_type": "mongodb_sharded",
               "region": "HKG",
               "service_type": "mongodb",
               "size": "250"
           },
           {
               "cost": 2500,
               "id": "53346ec90066a14f1f2f7886",
               "instance_type": "mongodb_replica_set",
               "region": "SYD",
               "service_type": "mongodb",
               "size": "RS"
           },
           {
               "cost": 19500,
               "id": "53346ed00066a14f1f2f7887",
               "instance_type": "mongodb_sharded",
               "region": "SYD",
               "service_type": "mongodb",
               "size": "5"
           },
           {
               "cost": 52500,
               "id": "53346ed70066a14f1f2f7888",
               "instance_type": "mongodb_sharded",
               "region": "SYD",
               "service_type": "mongodb",
               "size": "20"
           },
           {
               "cost": 117500,
               "id": "53346edc0066a14f1f2f7889",
               "instance_type": "mongodb_sharded",
               "region": "SYD",
               "service_type": "mongodb",
               "size": "50"
           },
           {
               "cost": 207500,
               "id": "53346ee20066a14f1f2f788a",
               "instance_type": "mongodb_sharded",
               "region": "SYD",
               "service_type": "mongodb",
               "size": "100"
           },
           {
               "cost": 485000,
               "id": "53346ee70066a14f1f2f788b",
               "instance_type": "mongodb_sharded",
               "region": "SYD",
               "service_type": "mongodb",
               "size": "250"
           },
           {
               "cost": 5900,
               "id": "540e029c6766421f86a30f1f",
               "instance_type": "redis_ha_instance",
               "region": "US",
               "service_type": "redis",
               "size": "500"
           },
           {
               "cost": 9900,
               "id": "540e029c6766421f86a30f20",
               "instance_type": "redis_ha_instance",
               "region": "US",
               "service_type": "redis",
               "size": "1000"
           },
           {
               "cost": 21900,
               "id": "540e029c6766421f86a30f21",
               "instance_type": "redis_ha_instance",
               "region": "US",
               "service_type": "redis",
               "size": "2500"
           },
           {
               "cost": 42900,
               "id": "540e029d6766421f86a30f22",
               "instance_type": "redis_ha_instance",
               "region": "US",
               "service_type": "redis",
               "size": "5000"
           },
           {
               "cost": 84900,
               "id": "540e029d6766421f86a30f23",
               "instance_type": "redis_ha_instance",
               "region": "US",
               "service_type": "redis",
               "size": "10000"
           },
           {
               "cost": 164900,
               "id": "540e029e6766421f86a30f24",
               "instance_type": "redis_ha_instance",
               "region": "US",
               "service_type": "redis",
               "size": "20000"
           },
           {
               "cost": 399900,
               "id": "540e029e6766421f86a30f25",
               "instance_type": "redis_ha_instance",
               "region": "US",
               "service_type": "redis",
               "size": "50000"
           },
           {
               "cost": 7900,
               "id": "540e029f6766421f86a30f26",
               "instance_type": "redis_ha_instance",
               "region": "LON",
               "service_type": "redis",
               "size": "500"
           },
           {
               "cost": 12900,
               "id": "540e029f6766421f86a30f27",
               "instance_type": "redis_ha_instance",
               "region": "LON",
               "service_type": "redis",
               "size": "1000"
           },
           {
               "cost": 27900,
               "id": "540e029f6766421f86a30f28",
               "instance_type": "redis_ha_instance",
               "region": "LON",
               "service_type": "redis",
               "size": "2500"
           },
           {
               "cost": 54900,
               "id": "540e02a06766421f86a30f29",
               "instance_type": "redis_ha_instance",
               "region": "LON",
               "service_type": "redis",
               "size": "5000"
           },
           {
               "cost": 695000,
               "id": "54adc47a168fd30b467bc19f",
               "instance_type": "mongodb_sharded",
               "region": "US",
               "service_type": "mongodb",
               "size": "500"
           },
           {
               "cost": 969900,
               "id": "54adc499168fd30b467bc1a0",
               "instance_type": "mongodb_sharded",
               "region": "US",
               "service_type": "mongodb",
               "size": "750"
           },
           {
               "cost": 1245000,
               "id": "54adc4d8168fd30b467bc1a1",
               "instance_type": "mongodb_sharded",
               "region": "US",
               "service_type": "mongodb",
               "size": "1000"
           },
           {
               "cost": 9500,
               "id": "54cc1fdc168fd35b224de6cc",
               "instance_type": "mongodb_jumbo_replica_set",
               "region": "US",
               "service_type": "mongodb",
               "size": "5"
           },
           {
               "cost": 25000,
               "id": "54cc1fdd168fd35b224de6cd",
               "instance_type": "mongodb_jumbo_replica_set",
               "region": "US",
               "service_type": "mongodb",
               "size": "20"
           },
           {
               "cost": 57500,
               "id": "54cc1fdd168fd35b224de6ce",
               "instance_type": "mongodb_jumbo_replica_set",
               "region": "US",
               "service_type": "mongodb",
               "size": "50"
           },
           {
               "cost": 102500,
               "id": "54cc1fdd168fd35b224de6cf",
               "instance_type": "mongodb_jumbo_replica_set",
               "region": "US",
               "service_type": "mongodb",
               "size": "100"
           },
           {
               "cost": 579900,
               "id": "552c2ec5872446aa096dd171",
               "instance_type": "redis_ha_instance",
               "region": "US",
               "service_type": "redis",
               "size": "75000"
           },
           {
               "cost": 749900,
               "id": "552c2ec5872446aa096dd172",
               "instance_type": "redis_ha_instance",
               "region": "US",
               "service_type": "redis",
               "size": "100000"
           },
           {
               "cost": 729900,
               "id": "552c2ec5872446aa096dd173",
               "instance_type": "redis_ha_instance",
               "region": "LON",
               "service_type": "redis",
               "size": "75000"
           },
           {
               "cost": 949900,
               "id": "552c2ec5872446aa096dd174",
               "instance_type": "redis_ha_instance",
               "region": "LON",
               "service_type": "redis",
               "size": "100000"
           },
           {
               "cost": 2900,
               "id": "55498f750c2d3550a5d85d58",
               "instance_type": "mongodb_sharded",
               "region": "US",
               "service_type": "mongodb",
               "size": "1"
           },
           {
               "cost": 104900,
               "id": "540e02a06766421f86a30f2a",
               "instance_type": "redis_ha_instance",
               "region": "LON",
               "service_type": "redis",
               "size": "10000"
           },
           {
               "cost": 209900,
               "id": "540e02a16766421f86a30f2b",
               "instance_type": "redis_ha_instance",
               "region": "LON",
               "service_type": "redis",
               "size": "20000"
           },
           {
               "cost": 499900,
               "id": "540e02a26766421f86a30f2c",
               "instance_type": "redis_ha_instance",
               "region": "LON",
               "service_type": "redis",
               "size": "50000"
           },
           {
               "cost": 2500,
               "id": "559c3f86759d6306ed1e4305",
               "instance_type": "elasticsearch",
               "region": "US",
               "service_type": "elasticsearch",
               "size": "2"
           },
           {
               "cost": 4900,
               "id": "559c3f86759d6306ed1e4306",
               "instance_type": "elasticsearch",
               "region": "US",
               "service_type": "elasticsearch",
               "size": "4"
           },
           {
               "cost": 8900,
               "id": "559c3f86759d6306ed1e4307",
               "instance_type": "elasticsearch",
               "region": "US",
               "service_type": "elasticsearch",
               "size": "8"
           },
           {
               "cost": 13900,
               "id": "559c3f86759d6306ed1e4308",
               "instance_type": "elasticsearch",
               "region": "US",
               "service_type": "elasticsearch",
               "size": "16"
           },
           {
               "cost": 23900,
               "id": "559c3f86759d6306ed1e4309",
               "instance_type": "elasticsearch",
               "region": "US",
               "service_type": "elasticsearch",
               "size": "32"
           },
           {
               "cost": 44900,
               "id": "559c3f86759d6306ed1e430a",
               "instance_type": "elasticsearch",
               "region": "US",
               "service_type": "elasticsearch",
               "size": "64"
           },
           {
               "cost": 79900,
               "id": "559c3f86759d6306ed1e430b",
               "instance_type": "elasticsearch",
               "region": "US",
               "service_type": "elasticsearch",
               "size": "128"
           },
           {
               "cost": 149900,
               "id": "559c3f86759d6306ed1e430c",
               "instance_type": "elasticsearch",
               "region": "US",
               "service_type": "elasticsearch",
               "size": "256"
           },
           {
               "cost": 279900,
               "id": "559c3f86759d6306ed1e430d",
               "instance_type": "elasticsearch",
               "region": "US",
               "service_type": "elasticsearch",
               "size": "512"
           }
       ]
   }

Get details on the plan specified by ID.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /plans/<plan_id>/

Response:

.. code-block:: bash

   {
       "data": {
           "cost": 279900,
           "id": "559c3f86759d6306ed1e430d",
           "instance_type": "elasticsearch",
           "region": "US",
           "service_type": "elasticsearch",
           "size": "512"
       }
   }

Record the contact form data, and notify sales.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /contact/

Request/Response:

.. code-block:: bash

   $ ERROR

Get details on an account.
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /accounts/<user_id>/

Response:

.. code-block:: bash

   {
       "data": {
           "accepted_msa": 1,
           "active": true,
           "add_instance_enabled": true,
           "company": "ObjectRocket",
           "creation_date": {
               "$date": 1430225967037
           },
           "email": "donovan@heydonovan.io",
           "has_casters_access": false,
           "id": "553fe69f5b335278436fa19b",
           "login": "donovan@heydonovan.io",
           "migrated": false,
           "name": "Donovan Hernandez",
           "phone": "4592222",
           "settings": {
               "stats_enabled": true
           },
           "zipcode": "78701"
       }
   }

Set the CC info for the authenticated account.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /accounts/<uid>/set_card/

Request/Response:

.. code-block:: bash

   $ ERROR

Get details on all casters belonging to this account.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /casters/

Request/Response:

.. code-block:: bash

   $ ERROR

Get details on a caster specified by ID.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /casters/<caster_id>/

Request/Response:

.. code-block:: bash

   $ ERROR

Get the data for an ad-hoc query request.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /graphs/

Request/Response:

.. code-block:: bash

   $ ERROR

Get both the replset infrastructure and the list of stats for a host.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /instances/<instance_name>/stats_config/

Response:

.. code-block:: bash

   {
       "shards": {
           "5db16d02db25b9673ff2f72440366df0": [
               "sydclus2br0vz18.syd.objectrocket.com:31134",
               "sydclus2br1vz18.syd.objectrocket.com:31134",
               "sydclus2br2vz18.syd.objectrocket.com:31134"
           ],
           "90a85209de63519f0c04728a1bdb9313": [
               "sydclus1br0vz10.syd.objectrocket.com:31166",
               "sydclus1br1vz10.syd.objectrocket.com:31166",
               "sydclus1br2vz10.syd.objectrocket.com:31166"
           ]
       },
       "stat_names": [
           "mongodb.connections.current",
           "mongodb.Database123.collections",
           "mongodb.Database123.dataSize",
           "mongodb.Database123.indexSize",
           "mongodb.Database123.indexes",
           "mongodb.Database123.numExtents",
           "mongodb.Database123.objects",
           "mongodb.Database123.storageSize",
           "mongodb.Database123.timeAcquiringMicros.r",
           "mongodb.Database123.timeAcquiringMicros.w",
           "mongodb.Database123.timeLockedMicros.r",
           "mongodb.Database123.timeLockedMicros.w",
           "mongodb.Name123.collections",
           "mongodb.Name123.dataSize",
           "mongodb.Name123.indexSize",
           "mongodb.Name123.indexes",
           "mongodb.Name123.numExtents",
           "mongodb.Name123.objects",
           "mongodb.Name123.storageSize",
           "mongodb.Name123.timeAcquiringMicros.r",
           "mongodb.Name123.timeAcquiringMicros.w",
           "mongodb.Name123.timeLockedMicros.r",
           "mongodb.Name123.timeLockedMicros.w",
           "mongodb.database1.collections",
           "mongodb.database1.dataSize",
           "mongodb.database1.indexSize",
           "mongodb.database1.indexes",
           "mongodb.database1.numExtents",
           "mongodb.database1.objects",
           "mongodb.database1.storageSize",
           "mongodb.database1.timeAcquiringMicros.r",
           "mongodb.database1.timeAcquiringMicros.w",
           "mongodb.database1.timeLockedMicros.r",
           "mongodb.database1.timeLockedMicros.w",
           "mongodb.db1.collections",
           "mongodb.db1.dataSize",
           "mongodb.db1.indexSize",
           "mongodb.db1.indexes",
           "mongodb.db1.numExtents",
           "mongodb.db1.objects",
           "mongodb.db1.storageSize",
           "mongodb.db1.timeAcquiringMicros.r",
           "mongodb.db1.timeAcquiringMicros.w",
           "mongodb.db1.timeLockedMicros.r",
           "mongodb.db1.timeLockedMicros.w",
           "mongodb.globalLock.currentQueue.readers",
           "mongodb.globalLock.currentQueue.total",
           "mongodb.globalLock.currentQueue.writers",
           "mongodb.mem.mapped",
           "mongodb.mem.resident",
           "mongodb.mem.virtual",
           "mongodb.opcounters.command",
           "mongodb.opcounters.delete",
           "mongodb.opcounters.getmore",
           "mongodb.opcounters.insert",
           "mongodb.opcounters.query",
           "mongodb.opcounters.update",
           "mongodb.test.collections",
           "mongodb.test.dataSize",
           "mongodb.test.indexSize",
           "mongodb.test.indexes",
           "mongodb.test.numExtents",
           "mongodb.test.objects",
           "mongodb.test.storageSize",
           "mongodb.test.timeAcquiringMicros.r",
           "mongodb.test.timeAcquiringMicros.w",
           "mongodb.test.timeLockedMicros.r",
           "mongodb.test.timeLockedMicros.w"
       ]
   }

Get all dashboards for the specified account.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /dashboards/

Request/Response:

.. code-block:: bash

   $ ERROR

Create a new dashboard.
~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /dashboards/

Request/Response:

.. code-block:: bash

   $ ERROR

Get the dashboard specified by ID.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /dashboards/<dashboard_id>/

Request/Response:

.. code-block:: bash

   $ ERROR

Update the dashboard specified by ID.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   PUT /dashboards/<dashboard_id>/

Request/Response:

.. code-block:: bash

   $ ERROR

Delete the dashboard specified by ID.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   DELETE /dashboards/<dashboard_id>/

Request/Response:

.. code-block:: bash

   $ ERROR

