# Delivering LiveQueries via LiveServer
## Ondrej Lehecka

> Facebook has been using GraphQL queries to build rich user experience on web and mobile. User interface updated in real time as other users interact with the system plays a key role in driving user engagement. LiveQueries is an API to allow building interactive user interface, update client caches, push updates to the client in the background and more. It allows subscribing to the query result and receive updates as the query result changes.

> LiveServer is a stateful back-end for LiveQueries which interacts with query execution engine and reactive data sources. It uses dependency tracking and query re-execution to send updated query results to the client. It also allows delayed query execution and application of strategies for failed client message deliveries. Client and server is using long living connections and RSocket application protocol to deal with subscriptions, bi-directional streams, flow control and connection resumability.

* LiveQuery
    * Annotated GraphQL
    * get-and-subscribe semantic
    * `query @live {`
        * initial resultset
        * updated results as they change
    * Design
        1. Reactive backend
        2. Delivers updates to client
        3. Stateful
        4. Consistent Routing
    * Key takeaways
        * Stateful service for efficient implementation of LiveQueries
        * Connection-oriented network protocols for long-running subscriptions
        * Reactive Data Sources
* Why?
    * Imagine a network of microservices interacting
    * Hard to create a mechanism to notify on change
* GraphQL Subscription
    * Similar but different
    * Trigger/event in the system
    <F2>* Every time event fired in background, aciton on client
* How?
    1. Client-Side Polling
        * Client can translate @live annotation to mean *"poll with some frequenc"*
        * Simple but inefficient
            * One query can translate to thousands of calls in the backend
            * Wasteful if data changing infrequently
    2. Server-side Polling
        * Server polls with some frequency, pushes updates to clients
        * Doesn't waste client resources but still inefficient
        * Requires long-lived polling
    3. Reactive BAckend
        * Client <-> Stateful GraphQL Server <-> Reactive Data Source
        * Stateful server monitors data source and pushes changes back
        * In microservice environment:

    ```
    Client <-> Stateful Server <-> Reactive Data Store
            v- Stateless Service -^ 
    ```
        * Stateful server contains sesssion info, lifetime etc
        * Possible because GraphQL queries are defined and stored
            * Not general querying (sql)
* Livequery Gateway
    * Tracks data dependencies for queries
    * 
    * Maintains context of active queries
    * Routing
        * Ensures client always talking to same host(s) for caching, performance etc
        * At FB routes you *and your friends* to the same box for caching etc
        * USers are grouped into *"Social Buckets"* for LB, routing etc
* Reactive Extensions
    * For tech that does not have reactive API
    * E.g. SQL database has replication built-in
        * FB create extension that listens to replication log and generates reactivity
    * Can be applied at any level, even caching layers
* RSocket protocol
    * Connectivity
    * Resumability
    * Layered on top of:
        * TCP
        * HTTP
        * Quic
    * Layering
        * Working on Extending HTTP2
        * pub/sub,resumability, credit-based flow control
* Use Cases
    * Current
        * Interactive user interface
        * Updating client caches
        * Push updates to clients in background (user doesn't have to be interacting)
    * Future
        * Delayed Execution
            * Use more compute in off-peak times
            * Pre-compute and cache
* Implementation Challenges
    * Over-observing
        * If client is asking for more data than required (just in case)
        * Now lots more data being tracked, auto-updated, using resource
    * Masked dependencies thru caching layers
        * Multiple layers of caching
        * Can be hard to see through layers to find dependencies
        * Queries not being updated
        * FB can have up to *30* layers of caching(!)
    * Consistency and race conditions
        * Large systems with loose coupling
        * Change may take time to propagate and a fresh view isn't served
    * Partial Reactivity
        * If your data source doesn't already have reactivity
    * Scaling
        * Load balancing
            * *"Social Buckets"*
            * e.g. 1000 out of 1000000 users
            * These all sent to a single host
            * When maxed out
                * Bigger host
                * Re-evaluate grouping
    * Debugging
        * Only option is good tooling
    * Man this is complicated!
* Facebook scale is mindblowing
    * Variety of systems that work together
    * Most use cases are eventually consistent
    * When you need to switch to this level of complexity is a business decision!
