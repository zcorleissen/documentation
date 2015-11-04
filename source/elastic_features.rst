Features
========

Kibana
------
We include an instance of `Kibana <https://www.elastic.co/products/kibana/>`_ automatically configured to connect to your Elasticsearch cluster.  Kibana allows you to build rich visualizations of your Elasticseach data using charts and graphs.

You can view the plain text and SSL URL addresses for Kibana under the **Connect** heading of the Control Panel.  Before you can access Kibana you will need to add Kibana-specific ACLs under the **Security** heading.

ElasticHQ
---------
`ElasticHQ <http://www.elastichq.org/>`_ is a plugin that provides a web interface for monitoring, management, and querying your Elasticsearch cluster.  ElasticHQ is installed by default at ``/_plugin/HQ``.

Elasticsearch-head
------------------
`Elasticsearch-head <http://mobz.github.io/elasticsearch-head/>`_ is another popular plugin for managing and monitoring Elasticsearch clusters.  Elasticsearch-head is also installed by default and is located at ``/_plugin/head``.

AWS DirectConnect
-----------------
AWS users in us-east-1 and eu-west-1 will automatically use dedicated 10Gbit AWS DirectConnect circuits for very high throughput, low latency connectivity to ObjectRocket Elasticsearch instances in our US-East-IAD1 and EU-London-LON5 datacenters, respectively.

ServiceNet Access
-----------------
We offer ServiceNet connectivity within Rackspace datacenters, which correspond to US-East-IAD1, US-Dallas, and EU-London-LON5.

ACLSync
--------
The ObjectRocket platform can automatically retrieve IP addresses from your Rackspace Cloud or AWS environment, and create an ACL for each of those. This feature is currently limited to retrieving IP addresses from a single AWS region.

Daily Backups
-------------
We automatically backup your data every 24 hours using Elasticsearch snapshots. Contact support@objectrocket.com to request a restore.
