# The Next Generation of Microservices
## Phil Calçado

> How are microservices in 2017 different from how we used to build them at the beginning of the decade?
> More traditional Service-Oriented Architectures were defined by protocols and standards published and curated by industry consortiums. Knowledge of the architectural style usually called "microservices", on the other hand, is often in the form of patterns, cautionary tales, and tools extracted from real-world reports and software made available by organisations that have adopted this style.
> Almost ten years since the first wave of such reports, the landscape has changed considerably. Many hard challenges from the past have been eased or completely solved, and a lot of the custom software created by the microservices pioneers have been made off-the-shelf open source software.
> In this talk, Phil Calçado will contrast what we first found in the first generation of microservices architectures against the current generation's landscape. Let's talk about which previous common knowledge and patterns are deprecated, which ones are still active, and introduce some of the ones that have been recently added to our toolbox.

* Microservices
    * Highly Distributed Application Architecture
    * Challenges
        * Organisational
            * Resource Management
            * [Calçado's Microservices Prerequisites](http://philcalcado.com/2017/06/11/calcados_microservices_prerequisites.html)
        * Technical
            * Complexity
            * [8 Fallacies of Distributed Computing](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)
    * ~2013 Microservices was the solution to all problems
    * Good book on patterns: [Release It!](https://pragprog.com/book/mnee/release-it)
* Handling Temporary Failure
    * Pattern: Circuit breakers and timeouts (try, wait, try again) circa 2013
        * Works by assuming client will back off and give the server breathing space
        * Breaks down with multiple, unrelated clients implementing the same pattern
            * Fix by adding shared state
            * Only 3 reasons to use Zookeeper
                1. You worked at Twitter and you can't let go
                2. If you want to use do shared state (cool kids using consul now)
                3. Kafka
            * But how to know which instances are healthy?
                * Client side service discovery
        * You need to do this for every service!
           * All of the overhead *just* for RPC reliability
            * There are many other aspects of microservice architecture that need similar
        * Popularised by conference speakers at large companies
            * Wanting to look interesting to attract talent
            * Hard to implement because *they have huge teams to do all of this*
    * Circa 2015 a lot of these patterns had been turned into open-source products
        * Forces people to implement libraries
            * Means new library version need to be pushed out
                * Security fixes etc
                * Monorepo doesn't solve this problem
                    * Irregular deployments
        * Why not push the business logic to the platform (instead of vice-versa)?
            * Can't add to the TCP/IP stack
            * Use sidecar
                * Like a proxy handling inbound and outbound traffic
                * Self-contained
                * Deployed alongside business logic
                * Separate team can manage the sidecar and deploy it separately
    * 2017 - Kubernetes
        * Kubernetes "won"
        * Can controls the network layer acting as a proxy
            * The network becomes a piece of software that we can control
        * Pattern: Service Mesh
        * Push the copy-paste service/network management down the stack
            * No copy/paste
            * No library management
        * Allows you to pretend some of the fallacies are actually true:
            1. The network is reliable
            2. The network is secure (internal HTTPS everywhere)
            3. Topology doesn't Change
        * The patterns still apply
            * But the *dumb work* is pushed down the stack
* Service Mesh
    * Works better with metadata-rich protocols
    * New optimised protocols are quite opaque
        * Binary, compiled, lacking metadata
        * gRPC and friends
        * HTTP proxy doesn't know what to do
    * Coupled to the platform
        * Harder to fully replicate production in dev environment
        * Modern service mesh is lightweight but still hard to deploy locally (kubernetes!)
    * Leaky Abstraction
        * Not everythings will be part of the mesh
        * Network still isn't homogenous
