External Integrations
=====================


New Relic
-------------------------

ObjectRocket has the ability to send metrics to the New Relic monitoring service.  Each instance has it's own dashboard inside New Relic.
There is no external client to run, simply plug the New Relic License key into the external integrations page on your ObjectRocket control
panel and data is automated sent to New Relic via API.

Enabling the Plugin
^^^^^^^^^^^^^^^^^^^

Configuration is a simple one step process.

* This feature must be enabled via the external `integrations`_ page.  Enter your New Relic license key. You will need a New Relic `login`_ if you don't already have one. You can grab your license key from your `accounts`_ page on the New Relic site.

All instances will start reporting data to New Relic.

.. _integrations: https://app.objectrocket.com/external
.. _accounts: https://rpm.newrelic.com/accounts
.. _login: https://rpm.newrelic.com/login

New Relic Charts
^^^^^^^^^^^^^^^^

* One configured, data will automatically be sent to New Relic on a periodic interval (roughly 300 seconds).


Disabling the plugin
^^^^^^^^^^^^^^^^^^^^

To disable a particular instance:

* Go to the instance settings page, and click the 'New Relic Monitoring' setting to off.

To disable the plugin completely:

* Go to the external `integrations`_ page and remove the New Relic license key and select update.  An empty field disables the feature entirely.