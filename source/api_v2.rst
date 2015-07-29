API Overview (v2)
=====================

This document covers version 2.0 of the ObjectRocket API.

Getting Started
---------------

v2 API Endpoint: `https://sjc-api.objectrocket.com/v2/`

Authentication
--------------

Authentication to the API occurs via `HTTP Basic Auth <https://en.wikipedia.org/wiki/Basic_access_authentication>`_. You'll need to authenticate with the API before you can do anything else (this would be the same username and password used when logging into the ObjectRocket Customer Portal). The server will respond with a **token** and **uid**. The token will expire after 24 hours. Here is an example on how to do so using cURL and HTTPie:

.. code-block:: bash

   $ curl --user 'donovan@heydonovan.io' 'https://sjc-api.objectrocket.com/v2/tokens/'
   Enter host password for user 'donovan@heydonovan.io':
   {"data": {"token": "IjA3MmQ5NGMwODUzOTRiMTE4ZWU0MzM2MGJlOTRiMzNhIg.CFoJ0A.4NWcNoAf-j3sEfTZzgKWtN1vdrg", "login": "donovan@heydonovan.io", "uid": "553fe69f5b335278436fa19b"}}

.. code-block:: bash

   $ http --auth 'donovan@heydonovan.io' 'https://sjc-api.objectrocket.com/v2/tokens/'
   http: password for donovan@heydonovan.io@sjc-api.objectrocket.com:
   HTTP/1.1 200 OK
   Connection: keep-alive
   Content-Length: 173
   Content-Type: application/json
   Date: Wed, 10 Jun 2015 15:25:01 GMT
   Server: nginx/1.6.0
   X-RateLimit-Limit: 1
   X-RateLimit-Remaining: 1
   X-RateLimit-Reset: -1

   {
       "data": {
           "login": "donovan@heydonovan.io",
           "token": "IjU2OTExN2VkYTY3ODQ5Y2JhNThkNTZlOWY2NmE4OTQ4Ig.CFnoTQ.mllZEOLgf7wLZIpcMzDVgMnSmpo",
           "uid": "553fe69f5b335278436fa19b"
       }
   }

One important note. The **token** is what will be used for the **X-Auth-Token** value that's required for every API request. If you do not include this header, you will receive a **401 UNAUTHORIZED** error.

.. code-block:: bash

    $ http --auth 'donovan@heydonovan.io' 'https://sjc-api.objectrocket.com/v2/instances/' \
      X-Auth-Token:Ijg2NjM3M2RlYzI4YzQ5YzlhODJjZmZhY2UwZGRkYzlkIg.CJQ-xQ.BEOGqqZuwAkp-dbnKv67rqfbQkY
    http: password for donovan@heydonovan.io@sjc-api.objectrocket.com:
    HTTP/1.1 200 OK
    Connection: keep-alive
    Content-Length: 1013
    Content-Type: application/json
    Date: Fri, 24 Jul 2015 21:26:35 GMT
    Server: nginx/1.8.0
    X-RateLimit-Limit: 100
    X-RateLimit-Remaining: 99
    X-RateLimit-Reset: 1437773196

    {
        "data": [
            {
                "api_key": "12345",
                "caster": null,
                "connect_string": "syd-mongos0.objectrocket.com:12345",
                "created": "2015-04-29 09:53:18",
                "id": "55410c7f5b335278490a5be8",
                "name": "test123",
                "plan": 5,
                "service": "mongodb",
                "ssl_connect_string": "syd-mongos0.objectrocket.com:45023",
                "type": "mongodb_sharded",
                "version": "2.4.6",
                "zone": "AP-Sydney"
            }
        ]
    }

Quick Reference
---------------

This is the full list of all the routes our API offers (grouped by product name). Clicking on a heading will take you to a more detailed page which describes each route in more detail.

:doc:`api_v2_general_resources`

* /accounts/<uid>/
* /casters/
* /casters/<caster_id>/
* /contact/
* /dashboards/
* /dashboards/<dashboard_id>/
* /graphs/ad_hoc
* /instances/<instance_name>/stats_config/
* /plans/
* /plans/<string:planid>/
* /tokens/

:doc:`api_v2_instance_resources`

* /instances/
* /instances/<instance_name>/
* /instances/<instance_name>/acls/
* /instances/<instance_name>/acls/<acl_id>/
* /instances/<instance_name>/rename/

:doc:`api_v2_elasticsearch_resources`

* /elasticsearch/
* /elasticsearch/<instance_name>/cluster/
* /elasticsearch/<instance_name>/data_nodes/
* /elasticsearch/<instance_name>/indices/
* /elasticsearch/<instance_name>/nodes/
* /elasticsearch/<instance_name>/users/
* /elasticsearch/check_states/

:doc:`api_v2_redis_resources`

* /redis/<instance_name>/connectedSlaves/
* /redis/<instance_name>/maxClients/
* /redis/<instance_name>/maxMemoryPolicy/
* /redis/<instance_name>/resize/
* /redis/<instance_name>/spaceUsage/

:doc:`api_v2_mongodb_resources`

* /mongodb/<instance_name>/backups/
* /mongodb/<instance_name>/compaction/
* /mongodb/<instance_name>/databases/
* /mongodb/<instance_name>/databases/<database_name>/
* /mongodb/<instance_name>/databases/<database_name>/collections/
* /mongodb/<instance_name>/databases/<database_name>/collections/<collection_name>/
* /mongodb/<instance_name>/logs/
* /mongodb/<instance_name>/opcounters/
* /mongodb/<instance_name>/opcounters/persecond/
* /mongodb/<instance_name>/replicasets/
* /mongodb/<instance_name>/shards/
* /mongodb/<instance_name>/spaceusage/
* /mongodb/<instance_name>/stepdown/

