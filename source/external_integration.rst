External Integration
====================

New Relic Metric Reporting
--------------------------
The ObjectRocket platform can automatically report metrics about your instances to the New Relic monitoring service.

Enabling New Relic Integration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To enable New Relic integration:

* Browse to the `external integration`_ page.
    * At the top right of the ObjectRocket UI, click on the person icon with your login
    * From the dropdown, select 'Manage External Integration'
* Add a New Relic Credential.
    * Enter a valid New Relic License Key.

By default, metrics with automatically be reported for all instances. Each instance will appear as an individual dashboard. Metrics are sent about once every five minutes.


Disabling New Relic Integration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To disable the reporting of metrics to New Relic for a particular instance:

* Browse to the settings page for that instance
* Set the button labeled 'New Relic Monitoring' to off.

To disable New Relic integration completely:

* Browse to the `external integration`_ page.
    * At the top right of the ObjectRocket UI, click on the person icon with your login
    * From the dropdown, select 'Manage External Integration'
    * Click the button labeled 'Delete License Key'.

|

ACLSync
-------------------------
The ObjectRocket platform can automatically retrieve IP addresses from your environment, and create an ACL for each of those IPs on each of your instances. This feature is currently limited to retrieving IP addresses from a single AWS region.


Enabling ACLSync
^^^^^^^^^^^^^^^^

AWS
~~~~

To enable AWS ACL Synchronization:

* Browse to the `external integration`_ page.
    * At the top right of the ObjectRocket UI, click on the person icon with your login
    * From the dropdown, select 'Manage External Integration'
* Add AWS credential information.
    * In the 'AWS' section, Select the AWS region from which to retrieve IP addresses.
    * Enter a valid AWS Access Key ID.
    * Enter the AWS Secret Key that corresponds to the Access Key ID.
    * Click the button labeled 'Set AWS Access Keys'.

By default, ACLs will automatically be created for all instances.


Disabling ACLSync
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

AWS
~~~~

To disable automatic ACL creation for a particular instance:

* Browse to the settings page for that instance
* Set the button labeled 'AWS ACL Synchronization' to off.

To disable automatic ACL creation completely:

* Browse to the `external integration`_ page.
    * At the top right of the ObjectRocket UI, click on the person icon with your login
    * From the dropdown, select 'Manage External Integration'
    * Under 'ACLSync', in the 'AWS' section, click the button labeled 'Delete AWS Access Keys'.

.. _external integration: https://app.objectrocket.com/external
.. _accounts: https://rpm.newrelic.com/accounts
.. _New Relic login: https://rpm.newrelic.com/login
