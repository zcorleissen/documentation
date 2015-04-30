Getting Started Guide
=====================

This guide is designed to get you up and running on the ObjectRocket system quickly and easily. There are just a few steps that need to be completed in the ObjectRocket control panel to launch a brand new instance: 

1. Create an Account
2. Provide Billing Information
3. Provision a Database

Create an ObjectRocket Account
------------------------------

Obtaining an ObjectRocket account is as simple as just `signing up here <https://app.objectrocket.com/sign_up>`_ and completing 3 steps.

Step 1 of 3: Create an Account
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Enter your account information, all fields are required.  ObjectRocket utilizes a single email address as the login for each account. So, choose a good one that fits for your group.  For instance, customers use devops@mycompany.com or objectrocket@mycompany.com.

Once complete, click ‘Launch my account’.

Step 2 of 3: Provide Billing Information
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Billing information needs to be added for the account. Visa, MasterCard, American Express, Diners Club, JCB are acceptable forms of payment. Billing occurs on instance creation, and monthly anniversary thereafter.  If a free trial is chosen billing occurs at the end of the 30-day trial period or when an additional shard or instance is added to the account.

Click on the ‘add a credit card to your account' link and enter your credit card information.    

Step 3 of 3: Provision a Database
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A plan is the unit of MongoDB or Redis storage required. A plan and a single MongoDB shard or Redis instance are analogous.  You can add more MongoDB shards and additional or larger Redis instances to your plan as your dataset grows.

- Select a name for your instance.  This can be any logical name.  Any alphanumeric string is valid.

- Select a zone that suits your needs.  Zones are either Rackspace or AWS Direct Connect datacenters.

- Select a plan that suits your needs.  Consider that as you grow you add MongoDB shards in your plan size and additional or larger Redis instances. More details on plans and pricing are available `here <http://www.objectrocket.com/pricing>`_.

- Click on the ‘Create Instance’  button.  Your instance is provisioned and listed as a resource.


You are almost done!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are just a couple more tasks to complete once your instance is created. ObjectRocket disallows access by default, so you will need to create an initial database with an initial database user, as well as open the firewall by adding ACLs to the web UI.

.. _create-a-database:

Create a Database
------------------------------

ObjectRocket grants access utilizing a combination of native MongoDB and Redis authentication and an access control list (ACL). The first step is to create a database, and give it a username and password credentials so you can get connected. Head to the `instances <https://app.objectrocket.com/instances>`_ page then click on the instance to which you would like to add a database. Click the ‘Add Database’  button.  Name the database, add an initial username, and provide a password. You can always add more users later; just add one for now.

Add an ACL
------------------------------

An ACL allows access from an outside network into the ObjectRocket system. It's based on an CIDR type IP address mask. ObjectRocket makes it easy to manage your ACL lists. Head to the `instances <https://app.objectrocket.com/instances>`_ page then click on the instance to which you would like to add an ACL. Select the ACL tab, and the 'Add ACL' button. ACLs are granted to an instance, so they allow access to every database in that instance. Enter the IP address of your client, and a brief description. The description just helps you keep track of what rules you have already created easily. If you don't know the address of your client, appserver, or webserver you can get its address using this technique:

.. code-block:: bash

    $>telnet www4.v6address.com
    Trying 184.105.238.114...
    Connected to www4.v6address.com.
    Escape character is '^]'.
    This is the telnet autoresponder at v6address.com.
    You have connected over IPv4.
    Your IP address is 1.1.1.1
    Connection closed by foreign host.

In order to open an ACL for this one host, you would enter 1.1.1.1/32 for the IP address. Once you hit submit it may take a few minutes for the ACL to take effect so be patient.

Congrats!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You are all set to start using your ObjectRocket instance.  Your connect string details are listed on the Instances page.

If you have any questions, concerns or comments please reach our database experts at support@objectrocket.com.
