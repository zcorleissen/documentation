REST API Examples
=================

Elasticsearch provides a `complete reference <https://www.elastic.co/guide/en/elasticsearch/guide/current/_talking_to_elasticsearch.html#_restful_api_with_json_over_http>`_ to its RESTful API.

Create and View an Index
------------------------

Create an index:

.. code-block:: bash

  curl -u user:password -XPUT 'http://iad1-10140-0.es.objectrocket.com:10140/customer?pretty'

View all indexes:

.. code-block:: bash

  curl -u user:password -XGET 'http://iad1-10140-0.es.objectrocket.com:10140/_cat/indices?v'

Index and Query a Document
--------------------------

Index a sample document into a customer index:

.. code-block:: bash

  curl -u user:password -XPUT 'http://iad1-10140-0.es.objectrocket.com:10140/customer/external/1?pretty' -d '
    {
        "name": "John Doe"
    }'

Query a document from an index:

.. code-block:: bash

  curl -u user:password -XGET 'http://iad1-10140-0.es.objectrocket.com:10140/customer/external/1?pretty'

Update a Document
-----------------

Add an "age" field to the user "John Doe":

.. code-block:: bash

  curl -u user:password  -XPOST 'http://iad1-10140-0.es.objectrocket.com:10140/customer/external/1/_update?pretty' -d '
    {
      "doc": { "name": "John Doe", "age": 20 }
    }'

Delete a Document or Index
--------------------------

Delete a document:

.. code-block:: bash

  curl -u user:password -XDELETE 'http://iad1-10140-0.es.objectrocket.com:10140/customer/external/1?pretty'

Delete an index:

.. code-block:: bash

  curl -u user:password -XDELETE 'http://iad1-10140-0.es.objectrocket.com:10140/customer?pretty'
