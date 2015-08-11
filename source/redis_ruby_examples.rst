Ruby Connection Examples
========================

<driver name>
-------------

.. |checkmark| unicode:: U+2713

The C# Redis driver is an officially recommended driver, and it's called `name <`https://link>`_.

Installation
~~~~~~~~~~~~

Installing `name <https://link>`_ is simple, using  :

.. code-block:: language

   $ command

Connecting, Authenticating, SET, GET, and DEL
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: go
   
  package main

  import "github.com/garyburd/redigo/redis"
  import "fmt"

  func main() {
	//Connect
	c, err := redis.Dial("tcp", "6d0350b##########523956f768b.publb.rackspaceclouddb.com:6379")
	if err != nil {
		panic(err)
	}
	defer c.Close()

	//Authenticate
	c.Do("AUTH", "KtKzkTB##############4jExUADzRfKC")

	//Set two keys
	c.Do("SET", "key1", "I'm a value!")
	c.Do("SET", "key2", "I am too!")

	//Get a key
	key1, err := redis.String(c.Do("GET", "key1"))
	if err != nil {
		fmt.Println("key1 not found")
	} else {
		//Print our key if it exists
		fmt.Println("key1 exists: " + key1)
	}

	//Delete a key
	c.Do("DEL", "key2")

	//Try to retrieve the key we just deleted
	key2, err := redis.String(c.Do("GET", "key2"))
	if err != nil {
		fmt.Println("key2 not found", err)
	} else {
		//Print our key if it exists
		fmt.Println(key2)
	}
  }

Output from above:

.. code-block:: bash
   
   $ go run redis.go
   
   key1 exists: I'm a value!
   key2 not found redigo: nil returned


Additional reading
~~~~~~~~~~~~~~~~~~

If you need more help with `driver`, here are some links to more documentation:

* `link FAQ <https://link>`_
* `link API Documentation <http://link>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
