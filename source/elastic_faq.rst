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

What are the default number of shards and replicas per index?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ObjectRocket Elasticsearch instances are configured with the standard Elasticsearch default settings of ``number_of_shards = 5`` and ``number_of_replicas = 1``, which means any newly created index will have 5 primary shards, each with 1 replica shard (for a total of 10 shards for any new index). The number of primary shards can be specified per index when the index is created, as described in the `Create Index API <https://www.elastic.co/guide/en/elasticsearch/reference/current/indices-create-index.html>`_. If you would like to change these defaults for your ObjectRocket Elasticsearch instance, please contact `support@objectrocket.com <mailto:support@objectrocket.com>`_.

How can I add a data node?
~~~~~~~~~~~~~~~~~~~~~~~~~~

A new instance comes with two data nodes and more can be easily added after the initial instance creation. To add more nodes go to the Elasticsearch instance in the Control Panel and simply click the **Data Nodes** heading, then the  **Add Data Node** button and follow the prompts. Additional charges apply, so take a look at our `pricing <http://objectrocket.com/pricing>`_ page for details.

.. image:: images/add_datanode.png
   :align: center
