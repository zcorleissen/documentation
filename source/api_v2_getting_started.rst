Overview
========

Getting Started
~~~~~~~~~~~~~~~

All data is sent and received as JSON. API access is accessed from the following domain:

.. code-block:: bash

   https://sjc-api.objectrocket.com/v2/

Authentication
~~~~~~~~~~~~~~

Authentication to the API occurs via `HTTP Basic Auth <https://en.wikipedia.org/wiki/Basic_access_authentication>`_. You'll need to authenticate with the API before you can do anything else (this would be the same username and password used when logging into the ObjectRocket Customer Portal).

If you linked your Rackspace cloud account with your ObjectRocket account, you will need to setup a password before you can use the API. Login, and click "Account Settings" at the top-right. Under the "Login Details" section, there will be a link to create a password for the account.

The server will respond with a **token** and **uid**. The token will expire after 24 hours. Here is an example on how to do so using cURL and `HTTPie <https://github.com/jkbrzt/httpie>`_:

.. code-block:: bash

   $ curl 'https://sjc-api.objectrocket.com/v2/tokens/' --user 'donovan@heydonovan.io'
   Enter host password for user 'donovan@heydonovan.io':
   {"data": {"token": "xLQiuUySDpyDjgGlaBiLbQmrdPYlKJETEIHLisZVxXcFDCsXKNQdohbsdErLsTKBWAmdYCgLKDjhNxYfE", "login": "donovan@heydonovan.io", "uid": "553fe69f5b335278436fa19b"}}

.. code-block:: bash

   $ http 'https://sjc-api.objectrocket.com/v2/tokens/' --auth 'donovan@heydonovan.io'
   http: password for donovan@heydonovan.io@sjc-api.objectrocket.com:
   HTTP/1.1 200 OK
   Connection: keep-alive
   Content-Length: 173
   Content-Type: application/json
   Date: Wed, 02 Dec 2015 19:10:37 GMT
   Server: nginx/1.8.0
   X-RateLimit-Limit: 1
   X-RateLimit-Remaining: 1
   X-RateLimit-Reset: -1
   X-Request-Id: 5b6d548382ff4494978120c72397a4f4
   
   {
       "data": {
           "login": "donovan@heydonovan.io",
           "token": "xLQiuUySDpyDjgGlaBiLbQmrdPYlKJETEIHLisZVxXcFDCsXKNQdohbsdErLsTKBWAmdYCgLKDjhNxYfE",
           "uid": "553fe69f5b335278436fa19b"
       }
   }

One important note. The **token** is what will be used for the **X-Auth-Token** value that's required for every API request. If you do not include this header, you will receive a **401 UNAUTHORIZED** error.

.. code-block:: bash

   $ curl 'https://sjc-api.objectrocket.com/v2/instances/' --header 'X-Auth-Token: xLQiuUySDpyDjgGlaBiLbQmrdPYlKJETEIHLisZVxXcFDCsXKNQdohbsdErLsTKBWAmdYCgLKDjhNxYfE'
   {"data": [{"service": "mongodb", "connect_string": "syd-mongos0.objectrocket.com:35023", "name": "MongoDB123", "zone": "AP-Sydney", "created": "2015-04-29 09:53:18", "ssl_connect_string": "syd-mongos0.objectrocket.com:45023", "encrypted": false, "storage_engine": "mmapv1", "ssl_service_net_connect_string": "syd-sn-mongos0.objectrocket.com:45023", "service_net_connect_string": "syd-sn-mongos0.objectrocket.com:35023", "compressor": "none", "version": "2.4.6", "plan": 5, "caster": null, "api_key": "88397705831449996672175456043915", "type": "mongodb_sharded", "id": "55410c7f5b335278490a5be8"}]}

.. code-block:: bash

   $ http 'https://sjc-api.objectrocket.com/v2/instances/' 'X-Auth-Token: xLQiuUySDpyDjgGlaBiLbQmrdPYlKJETEIHLisZVxXcFDCsXKNQdohbsdErLsTKBWAmdYCgLKDjhNxYfE'
   HTTP/1.1 200 OK
   Connection: keep-alive
   Content-Encoding: gzip
   Content-Type: application/json
   Date: Wed, 02 Dec 2015 19:14:05 GMT
   Server: nginx/1.8.0
   Transfer-Encoding: chunked
   Vary: Accept-Encoding
   X-RateLimit-Limit: 100
   X-RateLimit-Remaining: 99
   X-RateLimit-Reset: 1449083646
   X-Request-Id: a07dbb8ac2aa4dee91f1825e69ab6a5d
   
   {
       "data": [
           {
               "api_key": "88397705831449996672175456043915",
               "caster": null,
               "compressor": "none",
               "connect_string": "syd-mongos0.objectrocket.com:35023",
               "created": "2015-04-29 09:53:18",
               "encrypted": false,
               "id": "55410c7f5b335278490a5be8",
               "name": "MongoDB123",
               "plan": 5,
               "service": "mongodb",
               "service_net_connect_string": "syd-sn-mongos0.objectrocket.com:35023",
               "ssl_connect_string": "syd-mongos0.objectrocket.com:45023",
               "ssl_service_net_connect_string": "syd-sn-mongos0.objectrocket.com:45023",
               "storage_engine": "mmapv1",
               "type": "mongodb_sharded",
               "version": "2.4.6",
               "zone": "AP-Sydney"
           }
       ]
   }

Rate Limiting
~~~~~~~~~~~~~

You can make up to 100 requests per second. You can check the HTTP response headers of any API request to see your current rate limit status:

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

