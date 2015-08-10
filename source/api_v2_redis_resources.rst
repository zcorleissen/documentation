Redis Resources
================

Get details on the specified Redis instance's connected slaves.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/connectedSlaves/

Request/Response:

.. code-block:: bash

   $ http

Get details on the specified Redis instance's space usage.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/spaceUsage/

Request/Response:

.. code-block:: bash

   $ http

Get details on the specified Redis instance's max memory policy.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/maxMemoryPolicy/

Request/Response:

.. code-block:: bash

   $ http

Get details on the specified Redis instance's max clients.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/maxClients/

Request/Response:

.. code-block:: bash

   $ http

Resize a redis instance to the specified size.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /redis/<instance_name>/resize/

Request/Response:

.. code-block:: bash

   $ http

