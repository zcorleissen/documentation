ObjectRocket Backup and Recovery Guide
======================================

Overview
--------

Each instance is protected by replication. Should any component fail, the replica set architecture of MongoDB provides the primary level of high availability, fault tolerance and uptime. However as a last resort and for overall data protection backups are taken on the ObjectRocket system.

Backups
-------

Data backups are provided so customers can have access to point in time copy of their data. Backups are taken at regular intervals. Backups are taken per instance. A list of backup images can be seen under the GUI application at app.objectrocket.com under the instances->backups tab.

Backups are taken off a slave member, and are archived on the ObjectRocket system. The backup mechanism is a file-level mongodb backup. The files from a replica are copied to a backup location via OS level tools. All instances run with journaling enabled, however, recovery does not require any journal reply because the disk images are guaranteed consistent.

Because ObjectRocket is inherently sharded, backups are designed according to best practices to ensure backups are as consistent as possible among the members of a cluster (instance). Each instance is backed up with a high level of consistency, but not guaranteed consistency. They are not true point in time.

Customer Recovery Options
-------------------------

Download a backup image
~~~~~~~~~~~~~~~~~~~~~~~

Each backup is available for download. Customers need to email support@objectrocket.com and indicate the backup image to be restored. A list of the backup images is available in the ObjectRocket gui application under ‘backups’ for each database. The backup is then posted to Rackspace cloudfiles under the the customer API Key (or alternatively a ObjectRocket API Key). The customer can then restore the backup offsite.

If a customer has a single shard, recovery on an external environment to ObjectRocket is as simple as starting a downloaded backup image, uncompressing/untarring the datafiles into a directory, and starting MongoDB with that location as the --dbpath argument.

For instances with more than one shard, contact support@objectrocket.com for help with restoration in an environment external to ObjectRocket.

In place restore
~~~~~~~~~~~~~~~~

On customer request, an existing and running instance can be replaced/recovered with a backup image. All data in the existing instance will be replaced with the data of the backup image essentially ‘rolling back’ the entire instance. Customers need to email support@objectrocket.com requesting an in-place recovery.

Human Error
~~~~~~~~~~~~~~~~~~~~~~

Code release, mis-typing, or other human errors recovery is accomplished using a time delayed replica. In the case of a problem, the replica is manually stopped and opened in a read/only mode to manually piece back together the data. In order to have an instance enabled for a delayed slave, customers need to email support@objectrocket.com and request a delayed slave. This feature is an additional cost. Direct access to this delayed slave can be provided via a virtual IP address for tools/scripts to have access specifically to the delayed slave. Recovery is a customer responsibility beyond the core components provided by ObjectRocket. This is due to the fact there is an inherent knowledge of the schema, application and customer data required.

Data Validation Options
-----------------------

Continuous Data Validation
~~~~~~~~~~~~~~~~~~~~~~~~~~

It may be desirable for the customer to be able to validate data from time to time. The general approach is to point a diff tool or other comparison tool created by the customer at a slave instance and compare it against some other known archive. This can be accomplished on the ObjectRocket system by pointing the tools at either a regular or delayed slave. In former case, simply setting read preference to secondary. In the case of a delayed slave, customers should utilize the virtual IP address provided for access.

Point in time Data Validation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If a point in time comparison data set is required, customers can utilize a downloaded backup image in their environment for comparison purposes.