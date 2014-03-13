External Integrations
=====================


New Relic
-------------------------

ObjectRocket has the ability to send metrics to the New Relic monitoring service.  Each instance has it's own dashboard inside New Relic.
There is no external client to run, simply plug the New Relic License key into the external integrations page on your ObjectRocket control
panel and data is automated sent to New Relic via API.

Configuration
^^^^^^^^^^^^^

Configuration is a simple two step process.

* This feature must be enabled via the external `integrations`_ page.  Enter your New Relic license key. You will need a New Relic `login`_ if you don't already have one. You can grab your license key from your `accounts`_ page on the New Relic site.
* Each instance must have the setting 'New Relic Monitoring' enabled on the ObjectRocket instance settings page.

.. _integrations: https://app.objectrocket.com/external
.. _accounts: https://rpm.newrelic.com/accounts
.. _login: https://rpm.newrelic.com/login

New Relic Charts
^^^^^^^^^^^^^^^^

* One configured, data will automatically be sent to New Relic on a periodic interval (roughly 300 seconds).