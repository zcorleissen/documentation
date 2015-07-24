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

Quick Reference (Methods)
-------------------------

General resources

=======================  =========
URL                      HTTP Verb
=======================  =========
/plans/
/plans/<string:planid>/
/tokens/
/contact/
/accounts/<uid>/
/casters/
/casters/<caster_id>/
=======================  =========

Stats resources

========================================  =========
URL                                       HTTP VERB
========================================  =========
/graphs/ad_hoc
/instances/<instance_name>/stats_config/
/dashboards/
/dashboards/<dashboard_id>/
========================================  =========

Instance resources

=========================================  =========
URL                                        HTTP Verb
=========================================  =========
/instances/                                GET      
/instances/<instance>/                     GET      
/instances/<instance>/rename/              GET      
/instances/<instance>/acls/                GET      
/instances/<instance>/acls/<acl_id>/       GET      
=========================================  =========

Elasticsearch resources

==========================================  =========
URL                                         HTTP Verb
==========================================  =========
/elasticsearch/check_states/                POST     
/elasticsearch/<instance>/cluster/          GET      
/elasticsearch/<instance>/data_nodes/       GET      
/elasticsearch/<instance>/indices/          GET      
/elasticsearch/<instance>/nodes/            GET      
/elasticsearch/                             GET      
/elasticsearch/<instance>/users/            GET      
==========================================  =========

Redis resources

==================================================================  ===============
URL                                                                 HTTP Verb
==================================================================  ===============
/redis/<instance>/connectedSlaves/                                  GET     
/redis/<instance>/spaceUsage/                                       GET      
/redis/<instance>/maxMemoryPolicy/                                  GET      
/redis/<instance>/maxClients/                                       GET      
/redis/<instance>/resize/                                           POST    
==================================================================  ===============

MongoDB resources

+---------------------------------------------------------------------+
| Endpoint                                                            |
+=====================================================================+
| GET /mongodb/:instance/databases/:database/collections/             |
+---------------------------------------------------------------------+
| GET /mongodb/:instance/databases/:database/collections/:collection/ |
+---------------------------------------------------------------------+
| GET /mongodb/:instance/compaction/                                  |
+---------------------------------------------------------------------+
| GET /mongodb/:instance/databases/                                   |
+---------------------------------------------------------------------+
| GET /mongodb/:instance/databases/<database>/                        |
+---------------------------------------------------------------------+
| GET /mongodb/:instance/opcounters/persecond/                        |
+---------------------------------------------------------------------+
| GET /mongodb/:instance/opcounters/                                  |
+---------------------------------------------------------------------+
| GET /mongodb/:instance/replicasets/                                 |
+---------------------------------------------------------------------+
| GET /mongodb/:instance/shards/                                      |
+---------------------------------------------------------------------+
| GET /mongodb/:instance/spaceusage/                                  |
+---------------------------------------------------------------------+
| GET /mongodb/:instance/stepdown/                                    |
+---------------------------------------------------------------------+
| GET /mongodb/:instance/backups/                                     |
+---------------------------------------------------------------------+
| GET :ref:`mongodb-instance-logs`                                    |
+---------------------------------------------------------------------+

MongoDB
~~~~~~~

.. _mongodb-instance-logs:

/mongodb/:instance/logs/
-------------------------

Description: Lorem Ipsum

Example Request:

.. code-block:: bash

   $ http --auth 'user@example.com:password' 'https://sjc-api.objectrocket.com/v2/mongodb/test123/backups/'

Example Response:

.. code-block:: bash

   {
            "_id": {
                "$oid": "55b1e6f95559617dd0a517ec"
            },
            "backup_directory": "/backups/55410c7f5b335278490a5be8/20150724_0018",
            "backup_host": "sydbackups0.syd.objectrocket.com",
            "error_msg": "Successful, completed in 61 seconds",
            "filenames": {
                "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150724_0018.tgz",
                "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150724_0018.tgz",
                "config_server": "config_12345_20150724_0018.tgz"
            },
            "instance_id": {
                "$oid": "55410c7f5b335278490a5be8"
            },
            "instance_name": "test123",
            "instance_type": "mongodb_sharded",
            "login": "donovan@heydonovan.io",
            "port": 12345,
            "timestamp": {
                "$date": 1437697100909
            },
            "timestamp_formatted": "2015/07/24 00:18:20"
        }

Redis
~~~~~

more stuff

