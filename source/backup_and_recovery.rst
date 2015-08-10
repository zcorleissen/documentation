Backup and Recovery
===================

Overview
--------

Each instance is protected by replication. Should any component fail, the replica set architecture of MongoDB provides the primary level of high availability, fault tolerance, and uptime. However as a last resort and for overall data protection backups are taken daily here at ObjectRocket.

Backups
-------

.. note::

 Our default backup retention is two weeks. If you need this to be a larger window, please contact our `sales team <mailto:sales@objectrocket.com>`_.

Backups are taken once daily by default, but please talk to our `sales team <mailto:sales@objectrocket.com>`_ if you need a different schedule. Backups are taken per instance, and a list of backups can be seen by clicking the name of a MongoDB or Elasticsearch instance and then by clicking the **Backups** header.

Backups are taken using `mongodump` and are archived on the ObjectRocket system internally. Because ObjectRocket is built around sharding, backups are designed according to best practices to ensure backups are as consistent as possible among the members of an instance. Each instance is backed up with a high level of consistency, but not guaranteed consistency. They are not true point in time, and each shard is backed up individually.

Recovery Options
----------------

Download a backup
~~~~~~~~~~~~~~~~~

Each backup is available for download. Customers need to email our `support team <mailto:support@objectrocket.com>`_ and let us know which backup you need. A list of the backup images is available in the ObjectRocket control panel under **Backups** for each instance. We can upload backups to S3 or Cloud Files, but if you need something else we'll be happy to work something out.

In place restore
~~~~~~~~~~~~~~~~

An existing instance can be replaced/recovered with a backup image. All data in the existing instance will be replaced with the data of the backup image essentially ‘rolling back’ the entire instance. Customers need to email our `support team <mailto:support@objectrocket.com>`_ to request an in-place recovery.

Delayed Slaves
~~~~~~~~~~~~~~

Code release, mis-typing, or other human errors can be fixed by using using a time delayed replica set member. In case of a problem, the replica is manually stopped and opened in a read/only mode to manually piece back together the data. If you'd like to add a delayed slave to an instance, please email our `sales team <mailto:sales@objectrocket.com>`_. This feature has an additional cost, but does also provide direct access to this delayed slave via a virtual IP address for tools/scripts to have access specifically to the delayed slave. Recovery is a customer responsibility beyond the core components provided by ObjectRocket. This is due to the fact there is an inherent knowledge of the schema, application and customer data required.

Data Validation Options
-----------------------

Continuous Data Validation
~~~~~~~~~~~~~~~~~~~~~~~~~~

It may be desirable for the customer to be able to validate data from time to time. The general approach is to point a diff tool or other comparison tool created by the customer at a slave instance and compare it against some other known archive. This can be accomplished on the ObjectRocket system by pointing the tools at either a regular or delayed slave. In former case, simply setting read preference to secondary. In the case of a delayed slave, customers should utilize the virtual IP address provided for access.

Point in time Data Validation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If a point in time comparison data set is required, customers can utilize a downloaded backup image in their environment for comparison purposes.
