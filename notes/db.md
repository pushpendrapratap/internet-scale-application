1. "To compare databases, it’s helpful to understand the use case in great detail and define the current and anticipated variables, such as:

    - Schema and record sizes
    - Number of clients
    - Types of queries and access patterns
    - Rates of the read and write queries
      Expected changes in any of these variables
      Knowing these variables can help to answer the following questions:
    - Does the database support the required queries?
    - Is this database able to handle the amount of data we’re planning to store?
    - How many read and write operations can a single node handle?
    - How many nodes should the system have?
    - How do we expand the cluster given the expected growth rate?
    - What is the maintenance process?"

    Excerpt From: Alex Petrov. “Database Internals”. Apple Books.

2.
