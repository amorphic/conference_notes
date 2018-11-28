# Containerise Everything: Going Cloud Native With Docker
## Ian Crosby

* Rapidly changing, lots of new tech
 * Which tools are relevant, lasting
* Cloud native
 * SOA
  * Nice ideas but too broad
 * Definition
  * Cloud Native Computing Foundation has one
  * WeaveSocks by container solutions is a demo/reference for microservices + cloud native
  * Container Solutions defintion follows...
 * Monoliths
  * New tech doesn't mean everything we did in the past is useless
  * Latency/complication of network
  * Still appropriate in some instances
  * But they suck - full rewrites
 * Need the flexiblity of microservices
  * For all the usual reasons
   * Polyglot
   * Independent
   * Scalable etc
  * Allows us to
   * Scale
   * Replace
   * Optimise
  * Growth in use
   * Technology (cloud, containers etc)
   * Organisation (agile devops, small teams etc)
   * Architecture
* Containers vs VMs
 * Size (MB vs GB
 * Speed (ms vs sec)
* Microservices -> Containers
 * Easy way: 1:1
* Cloud native relies on automation
 * Build
  * Independent (dev laptop, build server)
  * Repeatable 
 * Optimisation
  * 100 lines of code -> 800MB when building due to deps
  * new docker image
   * COPY app /app
   * this is just a go binary
   * Note: docker cp to get binaries from images
  * Repeatble
   * Build
   * Artifact
 * Test
  * API
   * this is the contract the microservice exposes
   * best thing to test
  * Swagger
   * Test container takes swagger spec as input
   * Can test
  * State
   * New containers each time, no leftover state
  * Extend
   * Consumer-driven contracts
   * API versions
 * Deploy
  * Orchestration layer
   * Manual is a headache at best, at worst impossible
   * Lots of tools (Mesos, Kubernetes etc)
   * Scheduling, Discovery, Resourceing etc
* Cloud native is platform agnostic
 * What about AWS?
  * S3, DynamoDB etc
  * So not *really*
 * Most orchestration layers have similar config
  * Good because it's easy 
* Where do containers not fit?
 * Gray area
 * Databases
  * How critical
  * Type of database
  * How often accessed
  * NoSQL databases designed to scale hortizontally
   * Keep adding containers, all works well
   * Ok in containers
  * MySQL etc
   * iHow to do Replication etc?
   * Hold off for now!
 * Applicaiton boundaries
  * Login + Account service
   * Looked separate, turned out being too tightly coupled
   * Merged back together - this is haaaard!
   * DOn't split until you understand the service well!!!
 * Security
  * default approaches ignore security
   * by default running as root 
    * create user, run as that user
    * remove linux capabilities
    * disable ssh daemon
    * best practives - containers are as secure as VMs if best practice followed
* Containers != Docker  
 * LXC, rkt etc
* Cloud Native
 * Relies on Automation
 * Flexibility
 * Resiliency
  * Less control, more failures
  * Handle failures
 * Platform Agnostic
* Persistence
 * flockr clusterhq
  * manage data
  * work out which contaiers need what
 * kubernetes pet sets
  * some level of hosts affinity
  * uber engineering
   * mysql in containers
* Scaling
 * Up is easy
  * Add node 
  * Google container engine does this automagically
 * Down is hard
  * Most customers have static clusters
