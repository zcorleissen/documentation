MongoDB Rescources
==================

Description: Lorem Ipsum

/instances/
-----------

/instances/<instance_name>/
---------------------------

========== ========================================
HTTP VERBS Description
========== ========================================
GET        Performs a read of the object
POST       Creates a new object using <name>
DELETE     Deletes the object and associated things
========== ========================================

Example Request:

.. code-block:: bash

   $ http --auth 'user@example.com:password' 'https://sjc-api.objectrocket.com/v2/mongodb/test123/backups/'

Example Response:

.. code-block:: bash

   {
            "_id": {
                "$oid": "55b1e6f95559617dd0a517ec"
            },
            "backup_directory": "/backups/55410c7f5b335278490a5be8/20150724_0018",
            "backup_host": "sydbackups0.syd.objectrocket.com",
            "error_msg": "Successful, completed in 61 seconds",
            "filenames": {
                "5db16d02db25b9673ff2f72440366df0": "5db16d02db25b9673ff2f72440366df0_20150724_0018.tgz",
                "90a85209de63519f0c04728a1bdb9313": "90a85209de63519f0c04728a1bdb9313_20150724_0018.tgz",
                "config_server": "config_12345_20150724_0018.tgz"
            },
            "instance_id": {
                "$oid": "55410c7f5b335278490a5be8"
            },
            "instance_name": "test123",
            "instance_type": "mongodb_sharded",
            "login": "donovan@heydonovan.io",
            "port": 12345,
            "timestamp": {
                "$date": 1437697100909
            },
            "timestamp_formatted": "2015/07/24 00:18:20"
        }

Redis
~~~~~

more stuff

