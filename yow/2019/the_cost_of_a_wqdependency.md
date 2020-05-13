# The Cost of a Dependency

* How long will your codebase:
    * be used
    * be maintained
    * have support for its dependencies
* How does a project end up slow and hard to change?
    * Single repo
        * Feature coupling
        * Gui, Server, Framework, Datastore
        * Breaks down on in build and IDE:
            * Need to build/test/package everything on every change
        * You never feel like you're in a corner of the system
            * More like a warehouse with dependencies all over
        * Consequences
            * Cognitive overload
            * Build times increase
            * Less responsibilities
        * Questions
            * Who defines requirements and budget
            * Can this progression continue?
    * Interfaces
        * Injecting
            * Have to start implementing logic locally
        * Depending on external API
            * But API still in external package - it's someone else's abstraction
                * Assumes that you understand the cost of the dependency
            * Non-linear growth
            * Incur the cost of transient dependencies
                * Deep layering effect
                    * My app has 3 deps
                    * Each of those have 3 deps
                    * Already 13 deps
            * Deep call stacks
                * Huge cognitive load
                * Where do logging, instrumentation, metrics go?
            * Consequences
                * Build times
                * Test times
                * Lack of ownership
            * Compensating behaviour
                * Magic build scripts (if this then that)
                    * Usually only understood by a few
                * Using the real IoC Container in tests
* It it changes together, it lives together
    * Repos by feature responsibility
        * Feature A
        * Feature B
        * GUI Lib
        * Comms Lib
        * Persistence Lib
    * Repos by business domain
        * Loose coupleing, high cohesion
    * Forces interactions to be explicit
* Private by default
    * Aim for encapsulation
    * Rule of 3
    * Reuse is an evolution
* Plan of action
    * Move away from deep layers
        * GUI
        * App
        * Domain
        * Framework
        * Data Access
        * Data Store
    * Do composition instead
        * Adapter layers
        * Hexagonal architecture
        * Similar to Kubernetes Sidecar model
        * Feature A can change tech without impacting Feature B
    * Domain model *defines interfaces/contracts for everything it needs*
* Results
    * Encapsulation
        * Reduced cognitive load
        * Less busy work
        * Less onboarding friction
        * Greater technical freedom
            * To upgrade versions
            * To change tech
        * Snip rule
    * Inversion of Dependencies / Port and Adapters
        * Focussed code
        * Fast tests
        * Shallow stacks
        * Technical freedom
        * The baggage is obvious and easy to delete
    * Fixes are fractal. Work at all levels:
        * Repo
        * Package
        * API
* Books
    * Implementing Domain Driven Design
    * Good Enough Software
    * Hexagonal Architecture
