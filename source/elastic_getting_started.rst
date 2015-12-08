Getting Started with Elasticsearch
===================================

1. Create an instance
2. Add an Admin User
3. Add an ACL

1. Create an instance
~~~~~~~~~~~~~~~~~~~~~

.. image:: images/addinstance.png
   :align: center

- Click the **Add Instance** button.

- Select a name for your instance. This can be almost anything, as any alpha numeric string is valid.

- Select a Service, Elasticsearch in this case.

- Verify information provided is correct and move on to Step 2

.. image:: images/create_elastic.png
   :align: center

- Select your desired version of Elasticsearch.

- Select a zone that suits your needs. Zones are either Rackspace and/or AWS Direct Connect zones, labeled by airport codes in that region. Check out the `zone map <http://objectrocket.com/features>`_.

- Select the best Memory and Storage size for your application. For more details, check out `plans and pricing <http://objectrocket.com/pricing>`_.

- Verify your selections and click the **Confirm** button.

.. image:: images/create_elastic_2.png
   :align: center

You'll now be routed back to the **Instances** page, where you can see the build status of your instance. Yellow means it's in the build process, and green means it's ready to use. Click the name of your new instance to continue.

2. Add an Admin User
~~~~~~~~~~~~~~~~~~~~

- Under the **Users** heading, click the **Add User** button. Fill in the username and password, and for your first user make sure to create it as Admin.

.. image:: images/add_user_elastic.png
   :align: center


3. Add an ACL
~~~~~~~~~~~~~

- Under the heading **Security**, you have the option to **Add ACL**. This is necessary as we don't allow any access by default so you need to add any appropriate ACL's for your servers connecting to ObjectRocket. There are three fields: **ACL Role**, **IP Address** and **Description**. Adding a description is optional but can certainly help if you plan to have more than a few entries.

- The default ACL Role of **Elasticsearch** allows access to the Elasticsearch REST API and any plugins.  We also allow access to the `Java API <https://www.elastic.co/guide/en/elasticsearch/guide/current/_talking_to_elasticsearch.html#_java_api/>`_ via the Transport Client library -- select **Elasticsearch & Java API** to include this access.

- The **My IP** and **Any IP** buttons offer convenient shortcuts to add either your current IP address or to allow all IP addresses access to your instance.

.. image:: images/addacl_elastic.png
   :align: center
