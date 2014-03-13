Tools
=====

ObjectRocket has created a couple of example tools to use in
conjunction with the ObjectRocket service. The ObjectRocket API makes
it very easy to query the service for data and metadata for various
things like monitoring or performance tools.

Rocketstat
----------

Rocketstat is a clone of the popular mongostat utility. This utility
show various performance metrics about the ObjectRocket instance.
Note the data is an aggregation of all shards. It runs on the command
line, and probes the ObjectRocket API for data every N seconds and
reports the performance data on the command line. It is actually
based on the original python implementation of mongostat from 2009.
Licensed under the Apache License, Version 2.0.


`Rocketstat Github Repo <https://github.com/objectrocket/rocketstat>`_


RocketTop
---------

RocketTop is a real-time statistics viewer for ObjectRocket. It runs
on the command line and probes the ObjectRocket API for real time
session data every N seconds and displays the results similarly to
the Unix "top" utility. Licensed under the Apache License, Version
2.0.


`RocketTop Github Repo <https://github.com/objectrocket/rockettop>`_

