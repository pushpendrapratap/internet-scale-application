1.  ## Eventual Consistency:

    -   eventual delivery: eventually, every op seen by every node. it will be asynchronus i.e., may deliver in any order.
    -   convergence: seen same ops => have same state
    -   don't lose data
    -   https://www.youtube.com/watch?v=yCcWpzY8dIA&ab_channel=GOTOConferences
    -

2.  ## [Latency Numbers Every Programmer Should Know](https://colin-scott.github.io/personal_website/research/interactive_latency.html):

    -   CPU: cpu operation -> 0.4ns
    -   MEMORY: memory reference -> 100ns
    -   STORAGE: random read from ssd -> 16μs
    -   NETWORK: round trip for data from EU to US -> 150ms

3.
