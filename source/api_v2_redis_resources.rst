Redis Resources
===============

Get details on the specified Redis instance's connected slaves.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/connectedSlaves/

Response:

.. code-block:: bash

   {
       "data": 1
   }

Get details on the specified Redis instance's space usage.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/spaceUsage/

Response:

.. code-block:: bash

   {
       "data": {
           "freeSpacePercentage": 0.0656610107421875,
           "usedMemoryHuman": "1.64M"
       }
   }

Get details on the specified Redis instance's max memory policy.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/maxMemoryPolicy/

Response:

.. code-block:: bash

   {
       "data": "volatile-lru"
   }

Get details on the specified Redis instance's max clients.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /redis/<instance_name>/maxClients/

Response:

.. code-block:: bash

   {
       "data": "4064"
   }

Resize a redis instance to the specified size.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /redis/<instance_name>/resize/

Request:

.. code-block:: bash

   {
       "new_plan": 2500
   }

Response:

.. code-block:: bash

   {
       "data": "Started process of resizing instance Test123 from 1000 to 2500"
   }

