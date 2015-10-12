REST Examples
======================

Creating and Viewing an Index
------------------------------
Creating the index:

.. code-block:: bash

  curl -u user:password -XPUT 'http://iad1-10140-0.es.objectrocket.com:10140/customer?pretty'

View all indexes:

.. code-block:: bash

  curl -u user:password -XGET 'http://iad1-10140-0.es.objectrocket.com:10140/_cat/indices?v'

Index and Query a Document
---------------------------
Index sample document into customer index:

.. code-block:: bash

  curl -u user:password -XPUT 'http://iad1-10140-0.es.objectrocket.com:10140/customer/external/1?pretty' -d '
    {
        "name": "John Doe"
    }'
Query document from index:

.. code-block:: bash

  curl -u user:password -XGET 'http://iad1-10140-0.es.objectrocket.com:10140/customer/external/1?pretty'

Update Document
---------------
Adding the age field to the user John Doe:

.. code-block:: bash

  curl -u user:password  -XPOST 'http://iad1-10140-0.es.objectrocket.com:10140/customer/external/1/_update?pretty' -d '
    {
      "doc": { "name": "John Doe", "age": 20 }
    }'

Delete Document or Index
-----------------------------
Removing a document:

.. code-block:: bash

  curl -u user:password -XDELETE 'http://iad1-10140-0.es.objectrocket.com:10140/customer/external/1?pretty'

Removing an index:

.. code-block:: bash

  curl -u user:password -XDELETE 'http://iad1-10140-0.es.objectrocket.com:10140/customer?pretty'
