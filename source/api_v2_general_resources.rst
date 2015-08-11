General Resources
=================

Get details on all plans.
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /plans/

Request/Response:

.. code-block:: bash

   $ http

Get details on the plan specified by ID.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /plans/<string:planid>/

Request/Response:

.. code-block:: bash

   $ http

Record the contact form data, and notify sales.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /contact/

Request/Response:

.. code-block:: bash

   $ http

Get details on an account.
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /accounts/<uid>/

Request/Response:

.. code-block:: bash

   $ http

Set the CC info for the authenticated account.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /accounts/<uid>/set_card/

Request/Response:

.. code-block:: bash

   $ http

Get details on all casters belonging to this account.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /casters/

Request/Response:

.. code-block:: bash

   $ http

Get details on a caster specified by ID.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /casters/<caster_id>/

Request/Response:

.. code-block:: bash

   $ http

Get the data for an ad-hoc query request.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /graphs/

Request/Response:

.. code-block:: bash

   $ http

Get both the replset infrastructure and the list of stats for a host.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /instances/<instance_name>/stats_config/

Request/Response:

.. code-block:: bash

   $ http

Get all dashboards for the specified account.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /dashboards/

Request/Response:

.. code-block:: bash

   $ http

Create a new dashboard.
~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /dashboards/

Request/Response:

.. code-block:: bash

   $ http

Get the dashboard specified by ID.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /dashboards/<dashboard_id>/

Request/Response:

.. code-block:: bash

   $ http

Update the dashboard specified by ID.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   PUT /dashboards/<dashboard_id>/

Request/Response:

.. code-block:: bash

   $ http

Delete the dashboard specified by ID.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   DELETE /dashboards/<dashboard_id>/

Request/Response:

.. code-block:: bash

   $ http

