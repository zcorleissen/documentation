Instance Resources
==================

Get details on an account's instances.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /instances/

Request/Response:

.. code-block:: bash

   $ http

Create a new instance.
~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /instances/

Request/Response:

.. code-block:: bash

   $ http

Get details on the specified instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /instances/<instance_name>/

Request/Response:

.. code-block:: bash

   $ http

Delete the specified instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   DELETE /instances/<instance_name>/

Request/Response:

.. code-block:: bash

   $ http

Rename the specified instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /instances/<instance_name>/rename/

Request/Response:

.. code-block:: bash

   $ http

Get a list of ACLs for the given instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /instances/<instance_name>/acls/

Request/Response:

.. code-block:: bash

   $ http

Create a new ACL for the given instance.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   POST /instances/<instance_name>/acls/

Request/Response:

.. code-block:: bash

   $ http

Get a specific ACL.
~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   GET /instances/<instance_name>/acls/<acl_id>/

Request/Response:

.. code-block:: bash

   $ http

Delete an ACL.
~~~~~~~~~~~~~~

.. code-block:: bash

   DELETE /instances/<instance_name>/acls/<acl_id>/

Request/Response:

.. code-block:: bash

   $ http

