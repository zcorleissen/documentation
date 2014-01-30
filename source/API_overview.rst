API Overview
================

Overview
----------------
The ObjectRocket API is a REST based HTTP API over SSL. The API can be used in addition and along side the MongoDB driver access into ObjectRocket. Both regular data operations like add,get,update,delete are supported against any collection as well as various metadata operations are supported for observability and management of the instance.

Any client that supports an HTTP interface should work well with the ObjectRocket API. Examples of how to use the API exist for python,node.js,java,and php.

The API expects a POST with a document, and an API KEY. The document can be the document to write to the database and optionally, can be a query object (the predicate for the query). The API then returns a JSON formatted string with a return code, and the data requested or in the case of a failure the error msg.

.. code-block:: javascript

    {
        rc: 0,                  // success
        data: data_payload      // the data or metadata payload returned
    }

In the case of an error the format is:

.. code-block:: javascript

    {
        rc: 1,                  // a problem occurred
        msg: returned_message   // the error message
    }


Authentication
----------------

In order to use the API you must authenticate using your API key. A key is a unique key for each customer/instance pair. You can find your key in the 'API' column on the `instances`_ page.

.. _instances: https://app.objectrocket.com/instances