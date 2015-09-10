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
	c.Do("SET", "best_car_ever", "Tesla Model S")
	c.Do("SET", "worst_car_ever", "Geo Metro")

	//Get a key
	best_car_ever, err := redis.String(c.Do("GET", "best_car_ever"))
	if err != nil {
		fmt.Println("best_car_ever not found")
	} else {
		//Print our key if it exists
		fmt.Println("best_car_ever exists: " + best_car_ever)
	}

	//Delete a key
	c.Do("DEL", "worst_car_ever")

	//Try to retrieve the key we just deleted
	worst_car_ever, err := redis.String(c.Do("GET", "worst_car_ever"))
	if err != nil {
		fmt.Println("worst_car_ever not found", err)
	} else {
		//Print our key if it exists
		fmt.Println(worst_car_ever)
	}
  }

Output from above:

.. code-block:: bash
   
   $ go run redis.go
   
   best_car_ever exists: Tesla Model S
   worst_car_ever not found redigo: nil returned


Additional reading
------------------

If you need more help with `redigo`, here are some links to more documentation:

* `redigo FAQ <https://github.com/garyburd/redigo/wiki/FAQ>`_
* `redigo API Documentation <http://godoc.org/github.com/garyburd/redigo/redis>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
