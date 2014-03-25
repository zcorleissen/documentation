Getting Started Guide
=====================

This guide is designed to help understand how to get up and running on the ObjectRocket system quickly and easily. There are just a few steps that need to be completed to be up and running with a brand new instance. This guide assumes using the ObjectRocket web interface.

There are just a few steps to getting up and running:

1. Create an ObjectRocket account, instance, and enter billing info.
2. Create a database
3. Add a ACL

Create an ObjectRocket account
------------------------------

Obtaining an ObjectRocket account is as simple as just `signing up here <https://app.objectrocket.com/sign_up1>`_ and completing 3 steps.

Step 1 of 3: Add account information
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Enter your account information, all fields are required.  ObjectRocket utilizes a single login for an entity. So choose a good login that fits for your group.  For instance, some customers use devops@mycompany.com or similar.

Once complete, click 'next'.

Step 2 of 3: Select a plan
~~~~~~~~~~~~~~~~~~~~~~~~~~~

A plan is the unit of MongoDB storage required. A plan and a single shard are synonyms.  You can add more shards to your plan as your dataset grows.

- Select a name for your instance.  This can be any logical name.  Any alpha numeric string is valid.

- Select a zone that suits your needs.  Zones are either Rackspace or AWS Direct Connect zones.

- Select a plan that suits your needs.  Consider that as you grow you always add shards in your plan size. More details on plans and pricing are available `here <http://www.objectrocket.com/pricing>`_.

Step 3 of 3: Add billing information
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Billing information needs to be added for the account. Visa, MasterCard, American Express, Diners Club, JCB are all acceptable forms of payment. Billing occurs on instance creation, and monthly thereafter.  A free trial may be available and if so billing would occur at the end of the trial period.

Select the 'enter credit card' button and enter your CC information.  This may take a few seconds.

Once validated, a dialog will give you confirmation of the instance you want to create. Select 'next' to create the instance and be redirected to the web UI and your list of instances.

You are almost done!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are just a couple more things to complete once your instance is created. ObjectRocket disallows access by default, so you will need to create an initial database with an initial database user, as well as open the firewall by adding ACL's to the web UI.

Create a database
------------------------------

ObjectRocket grants access utilizing a combination of native MongoDB authentication and an ACL. The first step is to create a database, and give it a username and password credentials so you can get connected. Head to the `instances <https://app.objectrocket.com/instances>`_ page then click on the instance you would like to add a database to. Use the Add Database button on the databases page to add a database. Simply name the database, and add an initial username and password. You can always add more users later, just add one for now.

Add an ACL
------------------------------

An ACL allows access from an outside network into the ObjectRocket system. It's based on an CIDR type IP address mask. ObjectRocket makes it easy to manage your ACL lists. Head to the `instances <https://app.objectrocket.com/instances>`_ page then click on the instance you would like to add a ACL to. Select the ACL tab, and the add ACL button. ACL's are granted to an instance, so they allow access to every database in that instance. Enter the IP address of your client, and a brief description. The description just helps you keep track of what rules you have already created easily. If you don't know the address of your client, appserver, or webserver you can get it's address using this technique:

.. code-block:: bash

    $>telnet v4address.com
    Trying 184.105.238.114...
    Connected to v4address.com.
    Escape character is '^]'.
    This is the telnet autoresponder at v6address.com.
    You have connected over IPv4.
    Your IP address is 1.1.1.1
    Connection closed by foreign host.

In order to open an ACL for this one host, you would enter 1.1.1.1/32 for the IP address. Once you hit submit it may take a few minutes for the ACL to take effect so be patient.

Congrats!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You are all set to start using your ObjectRocket instance.  Your connect string details are listed on the instances page.

If you have any questions, concerns or comments please reach out at support@objectrocket.com.