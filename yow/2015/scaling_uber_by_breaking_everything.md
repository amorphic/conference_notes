* Scaling Uber by Breaking Everyhting
** Matt Ranney

* As of Dec 2015
 * 5k+ employees
 * 1.5k+ Engineers
 * Jan-Oct 2015 paid out AU$4.8B to drivers
* Why so many engineers?
 * Lots of locations
  * Lots of locale-specific
 * Must be available
  * Unlike FB, Twitter etc which you just use whenever
  * When you're using Uber, you want to use it immediately
  * If Uber doesn't work the instant you need it, you'll go elsewhere and the transaction is lost
  * So optimisation, reliability is very valuable as each transaction has financial value
* Tech at Uber is relatively new
 * Not a lot of institutional knolwedge
 * Making it up as they go
 * So much software being written to do so many important things (like arrange transport)
 * We should be doing things better
 * But growth is not slowing, it is accelerating
  * New products
  * New features on existing products
  * No time
 * Originally 100% outsourced
  * More important was the business side - regulation etc
  * Only brought in-house
 * History
  * 2011
   * dispatch Node.JS/MongoDB
   * API - Python/SQLAlchemy/MySQL
  * 2012
   * Dispatch swap MongoDB for Redis (needs to be fast so in memory)
   * Dispatch adds ON data access layer because SQLAlchemy struggoing
  * 2013
   * First non-API Python services
   * API switched to Postgres - unsuccessfuly, less performant
  * 2014
   * New Python service use MySQL - but this is struggling
   * Schmaless begins, must finish before NYE because Postgres will collapse
   * First Schemaless - trips out of Postgres
   2015
   * Dispatch Schemaless/Riak
* Tech Debt
 * Tried to make responsible choices with proven technology - mysql etc
 * Built datacentres - thought they were doing the right thing
 * But cumulative failures mean now that something is *always* breaking
 * Microservice growth: ~700 now
 * Simian Army + Chaos Engineering is a great thing
  * Turbulence and chaos is the norm now. There is no avoiding it.
  * Uber built UDestroy to simulate faults
   * Couldn't use Simina Army as it's AWS-centric
  * Engineers don't like Failure Testing
   * *Especially* not with Databases
    * Hard to test because of replication partners
     * Side note: master/slave is a bad metaphor, as are:
      * leader/follower
      * primary/secondary
     * Instead use:
      * queen/princess?
      * usa/canada?
      * australia/nz?
* Worst outage ever
 1. API postgres outage for 16 hours
 2. Master log replication to S3 failed, logs backed up on master
 3. Alerts -> Engineer but ignored
 4. Disk fills up
 5. Engineer deletes unarchived WAL files, so postgres qon't restart
 6. Error in config prevents slave promotion
 7. WAL file corrupted in transfer, other slaves unavailable.
 8. Find a slave to promote - will take 8 hours.
 9. Consultants prpose to write a _C program_ to bypass the corrupted WAL. Postgres starts
 10. Network outage to backup datacentres
 * Lessons learned
  * *Use very meangingful alert names*
   * "The postgres master is running out of space" rather than a generic postgres alert
  * Use derivative 
  * Make *lots* of copies of critical data
  * Practice failure scenarios
  * Special nodes are a bad idea
   * Cassandra, Riak - no 'special' nodes
   * Makes it easier to test failure because you can pull random nodes
  * Things like replication should be part of database internals
  * Amazon: "Even the slightest ourage has signifcant financial consequences and impacts customer trust"
   * This is increasingly true because everything is online now.
* Riak latency failure
 * Riak immediately masked the problem and dealt with it
 * ...until it was really bad
 * Clients confounded the problem
 * Lessons learned
  * Crash Only would be nice
   * Nodes just die, no gradual degradation
   * Retries
  * Latency
   * Overall latency >= latency of slowest component
   * Google: "Achieveing Rapid Repsonse Times in Online Systems"
    * Send a request to multiple services
     * Service A first
     * Service B second with a 5ms delay
    * If Service A handles, tells Service B to ignore (doesn't waste resources)
    * But otherwise the max delay is only 5ms!
   * Uber Partner App keeps a state digest
    * In case of failover, client can push state of running trip to new Dispatch service
* Human Error
 * Mostly the cause of all issues
 * Break everything - the humans will eventually so you might as well do it in advance 
* Embrace the Chaos
 * Engineers steer towards Consistence + Partition Tolerance
  * Because they don't liek the idea of "lying" to users
  * But users probably prefer Availability - they'd rather have an "almost right" system than no system
