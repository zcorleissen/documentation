MongoDB Resources
=================

Get a list of collection names belonging to the given instance database.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/databases/<database_name>/collections/

Request/Response:

.. code-block:: bash

   $ http

Create a new collection in the specified instance database.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /mongodb/<instance_name>/databases/<database_name>/collections/

Request/Response:

.. code-block:: bash

   $ http

Get details on a collection belonging to the given instance database.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/databases/<database_name>/collections/<collection_name>/

Request/Response:

.. code-block:: bash

   $ http

Get the compaction state of the specified instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/compaction/

Request/Response:

.. code-block:: bash

   $ http

Schedule the specified instance for compaction.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /mongodb/<instance_name>/compaction/

Request/Response:

.. code-block:: bash

   $ http

Get a list of databases and their statistics belonging to the given
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/databases/

Request/Response:

.. code-block:: bash

   $ http

Create a database and user on the specified instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /mongodb/<instance_name>/databases/

Request/Response:

.. code-block:: bash

   $ http

Get details on a database belonging to the given instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/databases/<database_name>/

Request/Response:

.. code-block:: bash

   $ http

Delete a database from the specified instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   DELETE /mongodb/<instance_name>/databases/<database_name>/

Request/Response:

.. code-block:: bash

   $ http

Get opcounters per second for the given instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/opcounters/persecond/

Request/Response:

.. code-block:: bash

   $ http

Get opcounters for the given instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/opcounters/

Request/Response:

.. code-block:: bash

   $ http

Get a list of replica sets belonging to the given instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/replicasets/

Request/Response:

.. code-block:: bash

   $ http

Get a list of shards belonging to the given instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/shards/

Request/Response:

.. code-block:: bash

   $ http

Add a shard to the given instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /mongodb/<instance_name>/shards/

Request/Response:

.. code-block:: bash

   $ http

Get space usage statistics from the specified instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/spaceusage/

Request/Response:

.. code-block:: bash

   $ http

Get the current stepdown window configuration of the specified instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/stepdown/

Request/Response:

.. code-block:: bash

   $ http

Update the stepdown window configuration of the specified instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /mongodb/<instance_name>/stepdown/

Request/Response:

.. code-block:: bash

   $ http

Get details on backups
~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/backups/

Request/Response:

.. code-block:: bash

   $ http

Get log details
~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /mongodb/<instance_name>/logs/

Request/Response:

.. code-block:: bash

   $ http

