Go Connection Examples
======================

.. |checkmark| unicode:: U+2713

The Go Redis driver is an officially recommended driver, and it's called `redigo <https://github.com/garyburd/redigo>`_.

Installation
------------

Installing `redigo <https://github.com/garyburd/redigo>`_ is simple, using the usual go get procedure:

.. code-block:: bash

   $ go get github.com/garyburd/redigo/redis

Connecting, Authenticating, SET, and GET
----------------------------------------

Connecting:

.. code-block:: go
  :linenos:
 
  package main

  import "github.com/garyburd/redigo/redis"
  import "fmt"

  func main() {
  //INIT OMIT
  c, err := redis.Dial("tcp", "6d0350bed9274caf83e23523956f768b.publb.rackspaceclouddb.com:6379")
  if err != nil {
  panic(err)
  }
  defer c.Close()

  //auth
  c.Do("AUTH", "KtKzkTB2HzprK9jf9kPFgaB94jExUADzRfKC")

  //set
  c.Do("SET", "YoDawg", "I heard you like Redis")

  //get
  world, err := redis.String(c.Do("GET", "YoDawg"))
  if err != nil {
  fmt.Println("key not found")
  }
  
  fmt.Println(world)
  //ENDINIT OMIT
  } 

Output from above:

.. code-block:: bash
   
   $ go run redis.go
   $ I heard you like Redis


Additional reading
------------------

If you need more help with `redigo`, here are some links to more documentation:

* `redigo FAQ <https://github.com/garyburd/redigo/wiki/FAQ>`_
* `redigo API Documentation <http://godoc.org/github.com/garyburd/redigo/redis>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
