1. Enities:

    - user (not every user will have a profile e.g., some merchants etc.)
        - id
        - phone no.
        - salt (useful in preventing rainbow table attack)
        - password (hashed using SHA256/bcrypt) <- hash(password + salt)
    - payment mode
        - UPI
        - credit card
        - debit card
        - netbanking
    - role
        - id
        - name
        - description
    - trxn
        - date (some dates will depend on the trxn status)
        - id
        - amount
        - source
        - destination
        - currency
        - remarks
        - billing address
    - trxn status
        - id
        - timestamp
    - profile
        - full name
        - address
        - pic
        - dob

2. RBAC (role based access control):

    - account roles:
        - normal
        - merchant
        - admin
    - role (ENUM type maybe)
    - permission (for fine grained access)

3. enum:

    - expensive to change
    - efficient
    - compiler can check

    db entry:

    - easy to change
    - high latency
    - late validation

4. trxn status (main class):

    - failed (ENUM type subclass)
        - reason
    - success (ENUM type subclass)
    - refund (ENUM type subclass)
        - reason
        - to
    - pending (ENUM type subclass)
        - last checked

5. ORM:

    - all abstractions are leaky.
    - might have to write custom queries and do indexing, simple orm might not help

6. If an attribute (column) is multi-valued then treat it as an entity/table

7. user-prfile relationship:

    - 1..1
        - if one owns other, put one into other (other is the dependent one e.g., `profile` in this case) as fk
        - else create a mapping table
            - user_id -> NOT NULL, UNIQUE
            - profile_id -> NOT NULL, UNIQUE
            - (user_id, profile_id) -> composite pk
    - 1..m
    - m..1
    - m..m

8. indicies:

    - read fast
    - write slow
    - apply indexing on fk

9. `user` owns the `profile` i.e., if user gets deletd then so does its profile.
10. `trxn` owns `trxn status`
11. if there is no ownership between two entities, create a separate mapping table for them else put either of them (based on usecase) in other as fk (foreign key)
