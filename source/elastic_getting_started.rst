Getting Started with Elasticsearch
===================================

1. Create an instance
2. Add an Admin User
3. Add an ACL


#How do I start?
#---------------
#
#If you have questions, we have data services specialists ready to assist, just contact us `here <http://objectrocket.com/contact>`_ or e-mail us at `sales@objectrocket.com <mailto:sales@objectrocket.com>`_!
#
#If you are ready to sign up now and don’t already have an ObjectRocket account go to our `sign up <https://app.objectrocket.com/sign_up>`_ page to create one, or `log in <https://app.objectrocket.com>`_ to get started.


1. Create an instance
~~~~~~~~~~~~~~~~~~~~~

.. image:: images/addinstance.png
   :align: center

- Click the **Add Instance** button.

- Select a name for your instance. This can be almost anything, as any alpha numeric string is valid.

- Select a backend engine, Elasticsearch in this case.

- Select the default **Clustered** type.

- Select the default Elasticsearch zone, but we'll be launching in other zones soon!

- Select the best Memory and Storage size for your application.

.. image:: images/create_elastic.png
   :align: center
   :height: 631px
   :width: 500 px
   :scale: 70%

- Click the **Create Instance** button.

You'll now be routed back to the **Instances** page, where you can see the build status of your instance. Yellow means it's in the build process, and green means it's ready to use. Click the name of your new instance to continue.

2. Add an Admin User
~~~~~~~~~~~~~~~~~~~~

- Under the **Users** heading, click the **Add User** button. Fill in the username and password, and for your first user make sure to create it as Admin.

.. image:: images/add_user_elastic.png
   :align: center


3. Add an ACL
~~~~~~~~~~~~~

- Under the heading **Security**, you have the option to **Add ACL**. This is necessary as we don't allow any access by default so you need to add any appropriate ACL's for your servers connecting to ObjectRocket. There are two fields: **IP Address** and **Description**. Only IP is mandatory, but a description can certainly help if you plan to have more than a few.

- We also offer connectivity via the Transport Protocol, using the Java transport client. Transport access lacks any authentication and as such must be explicitly allowed through an ACL option as seen in the screenshot below. Adding an ACL with the ``Transport Interface`` checked includes regular HTTP/HTTPS as well, so there's no need to add an additional to cover both.

.. image:: images/addacl.png
   :align: center
