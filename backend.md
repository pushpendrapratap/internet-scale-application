1.  ## communication protocols:

    -   TCP
    -   UDP
    -   HTTP
    -   web-socket (bi-directional communication)
    -   gRPC

2.  ## web servers:

    -   how web server works?
    -   dynamic vs static content
    -   edge web servers
    -   etags and their generation
    -   single threaded (e.g., node servers) or multi-threaded servers (e.g., apache web server)
    -   job of web servers (like Nginx works both as web server and proxy)

3.  ## database engineering:

    -   indexing
    -   ACID (atomicity, consistency, isolation, durability)
    -   relational vs NoSQL
    -   normaliaztion vs de-normalization

4.  ## proxies:

    -   micro-services
    -   proxy, reverse-proxy, caching, TLS termination, load balancer, layer 7/4/3 proxy
    -   basically anything that make requests behalf of client or anything that receives a request and make that request to oter servers that hide the identity of the original client or hides the identity of destination servers.
    -   service meshes (proxy and reverse-proxy)

5.  ## caching:

    -   in memory caching
    -   expire cache

6.  ## web frameworks runtime:

    -   helpful in building web api (e.g., django, node)

7.  ## messaging systems:

    -   important when there are systems communicating with other systems rather than a client specifically
    -   queue (kafka, rabbitmq)
    -   pub-sub system

8.  ## message format:

    -   JSON, XML, protobuf (often used in high bandwidth messages)

9.  ## security:
    -   encrytion
    -   TLS (transport layer security): how do you communicate between one node and the other node, so that the communication will be secured, or you can stop man in the middle attack
    -   saving credentials
    -   firewalls (check which port to open or close)
    -   network security
