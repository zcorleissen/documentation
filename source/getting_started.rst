Getting Started Guide
=====================

This guide helps you get started quickly and easily on the ObjectRocket platform. You can get a brand new instance up and running with only a few steps. 

This guide assumes you're using the ObjectRocket `dashboard <https://app.objectrocket.com/>`_.

1. Create an ObjectRocket account
2. Add billing info
3. Create an instance
4. Create a database
5. Add an ACL
6. Connect!

Create an account
~~~~~~~~~~~~~~~~~

`Sign up for ObjectRocket here <https://app.objectrocket.com/sign_up>`_. Enter your account information (all fields required) and click *Launch my account*.

ObjectRocket utilizes a single login for now, but we're working on adding functionality for sub-accounts. For now we recommend using a mailing list if you need access for multiple people. For example: `devops@mycompany.com`.

Add billing info
~~~~~~~~~~~~~~~~

Before you can create an instance, you'll need to add your billing information. Click *Add Credit Card* on the default landing page, or click your username on the upper right, click *Billing Information*, then click *Set Credit Card*.

Create an instance
~~~~~~~~~~~~~~~~~~

After you've entered billing information, you can add an instance.

1. Click the Instance heading, then click on *Add Instance*.

2. Select a name for your instance. 

    This can be almost anything, as any alphanumeric string is valid.

3. Select a service.

    Choose from Elasticsearch (clustered), MongoDB (sharded instance or replica set, see below), or Redis (HA Redis).

    Click on *Step 2* to continue.

4. Select a version.

    Select the **version** of the database service you'd like to run.

5. Select a zone.

    **Zones** are either Rackspace or AWS Direct Connect zones, labeled by airport codes in that region. Choose between Houston (IAD), Dallas (DFW), or London (LON).

6. Select a plan that suits your needs. 

    Consider that as you grow, your plan determines the size of shards as they're added. For more details, check out `plans and pricing <http://www.objectrocket.com/pricing>`_.

MongoDB: sharded instance vs. replica set
-----------------------------------------

In ObjectRocket, **sharded instances** consist of four redundant mongo servers, three config servers, and `<N>` number of shards. A shard is comprised of a three member replica set (1 PRIMARY + 2 SECONDARY). This set model creates data redundancy, fault tolerance, and lets Rackspace perform maintenance according to MongoDB best practices. 

Sharded instance plans also include:

    * Rackspace ServiceNet connectivity with the same datacenter
    * SSL connection support
    * AWS DirectConnect in our London, East-IAD3, and West datacenters
    * RocketScale: automatically add additional shards when space usage meets a threshold you define

    RocketScale works best with collections larger than 256MB that have a valid shard key or can use our AutoKey feature to automatically add a hashed shard key to collections larger than 256MB.

ObjectRocket's **replica set** plans consist of three members: PRIMARY + SECONDARY + ARBITER (non-data bearing). Rackspace offers two replica set plans: 1GB and 5+GB.

+-----------+-----------------------------------+--------------------+
| Feature   | 1GB                               | 5+GB               |
+===========+===================================+====================+
| Scalable? | Yes: automatic scaling up to 5GB  | No: flat size      |
|           |                                   | allocation         |
+-----------+-----------------------------------+--------------------+
| Number of | Limited to 1;                     | Unlimited within   |
| databases | intended for development only     | storage limits     |
+-----------+-----------------------------------+--------------------+
| MongoDB   | 2.4.6 only                        | 2.4.10 by default; |
| version   |                                   | other versions     |
|           |                                   | permitted          |
+-----------+-----------------------------------+--------------------+

Replica set instances do not offer Rackspace ServiceNet connectivity nor SSL connectivity.

Create a database
~~~~~~~~~~~~~~~~~

After you add an instance, it appears under the `Instances` heading. Click on the name of your instance to view instance details. Scrolling down the page you can see several different headers. Underneath Databases, there are two options: `Add Database` and `Copy Remote Database`. For now, click `Add Database`. This opens a popover with 3 fields, `Database Name`, `Username`, and `Password`. Simply fill in each and click the `Add Database` button to finish the process. Once this is done you can also go further and add collections or more users, but you can also do that via code or through the mongo shell now that you have a way to authenticate.

Add an ACL
~~~~~~~~~~

Back to the instance details page, under the heading `Security`, you have the option to `Add ACL`. This is necessary as we don't allow any access by default so you need to add any appropriate ACL's for your servers connecting to ObjectRocket. There are two fields: `IP Address` and `Description`. Only IP is mandatory, but a description can certainly help if you plan to have more than a few.

Connect!
~~~~~~~~

Provided you've added an Access Control List (ACL) and have a database with a user you can authenticate with, you can test basic connectivity from your terminal of choice with the Mongo shell:

::

	$ mongo iad-mongos0.objectrocket.com:<PORT>/<DATABASE> -u <USER> -p <PASSWORD>
	MongoDB shell version: 2.4.6
	connecting to: iad-mongos0.objectrocket.com:<PORT>/<DATABASE>
	mongos> show collections
	example      0.000MB / 0.004MB
	system.indexes  0.000MB / 0.008MB
	system.users    0.000MB / 0.008MB
	mongos>

If see something similar after running `show collections` you're connected and can do anything you'd expect to against this database. If you run into any issues or just want some guidance please don't hesitate to reach out to us at `support@objectrocket.com <mailto:support@objectrocket.com>`_!
