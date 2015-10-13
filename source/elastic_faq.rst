ObjectRocket Elasticsearch FAQ
--------------------------------

How do I connect?
~~~~~~~~~~~~~~~~~

You can connect via Elasticsearch's RESTful API over HTTP/HTTPS or the transport client library for Java API access.

Is SSL supported?
~~~~~~~~~~~~~~~~~

Yes! By using the SSL connection string provided, we handle everything you need for SSL access using standard https:// links.

Can I setup multiple user types?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, we currently offer Admin, with full control, and read only users setup through the Control Panel.

Is there a free trial?
~~~~~~~~~~~~~~~~~~~~~~

Yes! Choosing the 256MB RAM / 2GB Disk instance will be free for the first 30 days.

What other sizes are available?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Check out our `plans and pricing <http://www.objectrocket.com/pricing>`_, and click the Elasticsearch tab!

What versions are supported?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We currently default to **1.7.0**, but please contact `support@objectrocket.com <mailto:support@objectrocket.com>`_ if you need something different!

What kind of architecture is this using?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When you build an ObjectRocket Elasticsearch instance, you get a cluster with a total of 9 nodes. We automatically configure 4 front-end client nodes, 3 master nodes, and 2 data nodes. This robust setup is ready to handle the load and scale of your most mission critical workloads.

What plugins are available by default?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We install both `ElasticHQ <http://www.elastichq.org/>`_ and `elasticsearch-head <http://mobz.github.io/elasticsearch-head/>`_ by default in their default locations (``/_plugin/HQ and /_plugin/head``).

We can support other 3rd party plugins on a case by case basis.  Contact `support@objectrocket.com <mailto:support@objectrocket.com>`_ if you would like different plugins installed or if you would like us to disable them all.

What about backups?
~~~~~~~~~~~~~~~~~~~

We automatically backup your data every 24 hours using Elasticsearch snapshots.  Contact `support@objectrocket.com <mailto:support@objectrocket.com>`_ to request a restore.

Can I increase or decrease the ``number_of_shards`` or ``number_of_replicas`` on my instance?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you would like to change these defaults for your ObjectRocket Elasticsearch instance, please reach out to us at `support@objectrocket.com <mailto:support@objectrocket.com>`_.
