Getting Started with MongoDB
============================

1. Create an instance
2. Create a database
3. Add an ACL
4. Connect!

1. Create an instance
~~~~~~~~~~~~~~~~~~~~~

.. note::

   If you need help deciding what kind of instance to create, take a look at our :doc:`mongodb_overview`!

	
- Click the **Add Instance** button.

.. image:: images/addinstance.png
   :align: center

- Select a name for your instance. This can be almost anything, as any alpha numeric string is valid.

- Select a Service, MongoDB in this case.

- Select a type, either MongoDB Sharded or MongoDB Replica Set. The differences are outlined briefly below the type chosen, but more information can be found on our `MongoDB Overview <http://objectrocket.com/docs/mongodb_overview.html>`_.

.. image:: images/createmongo.png
   :align: center

- Select a version to deploy. We offer MongoDB 2.4, 2.6, and 3.0.

- Select a plan that suits your needs. Consider that as you grow you always add shards in your plan size when using a Sharded instance, but that isn't possible for a Replica Set. For more details, check out `plans and pricing <http://objectrocket.com/pricing>`_.

- Select a zone that suits your needs. Zones are either Rackspace and/or AWS Direct Connect zones, labeled by airport codes in that region. Check out the `zone map <http://objectrocket.com/features>`_.

- Select a Storage Engine. When using MongoDB 3.0 you have the option of alternate storage engines. We currently offer WiredTiger and MMAPv1 when using 3.0+.

.. image:: images/createmongo_2.png
   :align: center

2. Add a database
~~~~~~~~~~~~~~~~~~~~

.. image:: images/adddatabase.png
   :align: center

Once you've added an instance you should see it under the **Instances** heading. Click the name of your instance to view details about it and once on the details page, you can do several different things, but we'll focus on creating a database for the time being. Scrolling down the page you can see several different headers. Underneath Databases, there are two options: **Add Database** and **Copy Remote Database**. For now, click **Add Database**. This opens a popover with 3 fields, **Database Name**, **Username**, and **Password**. Simply fill in each and click the **Add Database** button to finish the process. Once this is done you can also go further and add collections or more users, but you can also do that via code or through the mongo shell now that you have a way to authenticate.

3. Add an ACL
~~~~~~~~~~~~~

Back to the instance details page, under the heading **Security**, you have the option to **Add ACL**. This is necessary as we don't allow any access by default so you need to add any appropriate ACL's for your servers connecting to ObjectRocket. There are two fields: **IP Address** and **Description**. Only IP is mandatory, but a description can certainly help if you plan to have more than a few.

.. image:: images/addacl_mongo.png
   :align: center

4. Connect!
~~~~~~~~~~~

Provided you've added an ACL and have a database with a user you can authenticate with, you can test basic connectivity from your terminal of choice with the Mongo shell:

::

	$ mongo iad-mongos0.objectrocket.com:<PORT>/<DATABASE> -u <USER> -p <PASSWORD>
	MongoDB shell version: 2.4.6
	connecting to: iad-mongos0.objectrocket.com:<PORT>/<DATABASE>

	mongos> show collections
	example_collection
	system.indexes
	system.users

	mongos>


If you see something similar after running ``show collections`` you're connected to the instance and can do anything you'd expect to against the database. If you run into any issues or just want some guidance please don't hesitate to reach out to our `Support team <mailto:support@objectrocket.com>`_!
