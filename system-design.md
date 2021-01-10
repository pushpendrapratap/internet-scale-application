1. ## back of the envelope calculation:

    - traffic estimates:
        - queries per second (QPS)
        - read/write ratio
    - storage estimates:
        - daily/monthly/annually
    - bandwidth estimates:
        - for write requests: total incoming data x KBps
        - for read requests: total outgoing data y KBps
    - memory estimates:
        - follow 80-20 rule: i.e., 20% data generate 80% traffic
        - therefore focus on memory require to cache those 20% data

2. ## requirements clarification:

    - users/customers
    - scale (read/write ratio)
    - performance:
        - what's expected write-to-read data delay?
        - what's expected p99 latency for read queries?
    - cost

3. ## where we store:

    - how to `scale writes`?
    - how to `scale reads`?
    - how to make both `write` and `reads fast`?
    - how `not to lose data` in case of hardware faults and network partitions?
    - how to achieve `strong consistency`? what are the tradeoffs?
    - how to `recover data` in case of an outage?
    - how to ensure `data security`?
    - how to make it `extensible` for data model changes in the future?
    - where to run (`cloud` vs `on-premises` data centers)?
    - how much money will it all `cost`?

4. ## misc:

    - try to understand whether the given procedure is a one time only operation or if it will be called repeatedly.
    - `bandwidth`: This is the maximum amount of data that can be transferred in a unit of time. It is typically expressed in bits per second (or some similar ways, such as gigabytes per second).
    - `throughput`: Whereas bandwidth is the maximum data that can be transferred in a unit of time, throughput is the actual amount of data that is transferred.
    - `latency`: This is how long it takes data to go from one end to the other. That is, it is the delay between the sender sending information (even a very small chunk of data) and the receiver receiving it.

5. ## load balancer (LB):

    - We can add a Load balancing layer at three places in our system:
        - Between Clients and Application servers
        - Between Application Servers and database servers
        - Between Application Servers and Cache servers

6.
