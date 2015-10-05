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
