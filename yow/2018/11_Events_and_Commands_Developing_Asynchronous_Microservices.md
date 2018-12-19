# Events and Commands: Developing Asynchronous Microservices
## Chris Richardson

* Microservices enable continuous delivery
    * Proces: Continuous Deployment / Delivery
    * Org: Small (2 pizza) teams
    * Arch: Microservice
    * Loosely coupled services, loosely coupled teams
* Architecture
    * Separate datastores essential for loose coupling
    * API Gateway -> Customer Service
                  -> Order Service
    * Seem standalone on the surface but they need to talk to one another
        * No ACID transactions to ensure entire transaction committed
        * FROM ORDERS... FROM CUSTOMERS... can't happen
    * Simple queries to find orders by customer are impossible
* Saga
    * A series of local transactions in each service.
    * https://microservices.io/patterns/saga
    * createOrder()
        * Order Service: createOrder()
        * Customer Service: reserveCredit()
        * Order Service: finaliseOrder()
    * Often initiated by a REST call
        * But if the saga is async we can't reply to say whether or not order was successful
            * Can only ask to come back later
    * Rollback
        * Hard - "compensating transactions"
    * ACD (no "I")
        * Sagas are interleaved -> anomalies such as lost updates
        * Must use countermeasures (i.e. order is flagged as "pending", then flagged as "complete")
    * Communication between saga participants
        * REST
            * Synchronous, temporal coupling
            * No guaranteed retry from client
        * Async
            * Services communicate via a message broker
                * "At least once" delivery
                * Kafka, MQ etc
            * Messages must be ordered
            * Service updates datastore and then publishes event
                * How to make these two events atomic?
    * How to sequence?
        * Choreography
            * Distributed decision making
            * Benefits
                * Simple
                * Participants loosely coupled
                * "Event-focussed" business logic
            * Drawbacks
                * Cyclic deps: services listen to *each other's* events
                * Overloads domain objects
                    * e.g. Orders need to know about Customers and vice versa
                * Events are an indirect way to make things happen
            * Works better in simple scenarios
        * Orchestrated
            * Centralised decision making
            * Persistent object that implements a state machine which tracks messages and invokes participants
            * On create:
                * Invokes a saga participant
                * Persists state in DB
                * Wait for reply
            * Messages are not *events* they are *commands* e.g. `reserveCredit`
                * Command messages and Reply messages instead of just Events
            * Benefits
                * Centralised coordination logic is easier to understand
                * Reduce coupling: e.g. Customer Serice knows less: simply has API for managing available credit
                * Reduces cyclic dependencies
            * Drawbacks
                * Risk of smart sagas directing dumb services
                    * Just don't do it
            * Works better in more complex scenarios
            * Likely requires a framework
* Database Updates
    * How to perform atomic transaction without 2-phase commit?
    * Approaches
        * Event Sourcing
            * Event-centric approach
            * Business logic implemented in terms of domain events
            * Persist *events* to database
                * No separate order table, just an events table of different type
                * Query by primary key, apply events in order
                * Every event guaranteed to be published
                * Allows for:
                    * Temporal queries to see the state at any given time
                    * Retroactive correction
                    * Auditing
                * Challenges:
                    * Unfamiliar model
                    * Evoloving the schema is hard (no migrations)
                    * Event store only supports PK-based access (no queries by other fields)
                    * Good fit for choreography but not for orchestration
        * Publishing "database update" messages
            * Messages got to an "updates" tables
            * Tail DB logs for updates table and publish to message broker
            * Or regularly poll updates table for updates
* Database Queries
    * API Composition: Inefficient
    * Command Query Responsibility Segregation
        * Use separate data models for COmmands and Queries
            * Keep them sync'd via events
        * Denormalise
        * Maintain a read-only replica designed specifically for a group of queries
        * Kept up-to-date by ievents form the services that own the data
        * `Request -> Service A -> Database (Event) -> Message Broker -> Service B -> Alt. Datastore <- Service B <- Request`
* Takeaways
    * Use syncronous protocoals
        * External APIs
        * API composition
    * Use async messaging
        * To publish events between services
    * Read: Microservices Patterns https://learn.microservices.io
        * 40% off: ctwyowconf18
