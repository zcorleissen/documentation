Instance Resources
==================

Get details on an account's instances
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /instances/

Response:

.. code-block:: bash

   {
       "data": [
           {
               "api_key": "708b16dca77f43938621c3b078b8b850",
               "caster": null,
               "connect_string": "b7fe19ed2fc72339f180961027d5c321/syd-c0-1.objectrocket.com:55029,syd-c0-0.objectrocket.com:55029",
               "created": "2015-07-29 14:19:38",
               "id": "55b9436bc3fbcc12b1d98963",
               "name": "test666",
               "plan": 1,
               "service": "mongodb",
               "type": "mongodb_replica_set",
               "version": "2.4.6",
               "zone": "AP-Sydney"
           },
           {
               "api_key": "fb9ccdeec96d4b709867369248a29935",
               "caster": null,
               "connect_string": "syd-mongos0.objectrocket.com:35036",
               "created": "2015-07-27 09:17:33",
               "id": "55b6599ecb143c243a21ac38",
               "name": "test1234",
               "plan": 5,
               "service": "mongodb",
               "ssl_connect_string": "syd-mongos0.objectrocket.com:45036",
               "type": "mongodb_sharded",
               "version": "2.4.6",
               "zone": "AP-Sydney"
           },
           {
               "api_key": "cc6a39b8debb4d2b9bac65071050a56c",
               "caster": null,
               "clb_id": null,
               "connect_string": "redis://2dbc8a2ea54d423c992aa2bb54ab69d1.publb.rackspaceclouddb.com:6379",
               "created": "2015-05-29 09:00:35",
               "id": "55688d235b335275dd2e17cd",
               "name": "Test1234",
               "password": "C2JwY3pqvjwPGqerhADYhF9jPQTdBKJVHfca",
               "plan": 2500,
               "public_connect_string": "redis://2dbc8a2ea54d423c992aa2bb54ab69d1.publb.rackspaceclouddb.com:6379",
               "service": "redis",
               "servicenet_connect_string": "redis://4762de18916141c2b6179e38ea90b999.publb.rackspaceclouddb.com:6379",
               "state": "ACTIVE",
               "type": "redis_ha_instance",
               "version": "2.8.17",
               "zone": "US-East-IAD3"
           },
           {
               "api_key": "4aa8a323d92d4253bd02c0992d621560",
               "caster": null,
               "connect_string": "syd-mongos0.objectrocket.com:35023",
               "created": "2015-04-29 09:53:18",
               "id": "55410c7f5b335278490a5be8",
               "name": "Test123",
               "plan": 5,
               "service": "mongodb",
               "ssl_connect_string": "syd-mongos0.objectrocket.com:45023",
               "type": "mongodb_sharded",
               "version": "2.4.6",
               "zone": "AP-Sydney"
           }
       ]
   }

Create a new instance
~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /instances/

.. note::

   The **service** field must be one of the following: elasticsearch, mongodb, mysql, or redis.

   **elasticsearch**:
      Plans available: 2, 4, 8, 16, 32, 64, 128, 256, and 512.

      Types available: elasticsearch.

      Versions available: 1.6.2, and 1.7.1.

      Zones available: US-East-IAD1, and US-Dallas.

   **mongodb**:
      Plans available: 1, 5, 20, 50, and 100.

      Types available: mongodb_sharded, mongodb_replica_set, and mongodb_jumbo_replica_set.

      Versions available: 2.4.6, 2.6.10, and 3.0.5.

      Zones available: US-East-IAD3, US-West, EU-London, AP-HongKong, US-Chicago, AP-Sydney, and US-Dallas.

   **mysql**:
      ERROR

   **redis**:
      Plans available: 500, 1000, 2500, 5000, 10000, 20000, 50000, 75000, and 100000.

      Types available: redis_ha_instance.

      Versions available: 2.8.17, 2.8.21, and 3.0.3.

      Zones available: EU-London, US-Chicago, US-East-IAD3, and US-Dallas.

Request:

.. code-block:: bash

   {
       "name": "TEST123",
       "plan": 2,
       "service": "elasticsearch",
       "type": "elasticsearch",
       "version": "1.6.2",
       "zone": "US-East-IAD1"
   }

Response:

.. code-block:: bash

   {
       "data": {
           "_id": {
               "$oid": "55e0a924cb143c426df6927e"
           },
           "ansible_group": null,
           "api_key": "2f91e30a48d94ef0ba403edf017d9e60",
           "build_id": "55e0a924cb143c426df6927d",
           "dtcreated": {
               "$date": 1440761524190
           },
           "elasticsearch_version": "1.6.2",
           "instance_name_prior": null,
           "instance_service": "elasticsearch",
           "instance_type": "elasticsearch",
           "login": "donovan@heydonovan.io",
           "login_prior": null,
           "name": "TEST123",
           "plan": 2,
           "state": "REQUESTED",
           "zone": "US-East-IAD1"
       }
   }

Get details on the specified instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /instances/<instance_name>/

Response:

.. code-block:: bash

   {
       "data": {
           "api_key": "4aa8a323d92d4253bd02c0992d621560",
           "caster": null,
           "connect_string": "syd-mongos0.objectrocket.com:35023",
           "created": "2015-04-29 09:53:18",
           "id": "55410c7f5b335278490a5be8",
           "name": "Test123",
           "plan": 5,
           "service": "mongodb",
           "ssl_connect_string": "syd-mongos0.objectrocket.com:45023",
           "type": "mongodb_sharded",
           "version": "2.4.6",
           "zone": "AP-Sydney"
       }
   }

Delete the specified instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   DELETE /instances/<instance_name>/

Response:

.. code-block:: bash

   {
       "data": "Successfully deleted Instance \"Test123\"."
   }

Rename the specified instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /instances/<instance_name>/rename/

Request:

.. code-block:: bash

   {
       "name": "Test456"
   }

Response:

.. code-block:: bash

   {
       "data": "Successfully renamed instance from \"Test123\" to \"Test456\"."
   }

Get a list of ACLs for the given instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /instances/<instance_name>/acls/

Response:

.. code-block:: bash

   {
       "data": [
           {
               "_cls": "Acl",
               "_id": {
                   "$oid": "55410e3d5b33522f64f9ca6f"
               },
               "cidr_mask": "128.0.0.0/1",
               "date_created": {
                   "$date": 1430326845000
               },
               "description": "Allow Any",
               "instance": "Test123",
               "login": "donovan@heydonovan.io",
               "metadata": {},
               "port": 35023
           },
           {
               "_cls": "Acl",
               "_id": {
                   "$oid": "55410e3a5b33522f64f9ca20"
               },
               "cidr_mask": "0.0.0.0/1",
               "date_created": {
                   "$date": 1430326842000
               },
               "description": "Allow Any",
               "instance": "Test123",
               "login": "donovan@heydonovan.io",
               "metadata": {},
               "port": 35023
           }
       ]
   }

Create a new ACL for the given instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /instances/<instance_name>/acls/

Request:

.. code-block:: bash

   {
       "cidr_mask": "123.123.123.123",
       "description": "Tesla HQ"
   }

Response:

.. code-block:: bash

   {
       "data": "55df9d97cb143c40ddc8376f"
   }

Get a specific ACL
~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /instances/<instance_name>/acls/<acl_id>/

Response:

.. code-block:: bash

   {
       "data": {
           "_cls": "Acl",
           "_id": {
               "$oid": "55df9d97cb143c40ddc8376f"
           },
           "cidr_mask": "123.123.123.123",
           "date_created": {
               "$date": 1440718231344
           },
           "description": "Tesla HQ",
           "instance": "Test123",
           "instance_id": {
               "$oid": "55410c7f5b335278490a5be8"
           },
           "instance_type": "mongodb_sharded",
           "login": "donovan@heydonovan.io",
           "metadata": {},
           "port": 35023,
           "service_type": "mongodb"
       }
   }

Delete an ACL
~~~~~~~~~~~~~~

.. code-block:: bash

   DELETE /instances/<instance_name>/acls/<acl_id>/

Response:

.. code-block:: bash

   {
       "data": {}
   }
