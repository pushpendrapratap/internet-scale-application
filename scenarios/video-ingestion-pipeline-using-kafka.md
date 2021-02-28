1. kafka: push messages to downstream services

    publisher -> broker -> subscriber

    producer -> topic -> consumer

2. app -> kafka -> redis/mysql/mongodb/elasticsearch/app2

3. cluster: group of brokers

    size: # of brokers in the cluster

    cluster_id, broker_id

4. zookeeper: do health check, naming and membership, configuration, leader

    producer -> zookeeper/leader <-- `communicate using gossip protocol` --> node1/node2

5. topics: basically it's a binary file on OS

    topics partitions: to increase the data storage capability and also the throughput of the system

    topic --> one-to-many -> partitions

6. RAFT: for leader election process

7. producer:

    - serializer
    - config
    - key
    - msg
        - partition
        - timestamp
        - key
        - value
        - topic

8. routing strategies:

    - direct
    - round-robin
    - key-hash (consistent hashing)
    - custom

9. consumer:
    - deserializer
    - pointer: offset
        - lco (last commited offset)
        - cp (current position)
        - log end

10 producer --> one-to-many --> consumer

11. queue: message published once, consumed once

    pub sub: message published once, consumed many times

    kafka: do both of these using 'consumer group'

12. each partition has to be consumed by exactly one and only one consumer, however you can have one consumer consuming single/multiple partitions and consumer group lets you do this.
