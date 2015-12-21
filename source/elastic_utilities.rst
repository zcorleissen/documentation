Elasticsearch Utilities
========================

elasticstat
-----------

`Elasticstat <https://github.com/objectrocket/elasticstat>`_ monitors real-time performance of an Elasticsearch cluster from the command line, similar to the Unix utilities `iostat <http://linux.die.net/man/1/iostat>`_ or `vmstat <http://linux.die.net/man/8/vmstat>`_. For more information about Elasticsearch performance metrics, check out `Cluster Health <https://www.elastic.co/guide/en/elasticsearch/guide/current/_cluster_health.html>`_ and `Monitoring Individual Nodes <https://www.elastic.co/guide/en/elasticsearch/guide/current/_monitoring_individual_nodes.html>`_ from the Elasticsearch Definitive Guide.

.. note::
    Make sure to set up :ref:`access control lists <elastic-acl>` in order to connect to your instance.

    You can control the frequency of ``elasticstat`` updates with the ``delayinterval`` optional parameter, which specifies a delay in seconds between updates.

Here's what basic, non-SSL usage looks like:

.. code-block:: bash

  $ elasticstat -h http://iad1-10140-0.es.objectrocket.com:10140,http://iad1-10140-1.es.objectrocket.com:10140,http://iad1-10140-2.es.objectrocket.com:10140,http://iad1-10140-3.es.objectrocket.com:10140 -u estest -p

To use SSL, add the ``--ssl`` flag to the command and enter valid SSL connection strings (HTTPS, port 20140):

.. code-block:: bash

  $ elasticstat --ssl -h https://iad1-10140-0.es.objectrocket.com:20140,https://iad1-10140-1.es.objectrocket.com:20140,https://iad1-10140-2.es.objectrocket.com:20140,https://iad1-10140-3.es.objectrocket.com:20140 -u estest -p
