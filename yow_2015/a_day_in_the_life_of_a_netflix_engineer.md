# A Day in the Life of a Netflix Engineer
## Dave Hahn

* The Netflix Goal: Win Moments of Truth
  * When a family has time to use, they use that moment of truth to watch Netflix 
  * All engineering is aimed at this goal
  * Supported by
    * Finding and creating great content
    * Working out how people find content
      * LoLoM - List of List of Movies they think people might like
      * Try change arrangement of things on screen
        * E.g. change an entire LoLoM row to a cinematic and measure engagement
        * Kids: relate to characters rather than specific shows
          * Tried organising by char vs show, worked, now this is default for kids 
      * Enormous A/B infra to test 
      * Average user passes thru 13 tests
* People
  * 50 teams, 800 engineers, 2000 staff
  * Culture
    * Velocity of Innovation
    * Know that things will occasionally break
    * Accept this as a tradeoff for innovation
  * Freedom & Responsibility
    * Give smart people the freedom to build things how they want to
    * This makes people take responsibility
  * Engineer-Driven Organization
    * No top-down
    * Engineers organise themselves
  * Continuity
    * Things are owned by *teams* and not individuals so no "big red bus" problems
    * Teams are trusted
    * Microservices are small and can be replaced relatively easily if the team doesn't want to support.
  * DevOps
    * 100% ownership culture
      * Design
      * Deploy
      * Support
      * No 'throw it over the fence'
      * On Call 24x7
      * Insight
      * Repair and remediate
    * Don't have:
      * Centralised NOC
      * Single architect
      * Production release crucible
      * Layers of management
        * Management do things *for* engineers, not *to* engineers
      * Formal Processes
      * "You can't do that"
        * No release schedules, rules
        * Get out of their way, help them release as safely and quickly as possible
* Infrastrucutre
  * No data centres
    * They used to. One caught on fire.
    * Realised goal is not to be really good at building world-class datacentres (see Goal above)
  * Open Connect CDN - used for all streaming
    * Why build a CDN?
      * Different goal to commercial CDNs whose goal is to make money as a CDN
      * As part of Netflix' Goal they must get bits to users asap
    * Embedded with ISP where possible, otherwise peered
    * FreeBSD, nginx, bird
    * Hardware profiles
      * 240TB 4U disk - "older" content
      * 10TB 1U SSD - "hot" recent content
      * 40GB NICs, 1000GB NICs coming online
    * openconnect.netflix.com
  * AWS - everything else
    * Mutliple locations, seamless transition
     * Proxies redirect traffic in moments of load
     * DNS records redirect around faults
     * Steady state monitored by Flux - this looks fscking awesome
    * Undifferentiated Heavy Lifting
      * AWS provides *lots* of services
      * Netflix doesn't have to care about building things like messaging etc
      * Focus obsessively about Moments of Truth instead (see Goal above)
    * Practice switching over all the time - redistribute global traffic
      * Test regularly so they can trust it to switch automatically and not require support calls (yay!) 
* Easy Ownership
  * Don't make frameworks, processes, rules
    * Given freedom, people will make their own frameworks, processes, rules which work for them
* Interconnection
  * Everything done with discovery in a standard way ("Eureka")
  * Solid network communication
    * How to do it when you own none of the infra? Coz this is scary...
      * "Ribbon"
        * Local method call that makes connection to "Eurkea" service in a standard way
      * "Hystrix"
        * Determine what's normal performance
        * Report when outside normal
        * Gracefully degrade if possible (if service unavailable - try a lesser equivalent service)
        * Happens on per-callpath basis automatically
* Continuous Deployment
  * Spinnaker 
    * Appy thing into Cloudy thing
    * Pipeline
      * New commit -> Package -> Test (canary, smoke test etc) -> Production
    * Service status
  * Data persistence as a service
    * For all types of storage 
      * Astyanax - cassandra
  * Insight
    * Metrics
      * Must be fast and reliable
    * Atlas
      * Big and fast for volume of netflix metrics (2.5bil/min) - most complex query takes 4 sec
      * Easy to discover metrics
      * Not focussed on building dashboard
    * Importantance of intelligence
      * No fixed thresholds (impossible to accurately determine, maintain)
      * Performance predictors
        * Make it easy for Service Owner to choose action to perform if performance predictor violated (log, send alert etc)
      * Own the service! Set up your own alerts!
  * Introspecting services
    * Slalom
  * Vector
    * Shows code vs System metrics
  * Flame graphs
* Ops Team
  * Tooling - things like spinnaker
  * Insight - things like atlas
  * Production Network Engineering
  * Peformance Engineering
    * Tuning OS
    * Applications
    * Language experts to help people with performance etc
    * Tools like Slalom
  * Traffic & Chaos
    * Traffic Management
    * Failure injection - to test what survives
    * Simian Army
      * Take out random pieces of infra
      * Check that stuff survives
    * Find ways to break things
  * CORE - when top-end metrics waver
    * Crisis management
    * Blameless reviews
    * Reliability best practices
    * Avail reporting
    * Partner Engagement
    * Goals
      * Protect customer experience
      * Look for unique failures - fuckups caused by bad tooling etc
    * General focus is Context not Control
      * However this is suspended in a crisis - just get it working!
