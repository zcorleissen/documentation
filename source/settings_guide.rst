ObjectRocket Settings
=====================

Each ObjectRocket instance has various settings that control its operation.


Stepdown Window
---------------

The stepdown window controls define a period of time for which our
stepdown daemon can cause a primary election to occur.


Options
^^^^^^^

* Stepdown Scheduled: Schedules your instance for stepdown operations. This
  option does nothing if the stepdown window isn't both on and defined.
* Stepdown Window: Enables or disables the stepdown window.
* Start and Stop: The stepdown daemon will step down your instance **once**
  within the defined stepdown window.
* Run Weekly: When enabled, the stepdown daemon will run once every week,
  starting in the window you've specified. The stepdown daemon adds a week to
  the start and stop portions of the window after it performs a stepdown
  operation against your instance.
* Weekly Compaction: When enabled, this instance will be compacted once per
  week during the defined stepdown window.


Replica Set Instances
^^^^^^^^^^^^^^^^^^^^^

When scheduled, the stepdown daemon will run the
`replSetStepDown <http://docs.mongodb.org/manual/reference/command/replSetStepDown/#dbcmd.replSetStepDown>`_
command against your instance's replica set.


Sharded Instances
^^^^^^^^^^^^^^^^^

When scheduled, the stepdown daemon will run the
`replSetStepDown <http://docs.mongodb.org/manual/reference/command/replSetStepDown/#dbcmd.replSetStepDown>`_
command against every shard in your instance.
