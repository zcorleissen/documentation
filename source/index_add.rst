API Overview
================

Overview
----------------
Use this API to add an index for a field. 

.. code-block:: bash

  curl --data 'api_key=<key>&doc={"index": {"key": <field>[, "sort": <direction>]}}' '<api_server>/db/<database>/collection/<collection>/index/add'
  
