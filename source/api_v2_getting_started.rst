..
   -- Random Thoughts
   All method descriptions should fit on one line
   If it's a GET request, prefix the desc with Get

ObjectRocket API (v2)
=====================

Overview
--------

Getting Started
~~~~~~~~~~~~~~~

All data is sent and received as JSON. API access is accessed from the following domain:

.. code-block:: bash

   https://sjc-api.objectrocket.com/v2/

Authentication
~~~~~~~~~~~~~~

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

Rate Limiting
~~~~~~~~~~~~~

TODO

General Resources
-----------------

List all accounts
~~~~~~~~~~~~~~~~~

Caster Resources
----------------

Get all casters
~~~~~~~~~~~~~~~
Get caster details
~~~~~~~~~~~~~~~~~~

Stat Resources
--------------

Instance Resources
------------------

Get all instances
~~~~~~~~~~~~~~~~~
Get instance details
~~~~~~~~~~~~~~~~~~~~
Get ACL's
~~~~~~~~~
Get ACL details
~~~~~~~~~~~~~~~
Rename an instance
~~~~~~~~~~~~~~~~~~


Elasticsearch Resources
-----------------------

Get all instances
~~~~~~~~~~~~~~~~~
Get cluster details
~~~~~~~~~~~~~~~~~~~
Get data node details
~~~~~~~~~~~~~~~~~~~~~
Add a new data node
~~~~~~~~~~~~~~~~~~~
Get indices
~~~~~~~~~~~
Get instance node details
~~~~~~~~~~~~~~~~~~~~~~~~~
Get all users
~~~~~~~~~~~~~
Update a user
~~~~~~~~~~~~~
Delete a user
~~~~~~~~~~~~~
Check state
~~~~~~~~~~~

Redis Resources
---------------

Get 'connected_slaves' info
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/connectedSlaves/

Request/Response:

.. code-block:: bash

   $ http

Get 'maxclients' config
~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/maxClients/

Request/Response:

.. code-block:: bash

   $ http

Get 'maxmemory-policy' config
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/maxMemoryPolicy/

Request/Response:

.. code-block:: bash

   $ http

Change size of instance
~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /redis/<instance_name>/resize/

*Parameters*:

======== ======= ==============================================
Name     Type    Description
======== ======= ==============================================
new_plan integer The size of the redis instance to provision to.
======== ======= ==============================================

*Request/Response:*

.. code-block:: bash

   $ http

Get space usage details
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/spaceUsage/

Request/Response:

.. code-block:: bash

   $ http

MongoDB Resources
-----------------

Get backups
~~~~~~~~~~~
Get compaction state
~~~~~~~~~~~~~~~~~~~~
Get databases
~~~~~~~~~~~~~
Get database details
~~~~~~~~~~~~~~~~~~~~
Get collections
~~~~~~~~~~~~~~~
Get collection details
~~~~~~~~~~~~~~~~~~~~~~
Get logs
~~~~~~~~
Get opcounters
~~~~~~~~~~~~~~
Get opcounters per second
~~~~~~~~~~~~~~~~~~~~~~~~~
Get replica sets
~~~~~~~~~~~~~~~~
Get shards
~~~~~~~~~~
Get space usage statistics
~~~~~~~~~~~~~~~~~~~~~~~~~~
Get stepdown window
~~~~~~~~~~~~~~~~~~~

