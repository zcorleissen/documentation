Elasticsearch Overview
=======================

What is Elasticsearch?
----------------------

Elastic.co defines Elasticsearch as a distributed, open source search and analytics engine, designed for horizontal scalability, reliability, and easy management. It combines the speed of search with the power of analytics via a sophisticated, developer-friendly query language covering structured, unstructured, and time-series data.

What does ObjectRocket Elasticsearch provide?
---------------------------------------------

Starting with many NoSQL data stores like Elasticsearch is easy, but daily administration, monitoring, backups, and scaling can add a heavy and challenging workload to already overtaxed teams. We take the operational burden off of your team with our purpose built platform and 24/7/365 Fanatical Support so you can focus on using Elasticsearch and not keeping it up and running.

ObjectRocket Elasticsearch instances are configured with the standard Elasticsearch default settings of ``number_of_shards = 5`` and ``number_of_replicas = 1``, which means any newly created index will have 5 primary shards, each with 1 replica shard (for a total of 10 shards for any new index). The number of primary shards can be specified per index when the index is created, as described in the `Create Index API <https://www.elastic.co/guide/en/elasticsearch/reference/current/indices-create-index.html>`_.
