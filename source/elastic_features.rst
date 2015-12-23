Features
========

Kibana
------

ObjectRocket includes a `Kibana <https://www.elastic.co/products/kibana/>`_ instance automatically configured to connect to your Elasticsearch cluster. Kibana builds rich visualizations of your Elasticseach data with charts and graphs.

Under Instances > Instance Details, the *Connect* heading displays URLs for Kibana connections in plain text and SSL.

.. note::
    Access to Kibana requires a Kibana-specific :ref:`access control list <elastic-access-control>` (ACL). 

ElasticHQ
---------

`ElasticHQ <http://www.elastichq.org/>`_ is a plugin that provides a web interface for monitoring, management, and querying your Elasticsearch cluster.  ElasticHQ is installed by default at ``/_plugin/HQ``.

Elasticsearch-head
------------------

`Elasticsearch-head <http://mobz.github.io/elasticsearch-head/>`_ is another popular plugin for managing and monitoring Elasticsearch clusters.  Elasticsearch-head is installed by default at ``/_plugin/head``.

AWS DirectConnect
-----------------

Amazon Web Services (AWS) users in ``us-east-1`` and ``eu-west-1`` locations automatically access dedicated 10Gbit `AWS Direct Connect <https://aws.amazon.com/directconnect/>`_ circuits for very high throughput, low latency connectivity to ObjectRocket Elasticsearch instances in our ``US-East-IAD1`` and ``EU-London-LON5``datacenters, respectively.

ServiceNet Access
-----------------

We offer ServiceNet connectivity within our ``US-East-IAD1``, ``US-Dallas``, and ``EU-London-LON5`` Rackspace data centers.

ACLSync
--------

ObjectRocket can automatically retrieve and create ACLs for groups of IP addresses from your Rackspace Cloud or AWS environment. This feature is currently limited to retrieving IP addresses from a single AWS region.

Daily Backups
-------------

We automatically back up your data every 24 hours using Elasticsearch snapshots. Contact support@objectrocket.com to request a restore.
