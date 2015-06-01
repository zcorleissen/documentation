Getting Started Guide
=====================

This guide is designed to help understand how to get up and running on the ObjectRocket platform quickly and easily. There are just a few steps necessary to be up and running with a brand new instance. This guide assumes you're using the ObjectRocket `dashboard <https://app.objectrocket.com/>`_.

Here are the high level steps:

1. Create an ObjectRocket account
2. Add billing info
3. Create an instance
4. Create a database
5. Add an ACL
6. Connect!

Step 1 of 6: Create an account
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Obtaining an ObjectRocket account is as simple as `signing up here <https://app.objectrocket.com/sign_up>`_ and completing the forms listed. Enter your account information, all fields are required. ObjectRocket utilizes a single login for now, but we're working on adding functionality for sub-accounts. For now we recommend using a mailing list if you need access for multiple people, eg. devops@mycompany.com.

Once complete, click 'Launch my account'.

Step 2 of 6: Add billing info
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Before you can create an instance, you'll need to add your billing information. You can do so from the default landing page by clicking 'add a credit card to your account', or by clicking your username on the upper right, clicking 'Billing Information', then clicking the 'Set Credit Card' button on the left side.

Step 3 of 6: Create an instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Here's a breakdown of the differences between a Replica Set and a Sharded instance on our platform:

In our sharded plans, an instance will consist of four redundant mongos servers, three config servers and N number of shards. A shard is comprised of a three member replica set (1 Primary + 2 Secondaries).  This is for data redundancy, fault tolerance, and provides us with the ability to do maintenances in a MongoDB best practice way. These plans also come with Rackspace ServiceNet connectivity with the same datacenter, SSL connection support, and AWS DirectConnect in our London, East-IAD3, and West datacenters. Our sharded plans can also utilize our RocketScale feature which will automatically add additional shards when space usage meets a threshold that you define. In order for this feature to be beneficial however, you must have collections that are sharded (must be at least 256MB+) with a valid shard key, or can use our AutoKey feature in conjunction to automatically add a hashed shard key to collections larger than 256M.

Our replica set plans consist of three members, but consist of a PRIMARY + SECONDARY + ARBITER (non-data bearing). There are 1GB instances which can scale in place to 5GB at 19$/GB/Mo (US DC prices). We also have 5GB and larger replica set instances, which have a flat storage allocation and does not scale like the 1GBs. Replica set instances do not have Rackspace Service Net connectivity nor SSL connectivity. A major difference between our Replica Set instances are that the 1GB versions are intended for development only and are limited to a single database running on 2.4.6. 5GB+ replica set instances are not limited in the number of databases other than by storage space, nor by version, and by default run 2.4.10.

- Click the 'Add Instance' button.

- Select a name for your instance. This can be almost anything, as any alpha numeric string is valid.

- Select a zone that suits your needs. Zones are either Rackspace or AWS Direct Connect zones, labeled by airport codes in that region. Check out the `zone map <http://objectrocket.com/features>`_.

- Select a plan that suits your needs. Consider that as you grow you always add shards in your plan size. For more details, check out `plans and pricing <http://www.objectrocket.com/pricing>`_.

Step 4 of 6: Create a database
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once you've added an instance you should see it under the `Instances` heading. Click the name of your instance to view details about it and once on the details page, you can do several different things, but we'll focus on creating a database for the time being. Scrolling down the page you can see several different headers. Underneath Databases, there are two options: `Add Database` and `Copy Remote Database`. For now, click `Add Database`. This opens a popover with 3 fields, `Database Name`, `Username`, and `Password`. Simply fill in each and click the `Add Database` button to finish the process. Once this is done you can also go further and add collections or more users, but you can also do that via code or through the mongo shell now that you have a way to authenticate.

Step 5 of 6: Add an ACL
~~~~~~~~~~~~~~~~~~~~~~~

Back to the instance details page, under the heading `Security`, you have the option to `Add ACL`. This is necessary as we don't allow any access by default so you need to add any appropriate ACL's for your servers connecting to ObjectRocket. There are two fields: `IP Address` and `Description`. Only IP is mandatory, but a description can certainly help if you plan to have more than a few.

Step 6 of 6: Connect!
~~~~~~~~~~~~~~~~~~~~~~~

Provided you've added an ACL and have a database with a user you can authenticate with, you can test basic connectivity from your terminal of choice with the Mongo shell:

::

	$ mongo iad-mongos0.objectrocket.com:<PORT>/<DATABASE> -u <USER> -p <PASSWORD>
	MongoDB shell version: 2.4.6
	connecting to: iad-mongos0.objectrocket.com:<PORT>/<DATABASE>
	mongos> show collections
	exampleDB
	system.indexes
	system.users
	mongos>

If see something similar after running `show collections` you're connected and can do anything you'd expect to against this database. If you run into any issues or just want some guidance please don't hesitate to reach out to us at `support@objectrocket.com <mailto:support@objectrocket.com>`_!
