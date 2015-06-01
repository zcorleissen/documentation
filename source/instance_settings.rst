MongoDB Instance Settings
=========================

This is where you can modify settings specific to this instance.

>General

>> RocketScale Threshold

"RocketScale is our auto-scaling feature with which you can specify a percentage of space currently used and when that limit is hit, an additional shard will be added to scale the instance horizontally. This will only add shards in the current plan size, eg. 5GB instance will have additional 5GB shards added. One caveat here is that if you don't have a `shard key <http://docs.mongodb.org/manual/core/sharding-shard-key/>`_ defined, but have this enabled, a shard will still be added to the instance but not be able to use the additional space for any unsharded collections."

>> Profiling Level

"This allows you to enable a specific `profiling level <http://docs.mongodb.org/manual/tutorial/manage-the-database-profiler/>`_ for databases on this instance. Slow is anything longer than 20ms, and All will log all queries. All does incur a bit of a performance hit as it turns every query into a write, regardless of the query itself."

>> Auto Key

"Auto Key is our feature which will automatically apply a hashed index on collections larger than 256MB that do not already have a shard key defined. It will notify you via email of any created, after it's applied the index and hashed key. It operates per database, so an ideal use case would be to specify shard keys on your larger collections where performance is needed most, and then let our system handle the rest for smaller collections."

>Balancer

"These settings revolve around the MongoDB `balancer <http://docs.mongodb.org/manual/core/sharding-balancing/>`_. Summarizing, the balancer handles data distribution among the shards within in a sharded instance."

>> Balancer Enabled Checkbox

"This enables or disables the balancer entirely. Please use with caution, as if a shard is added and this is turned off, no data will be allocated to the new shard."

>> Balancer Window (UTC)

"This allows you to choose whether the balancer is allowed to run all the time, or within a definable daily window."

>> Balancer Schedule

"This allows you to specify when the balancer runs each day, making sure no data is in transit during peak hours. MongoDB has this set in UTC to help minimize any timezone differences, so please be aware when choosing when this is run."

>Stepdown Window

"ObjectRocket can handle compactions for you automatically, making sure you're only using the least possible space. MongoDB automatically creates file extents to add data to later, which can sometimes make the database seem like it's using more space than it really is. Setting a stepdown window allows us to compact your instance weekly ensuring that the padding factor doesn't grow unchecked. It also allows you to reclaim disk space from deleted documents which MongoDB doesn't give back to the OS natively. You can read more on Mongo's space allocation here: `Why are the files in my data directory larger than the data in my database? <http://docs.mongodb.org/manual/faq/storage/#why-are-the-files-in-my-data-directory-larger-than-the-data-in-my-database>`_"

>> Stepdown Scheduled

>> Stepdown Window (PDT)

>> Enable Weekly Stepdown

>> Enable Weekly Compaction

>External Integration

>> New Relic Monitoring

>> Amazon ACL Sync

>> Rackspace ACL Sync

>Monitoring

>> Instance Storage Usage