Go Connection Examples
======================

.. |checkmark| unicode:: U+2713

The Go Redis driver is an officially recommended driver, and it's called `redigo <https://github.com/garyburd/redigo>`_.

Installation
------------

Installing `redigo <https://github.com/garyburd/redigo>`_ is simple, using the usual go get procedure:

.. code-block:: bash

   $ go get github.com/garyburd/redigo/redis

Connecting, Authenticating, SET, GET, and DEL
---------------------------------------------

Connecting:

.. code-block:: go
   
  package main

  import "github.com/garyburd/redigo/redis"
  import "fmt"

  func main() {
		//Connect
		c, err := redis.Dial("tcp", "6d0350bed9274caf83e23523956f768b.publb.rackspaceclouddb.com:6379")
		if err != nil {
			panic(err)
		}
		defer c.Close()

		//Authenticate
		c.Do("AUTH", "KtKzkTB2HzprK9jf9kPFgaB94jExUADzRfKC")

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
			fmt.Println("key2 not found")
		} else {
			//Print our key if it exists
			fmt.Println(key2)
		}
  }

Output from above:

.. code-block:: bash
   
   $ go run redis.go
   
   key1 exists: I'm a value!
   key2 not found


Additional reading
------------------

If you need more help with `redigo`, here are some links to more documentation:

* `redigo FAQ <https://github.com/garyburd/redigo/wiki/FAQ>`_
* `redigo API Documentation <http://godoc.org/github.com/garyburd/redigo/redis>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
