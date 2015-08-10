Elasticsearch Resources
=======================

Check state of instances provided
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /elasticsearch/check_states/

Request/Response:

.. code-block:: bash

   $ http

Get details on the specified Elasticsearch instance's cluster.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/<instance_name>/cluster/

Request/Response:

.. code-block:: bash

   $ http

Get details on the specified Elasticsearch instance's data nodes.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/<instance_name>/data_nodes/

Request/Response:

.. code-block:: bash

   $ http

Add a new data node to the specified Elasticsearch instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /elasticsearch/<instance_name>/data_nodes/

Request/Response:

.. code-block:: bash

   $ http

Get details on the specified Elasticsearch instance's indices.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/<instance_name>/indices/

Request/Response:

.. code-block:: bash

   $ http

Get details on the specified Elasticsearch instance's nodes.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/<instance_name>/nodes/

Request/Response:

.. code-block:: bash

   $ http

Get details on an account's Elasticsearch instances.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/

Request/Response:

.. code-block:: bash

   $ http

Get a list of all users currenlty added to the instance specified by name.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /elasticsearch/<instance_name>/users/

Request/Response:

.. code-block:: bash

   $ http

Create or update a user for the instance specified by name.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /elasticsearch/<instance_name>/users/

Request/Response:

.. code-block:: bash

   $ http

Delete a user from the instance specified by name.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   DELETE /elasticsearch/<instance_name>/users/

Request/Response:

.. code-block:: bash

   $ http

