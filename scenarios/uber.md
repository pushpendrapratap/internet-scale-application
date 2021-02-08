1. features:

    - ride booking
    - nearby cabs
    - ETA of driver
    - upfront fair
    - see current location
    - ETA till destination
    - pool
    - car type
    - payment

2. marketplace:

    - riders: demand -> doing reading -> for scaling reads, do replication
    - drivers: supply -> writing -> for scaling writes, do sharding
    - uber has to know the location of both of these.
    - a service, mapping gps-location to cell-id
    -

3. quad tree data-structure (we are dividing a globe into rectangle, that's why quad):

    - https://eng.uber.com/h3/
    -

4. kafka: it decouples the place where message is being generated and message is being consumed

5. architecture (main components):

    - cell-id mapping with driver
    - long-poll or web-socket connection (need duplex connection between drivers & servers and riders & servers)
    - hence, app server will be stateful i.e., all request froma particular driver-id will go to a specific app server
    - consistent hashing
    -

6. driver client (write) -> LB/Gateway -> app server (persistent connection) -> ring (mapping of driver to cell-id, add/delete request, it uses consistent hashing) ->

    rider client (read) -> LB/Gateway -> very similar to above but with some different logic
