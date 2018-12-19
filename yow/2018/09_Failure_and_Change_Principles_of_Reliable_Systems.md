# Failure and Change: Principles of Reliable Systems
## Mark Hibberd

* Reliability: The quality of performing consistently well
    * The goals are clear
    * The path is less obvious
* Service
    * P[failure] = 0.1 or 10%
    * 10 x intances gives redundancy but requires us to embrace failure
        * Total failure probability of 0.1^10 (0.0000000001%)
        * Individual failure probability of 0.9^10 (65%)
    * Architecure provides the opportunity for tradeoffs
* Designing a reliable system
    * Chess System example
        * Pair Players
        * Games Play
        * History
        * Analyse Games
        * Play Engines
    * Monolithic
        * No risk of failure due to interactions failing
        * Increase cost of individual failure potentially taking all servies down
        * Removes independence
    * Service
        * Naive aproach
            * Look at Nouns: "Player,", "Game"
            * "Game" might have states such as "in play" etc
                * This makes the Game service essential to the other services
                * Entity Service Pattern: Don't do this!
            * We have all of the downsides of a monolith with the new problem of network connectivity.
        * Better approach
            * Get away 
            * Games as a *value* instead of a *service*
            * Game passed to other services: Pair, Play, Engine, Analyse, History
            * Pairing Service
                * Looking for shared game identifier
                * Players have game requirements
                * Pairing service can 
                * How independent is this service?
                    * What does it know? About players waiting for a game
                    * WHat is it Told? When a new player wants to pair
                    * Ask: Nothing
                    * REsponse: Vends players who are connected
            * Playing Servce
                * Knows: Games in play
                * Told What a player makes a move
                * Asks: Nothing
                * Returns: Completed Game
            * Analyse/History
                * Finished games can be passed off to these
                * Separate out from play service (which only needs 
                * Gives out game values
                * Knows: How to return/analyse games
                * Told: Completed Game values
                * Asks: Nothing
                * Response: complete game values
            * Never have services that have to ask for things or update state!
            * Independent responsiblities over shared nouns
                * Our verbs are the services!
* Operating Systems
    * 8 Fallacies of Distributed Computing
        * A slow call is worse than a bad call - use timeouts!
    * Scaling services
        * 7 instances
            * 14% to each instance
            * Single failure means 15% increase to each instance - this goes up quickly!
        * Once one services fails, other services will probably fail
        * Techniques
            * If an instance can only handle X, don't send it 2X 
            * Tapering limits
            * Backoff
    * Health Checks
        * Cascading checks
            * If a parent service health check is coupled to a child it will declare failure when it could continue working
    * Involve the users
        * Graceful degradation is required
            * Features go all the way back to the UI
                * Features disappear so they can no longer be clicked
                * API calls return less information
* Changing Systems
    * Deploying new versions
        * Version N+1 running alongside Version N
        * The chance of all N+1 nodes failing is high (bugs etc)
        * Need to phase 
    * In-prod testing
        * N reads/writes from prod datastore
        * N+1 reads from prod datastore but writes to test datastore
        * Test results are as expected
        * Sync?
    * Phased migration
        * 5% of traffic to N+1
        * Run tests
        * Slowly increase load
            * Continue
            * Roll back
    * Could your system survive shipping a bad line of code?
* Data and code needs to have an independent lifecycle
    * E.g. Upgrading a deployment system
        * Usually maintains state on filesystem: requires code and data to migrate at the same time
    * E.g. Kubernetes
        * Redundancy inside the cluster
        * But only a single cluster!
            * Requires a big, scary change when cluster needs to change
* Constructing reliable systems from unreliable parts
    * E.g. an unreliable library that fails and corrupts data
        * Create a proxy to take control of interactions
        * Wrap service in a http service that logs input
        * When the library corrupts data, replay the logs
* The goal
    * "A beach house isn't just real estate, it's a state of mind".
    * You want to know that things will fail but you won't get called.

