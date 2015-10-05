Getting Started with Redis
==========================

1. Create an instance
2. Add an ACL
3. Connect!

1. Create an instance
~~~~~~~~~~~~~~~~~~~~~

- Click the 'Add Instance' button.

.. image:: images/addinstance.png
   :align: center

- Select a name for your instance. This can be almost anything, as any alpha numeric string is valid.

- Select a Service, Redis in this case.

- There is only one type of Redis offered at the moment, defaulting to HA Redis.

.. image:: images/createredis.png
   :align: center

- Select a version to deploy. We offer 2.8.22 and 3.0.4 as a beta.

- Select a zone that suits your needs. Zones are either Rackspace or AWS Direct Connect zones, labeled by airport codes in that region. Check out the `zone map <http://objectrocket.com/features>`_ for more details.

- Select a plan that suits your needs. For more details, check out `plans and pricing <http://www.objectrocket.com/pricing>`_.

.. image:: images/createredis.png
   :align: center

3. Add an ACL
~~~~~~~~~~~~~

Under the heading `Security`, you have the option to `Add ACL`. This is necessary as we don't allow any access by default so you need to add any appropriate ACL's for your servers connecting to ObjectRocket. There are two fields: `IP Address` and `Description`. Only IP is mandatory, but a description can certainly help if you plan to have more than a few.

.. image:: images/addacl_mongo.png
   :align: center

3. Connect!
~~~~~~~~~~~

Provided you've added an ACL, you can test basic connectivity from your terminal of choice with redis-cli:

.. code-block:: bash

   $ redis-cli -h '<hostname>' -p '<port>' -a '<password>'
   hostname:port> set my_key my_value
   OK
   hostname:port> get my_key
   "my_value"

Or you can use netcat/telnet as well:

.. code-block:: bash

   $ nc '<hostname>' '<port>'
   auth <password>
   +OK
   set my_key my_value
   +OK
   get my_key
   $8
   my_value

If you see something similar to the example above, you're good to use the instance as you normally would any other redis implementation! If you run into any issues or just want some guidance please don't hesitate to reach out to us at `support@objectrocket.com <mailto:support@objectrocket.com>`_!
