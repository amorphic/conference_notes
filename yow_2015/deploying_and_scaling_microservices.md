# Deploying and Scaling Microservices
## Saw Newman

* Purpose: Autonomy to allow shipping of functionality more *quickly*
* Independent Deployability
  * Deploying multiple services is error-prone
  * Simplifies other things - no need for complex orchestration (Puppet, Chef etc)
* One Artifact!
  * CI build pipeline - validate a change before it hits prod
    * Rebuilding at each stage is dangerous - not necessarily the same thing at each stage
    * Build artifact once at the beginning and move that thru the pipeline to prod
* What do we want from an artifact?
  * Easy to create
  * Easy to deploy
  * Abstract out the tech stack
  * Good for dev, good for ops
* Artifact Types
  * Tarballs
    * Easy to create
    * Hard to deploy (orchestration)
      * Don't really abstract out the stack
      * Bad for dev and ops
  * Stack-specific
    * nuget, pip, jar
    * designed for reusable libraries, not reusable software
    * Easy to create
    * Not necessarily easy to deploy
    * Bad for ops - needs special platform-specific knowledge
  * OS-specific
    * `sudo apt-get install microservice`
    * os has toolchain for managing these
      * checking versions, authorisation via keys etc
    * Hard to create for devs
    * Easy to deploy (in prod or locally)
    * Abstracts the tech stack (as long as on the same platform)
* Using a Standard Build Process
  * Same build process locally as in pipeline, prod etc
    * Independent deployment of an instance of that service
    * `$ deploy Returns v456 Production` <command> <version> <environment>
    * Same artifact, different topology (via config)
* Deployment Challenges
  * Collissions, side-effects, e.g. dependencies
  * Generally one service per machine/OS
    * Easier to reason about, control, manage
    * But expensive (one VM per instance)
  * Custom Images (eg AWS, VMWare)
    * Images can be large, hard to create and deploy
    * Not easy to deploy - need to talk to the hypervisor, reboot etc
    * Good at abstracting out the tech stack
 * Not so great for Ops
   * fine-grained VMs waste resources in hypervisor, hard to manage
   * ok if images are large (like netflix 32GB minimum)
* Use Docker!
  * Solves problems of custom images
  * Easy-ish to create
  * Easy to deploy
  * Abstract out the tech stack
  * Great for devs, not so great for Ops
    * Great to run entire env on 
    * Hard to run across multiple hosts in prod (because nobody is running entire stack on one machine)
    * Enter Docker Platforms
* Docker platforms
  * Docker Swarm
    * Swarm Manager -> Swarm Nodes (1:M)
    * Same docker command line (70% and growing) - plays nice with rest of Docker
    * Abstraction of deployment across hosts
    * Scheduling strategies
      * Binpack - cram into machines in order
      * Spread - evenly across machines
      * Random - Why?
    * Docker compose yaml file
      * Good for topology of a single service
      * Not so good for dev/production
    * Doesn't rebalance
      * Not maintaining state
      * So need to manually fix 
      * Supposedly fixed in next release
      * Doesn't restart failed containers (can do within the docker engine)
    * Rackspace + O'Reilly using it. Not many others.
  * Mesos
    * Master -> Agents (1:M)
    * Uses "frameworks"
      * which are really plugins
        * Scheduler -> runs on master
        * Executor -> runs on host
      * Marathon is a framework
        * For long-running processes like Docker!
        * Maintains state, e.g. 
        * Custom schedules in whatever language
       * Other frameworks for other things
         * Eremetic - API for short-running containers
         * Apple wrote a custom framework for Siri jobs
       * Great for mixed workloads
    * VERY powerful, lots of features, widely used
      * Orbitz - use marathon for running microservices
    * Fairly complex
    * Lots of moving parts (minimum 9 nodes - 3 zookeeper, 3 master, 3 marathon)
    * Probably needs a higher-level tool for management (no good ones seem to exist yet)
    * Dev: minimesos
 * Kubernetes
   * Works for google, you get a subset
   * API Server -> Kubelet
   * Kubelets deploy pods
     * A colelcitno of tightly coupled containers, running on one node
     * But why? Microservices should be loosely coupled
     * Can attach metadata
     * Can attach *volume* - useful for deploying config etc
   * Service
     * Defines which pods belong to it (not the other way around)
     * Kubernetes organsies wiring them together
     * Service Proxy abstracts the connectivity to the Service (and the pods)
   * Control scale/resources at the pod level
     * But you build services so there is a disconnect
   * Simpler to setup than Mesos but more single purpose
   * Closer to a PAAS
* Summary
  * Use Docker Images as Artifacts
  * Mesos or maybe Kubernetes
  * Platforms are still new
    * Be careful if you're risk averse
    * Keep an eye on cutting edge
  * Service Discovery
    * Kubernetes - metadata (etcd under the hood)
    * Swarm - tags
    * Mesos - already running Zookeeper
      * Orbitz run Console underneath
* Question - Amazon ECS
  *  Harder to set up
  * No self healing
  * No scheduling
  * Can't run yourself
    * Perhaps a swarm plugin?
  * Ok for amazon shops
* Note: always use yaml for config (*not* JSON)!
