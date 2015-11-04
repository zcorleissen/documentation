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

Yes, we currently offer admin, read only and Kibana only user roles through the Control Panel.

Is there a free trial?
~~~~~~~~~~~~~~~~~~~~~~

Yes! Choosing the 256MB RAM / 2GB Disk instance will be free for the first 30 days.

What other sizes are available?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Check out our `plans and pricing <http://www.objectrocket.com/pricing>`_, and click on **Elasticsearch**!

What versions are supported?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We currently default to **1.7.3** and offer **2.0.0** via our Early Access program, but please contact `support@objectrocket.com <mailto:support@objectrocket.com>`_ if you need something different!

What kind of architecture is this using?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When you build an ObjectRocket Elasticsearch instance, you get a cluster with a total of 11 nodes. We automatically configure 4 front-end client nodes, 2 Kibana nodes, 3 master nodes, and 2 data nodes. All nodes are containerized, which provides guaranteed resources (memory, CPU, disk I/O), prevents “noisy-neighbor” problems, and eliminates the performance bottlenecks of traditional hardware virtualization.

How much does ObjectRocket Elasticsearch cost per month?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The monthly cost of our ObjectRocket Elasticsearch instances are based on the plan size of the data nodes and the number of data nodes in the cluster.  Client, Kibana, and master nodes are included at no additional charge.

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
