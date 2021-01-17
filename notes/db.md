"To compare databases, it’s helpful to understand the use case in great detail and define the current and anticipated variables, such as:
* Schema and record sizes
* Number of clients
* Types of queries and access patterns
* Rates of the read and write queries
Expected changes in any of these variables
Knowing these variables can help to answer the following questions:
* Does the database support the required queries?
* Is this database able to handle the amount of data we’re planning to store?
* How many read and write operations can a single node handle?
* How many nodes should the system have?
* How do we expand the cluster given the expected growth rate?
* What is the maintenance process?
"

Excerpt From: Alex  Petrov. “Database Internals”. Apple Books. 


- hot shards
- replication (to combat bandwidth issue)
- shards (to avoid heavy data storage)
- one shard can also be replicated multiple times, if the load is heavy on that particular shard
- write through cache: i.e., you are writing to both cache and db
- global cache: cache invalidation: TTL (time to live) associated with all the keys which are in cache
- this cache will be associated with the application server. so if the app server dies, cache will die. Also it will make the system statefull rather than stateless. If the throughput on the system is very high but the amount of data to be cahced is low, I can use in-memory cache (e.g, goolge's guava). Also, cache will not be pre-populated in the cache, for this cache.	
- client -> DNS -> LB -> app server -> DB
				|-> cache
- redis is not in-memory cache, it's global cache 
- redis runs as a diff. service
- application cache runs in a same machine (e.g., JVM)
- intruduce caching in LB (it's a kind of specialize application server and does following tasks: routing + queuing + caching): 
	- API gateway
	- varnish
	- tradeoff: consistency (only way to invalidate cache is via TTL)
	e.g., key: netflix.com/home?username=abc_123_xyz, value: <html>, json, etc.
- CDN for caching
- total invalidation time = TTL(CDN) + TTL(LB)
- client cache: browser, mobile, etc.
	- TTL
	- cache control header: etag header, LMS (last modified since), etc.
	- etag: hash (md5, etc.) of image/text, etc. this way we are saving bytes
- OTT (over the top) apps:
	three kind of trays:
	- editorial (e.g., amazon/netflix originals, new movies/serials): same for every user 
		- ott.com/editorial
		- TTL(24 hrs.)
	- recommendation: group specific 
		- ott.com/recommended/category_id: this way we have less key, val pair to store in DB and this way it can also fit in one server
	- continue watching: user specific
		- ott.com/watch?user_id:
		- ML model will pre-populate the recommendations in db or cache (e.g., ML model runs every 6 hrs.) rather than real time inference
		- TTL depends on how frequently ML model is running
		- S3 filestore: stores data like, click-stream
		- cache, and good idea is to replicate it but sharding depends on no. of users and the kind of info you have
- clickstream system:
	- track user actions
	- % of whole movie watched
	- open for extension (i.e., business team can come and ask any kind of questions)
	- ingest -> store data (queuing/kafka) -> extract information -> transform -> save (DB)
	- netflix case study:
		- watch time: 300s (iOS)
		- watch time: 5mins. (Android)
		- client SDK: (REST/RPC): 
			- To solve data sanity problem, convert both watch time to same format via client SDK
			- throughput issue: 1000 events/s:
				- micro-batching: use queue. And after every 10s (configurable) or set on queue size or both, flush the queue to backend
			- Retries: every x sec., or with exponential back-off
	-  
