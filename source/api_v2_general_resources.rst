General Resources
=================

Get details on all plans
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
               "cost": 5900,
               "id": "540e029c6766421f86a30f1f",
               "instance_type": "redis_ha_instance",
               "region": "US",
               "service_type": "redis",
               "size": "500"
           },
           {
               "..."
           }
       ]
   }

Get details on the plan specified by ID
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

Get details on an account
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

Get the data for an ad-hoc query request
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /graphs/ad_hoc/

.. note::

   There are four query paramters that need to be present:

   **format**:
      This has to be zingchart for now

   **granularity**:
      Either minute or day

   **start_time**:
      A start time in the following format: "Year-Month-Day Hour:Minute:Second"

   **end_time**:
      An end time in the following format: "Year-Month-Day Hour:Minute:Second"

Request:

.. code-block:: bash

   POST /v2/graphs/ad_hoc/?start_time=2015-09-01+00%3A01%3A01&format=zingchart&end_time=2015-09-01+03%3A01%3A01&granularity=hour HTTP/1.1

   {
       "stats": [
           {
               "host": "sydclus2br0vz18.syd.objectrocket.com:31134",
               "instance": "MongoDB123",
               "name": "mongodb.opcounters.query"
           },
           {
               "host": "sydclus1br2vz10.syd.objectrocket.com:31166",
               "instance": "MongoDB123",
               "name": "mongodb.opcounters.query"
           },
           {
               "host": "sydclus2br0vz28.syd.objectrocket.com:32795",
               "instance": "MongoDB123",
               "name": "mongodb.opcounters.query"
           }
       ]
   }

Response:

.. code-block:: bash

   [
       {
           "legend-item": {
               "text": "sydclus2br0vz18"
           },
           "text": "sydclus2br0vz18",
           "values": [
               [
                   1441069200000,
                   0
               ],
               [
                   1441069260000,
                   0
               ],
               [
                   "..."
               ]
           ]
       },
       {
           "legend-item": {
               "text": "sydclus1br2vz10"
           },
           "text": "sydclus1br2vz10",
           "values": [
               [
                   1441069200000,
                   0
               ],
               [
                   1441069260000,
                   0
               ],
               [
                   "..."
               ]
           ]
       },
       {
           "legend-item": {
               "text": "sydclus2br0vz28"
           },
           "text": "sydclus2br0vz28",
           "values": [
               [
                   1441069200000,
                   0
               ],
               [
                   1441069260000,
                   0
               ],
               [
                   "..."
               ]
       }
   ]

Get both the replset infrastructure and the list of stats for a host
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
           "mongodb.opcounters.update"
       ]
   }
