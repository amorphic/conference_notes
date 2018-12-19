# Lessons learned building Kubernetes controllers
## Dave Cheney

* Kubernetes overview
    * Replicated Data store; etcd
    * API server; auth, schema validation, CRUD operations, watch
    * Controllers & operators: watch the API server, try to make the world match the contents of the data store
    * Container runtime; e.g. Docker, running containers on individual hosts enrolled with the API server
* Ingress Controller
    * Should take care of the 90% use case for HTTP middleware
        * Traffic consolidation
        * TLS management: presenting certificates
        * Abstract configuration
            * Generic as opposed to Apache vs Nginx vs HAProxy etc
        * Path-based routing
            * Abstract rather than encoding routing within application
            * These routes -> That application
* Contour
    * Envoy
        * A proxy designed for dynamic configuration.
    * Contour is the API server, Envoy is the API client.
        * Contour starts as a blank slate and expects a constantly changing configuration (from Envoy)
        * Kubernetes -> (REST/RPC) -> Contour -> (gRPC) -> Envoy
* Building Software for Kubernetes
    * A kubernetes component should be relatively small.
        * Contour: 28000 LOC
            * 5000 source
            * 15800 tests
            * If it's getting into the 100k's LOC break it up!
    * main.main
        * Keep it as simple as possible
            * Makes testing easier
            * Avoids coupling
        * Parse flags
        * Read config form disk/env
        * Set up connections
        * Set up loggers
        * Call business logic, exit(3) on success
    * Docker
        * Try to avoid the `docker build && docker push` steps in your inner loop
            * NO sequential debugging in docker deployed to kubernetes
        * Cache things
    * Functional Testing
        * Functional tests are terrible + slow
        * Usually attempt to parallelise, but this makes them unstable
        * But there are scenarios that Unit Tests don't cover
        * Need to model the sequence of interactions between Kubernetes and Envoy
            * Not testing:
                * Kubernetes (assume it works)
                * Envoy (assume it works)
            * Pass in kubernetes requests, analyse envoy output.
        * High success rate in reproducing bugs reported in the field.
        * Easy to model failing scenarios (enables TDD).
        * Easy for contributors to add tests.
        * Avoid `docker push && delete` and 5 min lag.
             
