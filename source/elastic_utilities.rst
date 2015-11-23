Elasticsearch Utilities
========================

elasticstat
-----------

Elasticstat is a utility for real-time performance monitoring of an Elasticsearch cluster from the command line, much like how the Unix utilities iostat or vmstat work. The frequency of updates can be controled via the DELAYINTERVAL optional parameter, which specifies a delay in seconds after each update.

Performance metrics shown are based on the articles `Cluster Health <https://www.elastic.co/guide/en/elasticsearch/guide/current/_cluster_health.html>`_ and `Monitoring Individual Nodes <https://www.elastic.co/guide/en/elasticsearch/guide/current/_monitoring_individual_nodes.html>`_ from the Elasticsearch Definitive Guide. Please refer to these articles for further insight as to the significance of each metric.

Find more information about setting up elasticstat: https://github.com/objectrocket/elasticstat

.. note::
  NOTE! Ensure you have the correct ACL's in place or you will not be able to connect to your instance.

Here's what the basic (non-ssl) usage looks like using the connect string ``http://iad1-10140-0.es.objectrocket.com:10140``, ``http://iad1-10140-1.es.objectrocket.com:10140``, ``http://iad1-10140-2.es.objectrocket.com:10140``, ``http://iad1-10140-3.es.objectrocket.com:10140``, on port ``10140``, with the username ``estest``:

.. code-block:: bash

  $ elasticstat -h http://iad1-10140-0.es.objectrocket.com:10140,http://iad1-10140-1.es.objectrocket.com:10140,http://iad1-10140-2.es.objectrocket.com:10140,http://iad1-10140-3.es.objectrocket.com:10140 -u estest -p

If you would like to use ssl please add on the ``--ssl`` flag and use the proper ssl connect string:

.. code-block:: bash

  $ elasticstat --ssl -h https://iad1-10140-0.es.objectrocket.com:20140,https://iad1-10140-1.es.objectrocket.com:20140,https://iad1-10140-2.es.objectrocket.com:20140,https://iad1-10140-3.es.objectrocket.com:20140 -u estest -p
