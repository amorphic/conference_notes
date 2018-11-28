# Facebook Product Infrastructure
##Adan Wolff

* Product Infrastructure
  * Ideas + Approach
* Product has various Views (e.g. Facebook)
  * Customers
    * Plebs
    * Advertisers
    * Mobile etc
  * Operational view
  * Business view
* Move fast and break things
  * Don't limit change
  * Focus on infrastructure which finds problems and makes them easy to fix
  * Hacker Process
    * Build -> Increase Audience -> Ship
    * <- Gather Data !!! (oft forgotten)
  * Iteration speed is the determining factor of product success
    * But without sacrificing performance
* Release engineering
  * Facebook release cycle:
    * Master: 1 week
    * Release:
      * 4 days of stabilization
      * 3 days of SOAK/dogfooding
      * Release!
    * Strive to make the cost of missing release as low as possible
    * CI would be nice!
  * Feature gating
    * Every change should be being a gate, e.g. using a feature flag:
      ```
      if (gk_check('64bit_rollout') {
        init_64();
      } else {
        init();
      }
      ```
    * Separate interface for feature gatekeeper:
      * Add restraints to rollout change to just:
        * particular demographics
        * particular internal teams
        * everyone
    * Metrics interface to show change from control (a/b):
      * sessions: +/- %
      * time spent: +/- %
* Easy to add code, not easy to remove
  * FB lets it grow
  * FB measures carefully, knows if things are working
  * Dev time is almost always better spent building
  * Removing code ends up being a bigger job - touches lots of things
  * Code has more business value being left alone vs time to remove
* Beyond iterative
  * Sometimes must take great leaps across the map into unknown territory
* Infrastructure
  * This is an abstract idea rather than implementation
    * e.g. aquaduct - idea is to 'move water' but there are many implementations
  * A projection forward in time
    * Where we want to be: 'we want to have water over here from over there'
    * But hard to predict: lead in pipes caused harm
  * SQL idea of update/delete
    * How to replicate the change or absence of something in a stream?
    * Look at kafka
    * REST
      * Problem getting all fields when we don't need them
      * Problem of getting list of ids, then full details
      * GraphQL replacing this with graph DB idea
  * MVC
    * Separate abstract information from how you display it
    * Stateful entities on both sides: model and view, controller trying to tie it together
    * React -> pure transformation between model and view
      * Flux: Aciton -> Dispatcher -> Store -> View -> Action (.\*) -> Dispatcher (single event emitter which diffs and updates the view)
      * Streams are powerful 
* Cognitive approach to software design
  * Cartesian Dualism
  * How do we process all of the incoming streams to form a reality?
  * "Consciousness Explained: Multiple Drafts Model
