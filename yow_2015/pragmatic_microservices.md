# Pragmatic Microservices
## Randy Shoup

* Architecture Evolution
  * eBay - 5th gen
  * Twitter - 3rd gen
  * Amazon - Nth gen
  * All now polyglot microservices
    * Trend is towards microservice once they have larger teams and larger problems
    * But none started that way!
* Principles
  * Solve the problems you have, not the ones you might have in 2 years
  * Solve customer's problems
  * Right tool, right job, right time
* Monolithic
  * Pros
    * Simple at first
    * In-process latencies
    * Single codebase, deploy unit
    * Resource-efficient at small scale
      * 1 machine for monolith
      * 1 machine for database
  * Cons
    * Coordination overhead as team grows
    * Poor enforcement of modularirty (even with good guidelines, no enforcement)
    * Poor scaling (vertical but not horizontal)
    * All-or-nothing deployment
  * Database
    * Pros
      * Simple at first
      * Join queries are easy
      * Transactionsa
      * resource efficient at small scale
    * Cons
      * Coupling over time
      * Performance/scalability bottleneck
      * Hard to tune a database doing *everything* (reads, write, large queries etc)
      * Single point of failure
  * Improving
    * Exploit "natural partitions"
      * e.g. for Ebay: buyers, sellers, for Uber: drivers, customers
      * Internal componentization
    * Continuous Delivery
    * Rapid deployment allows rapid evolution
* Microservices
  * Definition
    * Service-oriented architecture done properly
    * Single purpose
    * Simple, well-defined interface
    * Modular and independent
    * Fullest expression of SE principles of encapsulation and modularity
    * Isolated persistence! (No DB backdoors to other services)
  * Pros
    * Each unit is simple
    * Independent scaling and performance
    * Independent testing and deployment
    * Can optimally tune performance (caching, replication etc)
  * Cons
    * Many cooperating units
    * Network latencies
     * Non-blocking
     * Async
     * Parallel
    * No transactions
      * Difficult to do atomic sets of actions
    * Cross-cutting concerns and refactoring
      * Must deal with several codebases for a singe concept
      * Requires more sophisticated tooling/management
  * Prerequisites
    * Process Maturity
      * CD is an absolute requirement
        * Repeatable deployment pipeline
        * Low-risk, push-button deployment
        * Rapid release cadence
        * Rapid rollback/recovery
    * Automated testing
      * Writing tests + code together (TDD or whatever)
      * Confidence to make risky changes
    * CI for stitching together components on each iteration
    * Organisational Maturity
      * Conway's Law - org constrains architecture
      * Engineer org to have small, independent teams
      * Change the org first
        * Service teams aligned to domains (2-pizza teams)
        * Clear, well- defined area of responsibility
        * Single service or set or related services
        * A given service is managed within one team
        * Cross-functional teams
          * Team has inside it all skill sets needed to do the job
        * Some supporting teams
      * End to end ownership
        * Team owns serviec from design to deployment and retirement
        * No separate maintenance team
        * DevOps: "You build it you run it"
    * Operational Maturity
      * Availability and Reliability as first-order concerns
      * Pets rather than cattle
        * We no longer care about individual machines or instances
        * We only care about the service in the aggregate
      * Monitoring
        * Detailed, end-to-end monitoring of prod systems
        * Need ability to detect and alert on system issues
        * Require ability to do remote runtime diagnosis (no ssh!)
* Decision to re-architect
  * Why?
    * Velocity
      * Time to market - if constrained by coupling, complexity of monolith
      * Teams are interfering with each other and no longer able to develop independently
      * Difficult for new engineers to be productive
    * Scaling
      * Vertical scaling no longer works
      * Parts of the system need to scale at different ratess.
    * Isolation
      * Resource isolation (one component uses all the resources)
      * Fault isolation (avoid co-ordinated failures
    * Deployment
      * Parts need to be deployed independently 
      * Release cadence slow
      * Release to difficult/risky
  * When?
    * Current arch is unsustainable in near term
      * Need fo re-arch outweighs significant investment required
      * Need for architecture outweighs opportunity costs
    * Steady and growing usage
      * It is worthwhile to make the investment
      * Resources available to invest
    * Re-arch should be a sign of success, not failure (due to new plateaus and peaks of success, business)
    * "If you don't end up regretting your early technology decisions, you probably over-engineered"
* How
  * "The only thing a Big Bang migration guarantees is a big *Bang*" - Martin Fowler
  * Steps:
    1. Pilot implementation
      * Choose initial end-to-end vertical experience to migrate / create
      * Provide real customer value
      * Opportunity to learn and adjust
      * Bounded investment and risk
    2. Incremental migration
      * Focus on areas with highest rate of change
      * Prioritise business value - highest ROI areas first
         * Because we already proved it works
      * Maximises our near-term investment
      * Confront and solve hard problems sooner rather than later
    3. New feature deployment in parallel
      * Typically cannot pause all feature work to migrate
    4. Residual Monolith may remain indefinitely
      * Lowest business value
      * Most stable, least changing
  * Can migrate or not - opportunistically
  * Carve off a "seam" of the monolith
  * Wall it off behind an interface
  * Write tests
  * Replace implementation with a service
  * Rinse, repeat
* Building
  * Choose common chassis / framework
    * Easy to build/maintain a service
    * NetflixOSS, GoKit
  * Design Service Interface (Formally!)
    * Propose
    * Discuss with clients
    * Agree
  * Prototype implementation
    * Simplest thing that works
  * Real implemewntations
    * Throw away the prototype!
      * Quicker end-to-end if willing to throw away the prototype
* Interface Stability
  * Backward/forward compatibility of interfaces
    * Can *never* break client's code
    * Often means multiple interface versions
    * Sometimes mutliple deployments
  * Explicit deprecation policy
    * Strong incentive for service team to wean customers off old versions
* Anti-patterns
  * Mega-Service
    * Overly broad area of responsibility
    * Leads to more upstream/downstream dependencies
  * "Leaky Abstraction"
    * Interface reflects *provider's* implementation, not the consumer's model
  * Shared persistence
    * Breaks encapsulation, encourages "backdoor" interface violations
    * Unhealthy and near-invisible coupling
* Persistence options
  1. Operate your own datastore: Store to your own instance of mysql/postgres/mongo etc owned and operated by the service
  2. Use a persistence service: Store to own partition of bigtable etc
