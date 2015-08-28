Overview
========

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

You can make up to 100 requests per minute. You can check the HTTP response headers of any API request to see your current rate limit status:

.. code-block:: bash

   HTTP/1.1 200 OK
   Connection: keep-alive
   Content-Length: 12
   Content-Type: application/json
   Date: Thu, 27 Aug 2015 23:57:22 GMT
   Server: nginx/1.8.0
   X-RateLimit-Limit: 100
   X-RateLimit-Remaining: 99
   X-RateLimit-Reset: 1440719843
   X-Request-Id: 19dd4f836e424d20b6d4dd05a868c5ac

