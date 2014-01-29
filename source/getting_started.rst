Getting Started Guide
=====================

This guide is designed to help understand how to get up and running on the ObjectRocket system quickly and easily. There are just a few steps that need to be completed to be up and running with a brand new instance. This guide assumes using the ObjectRocket web interface.

1. Get an ObjectRocket account
2. Add billing information
3. Create an instance
4. Create a database
5. Add a ACL

Get an ObjectRocket account
----------------

Obtaining an ObjectRocket account is as simple as just [signing up here](https://app.objectrocket.com/sign_up1)

Add billing information
----------------

Before an instance can be created, the account must be updated with current credit card information. Visa, MasterCard, American Express, Diners Club, JCB are all acceptable forms of payment. Billing occurs on instance creation, and monthly thereafter.

To add a card after sign up, go to the [account page](http://app0.sjc.objectrocket.com:8081/billing), and enter a credit card.

Create an instance
----------------

An instance is a complete MongoDB cluster. It's the container in which you will interact with the ObjectRocket service. You can have multiple instances.

First go to the instances page, and select add instance. The add instance dialog will pop up. Add a name for the instance, Any alphanumerical string is fine, no spaces. Also choose a plan, and instance size in the plan selector box. Click submit. You have just provisioned a fully redundant, highly performant, sharded, and replicated instance.

Create a database
----------------

ObjectRocket grants access utilizing a combination of native MongoDB authentication and an ACL. The first step is to create a database, and give it a username and password credentials so you can get connected. Head to the instances page then click on the instance you would like to add a database to. Use the Add Database button on the databases page to add a database. Simply name the database, and add an initial username and password. You can always add more users later, just add one for now.

Add a ACL
----------------

An ACL allows access from an outside network into the ObjectRocket system. It's based on an CIDR type IP address mask. ObjectRocket makes it easy to manage your ACL lists. Head to the instances page then click on the instance you would like to add a ACL to. Select the ACL tab, and the add ACL button. ACL's are granted to an instance, so they allow access to every database in that instance. Enter the IP address of your client, and a brief description. The description just helps you keep track of what rules you have already created easily. If you don't know the address of your client, appserver, or webserver you can get it as shown below from the command line:

.. code-block:: javascript

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
----------------

You are all set to start using your ObjectRocket instance. See how to connect via MongoDB native drivers, or via the ObjectRocket API.  If you have any questions, concerns or comments please reach out at [support@objectrocket.com](mailto:support.objectrocket.com)