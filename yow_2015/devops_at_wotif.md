# DevOps @ Wotif - Making Easy Right
## Alexandra Spillane and Matt Callanan

* http://mattcallanan.net

* Make it easy to do the right thing
* What is "the right thing"?
 * Bridging the Dev<->Ops chasm
* What was wrong?
 * Downward spiral of manual activity
 * Silos
 * Overloaded Ops teams - too much work
 * Frustrated Dev teams - slow to get code to prod
 * High release overhead
 * Large batch sizes
 * Manual testing
 * Poor visibility
  * Ops couldn't see what they were rolling out
  * Devs couldn't see how code was performing
 * Calendar of Doom
  * Scheduling in advance
  * Higher priorities bumping lower
 * Superstitious Gatekeeping
  * All releases subjected to 48h load testing
 * Tried to implement microservices
  * But didn't have right organisation and agility
* Re-organised
 * CD team
  * Ops + Dev + BA
 * Goal: release from weeks/months to a day
* Flexibiility vs Predictability
* Standardisation
 * Standardised on
  * How services are deployed
  * How they communicate
 * Freedom on
  * What ran *inside* the services
   * Languages
   * Frameworks
* How to fix
 * Discussed with Ops and Dev, then mgmt, architecture, BAs etc
  * Non-confrontational
 * Collected ideas on a wiki page
  * Prioritised ideas that were achievable in reasonable timeframe
 * Proposed standards, e.g. logging
  * Allowed comments
  * Idea -> Trial -> Agree -> Implement
  * Documented standard - no need to argue
* But how to speed up?
 * Automated verification
  * Python/Fabric - logs on to server and runs standard tests
  * Check ports, files, etc.
  * Fast operational feedback
  * Test-driven operational feedback
   * Target at a given version, run tests
  * Keep old test cases for old versions
  * Reference implementation
   * "Hello World" service
   * Updated for each new version of standards
 * Automated rollout
  * Built in Python/Fabric
  * First versions were interactive to build trust
  * Mandated a 'smoke test' script present in release
 * An alternative path to production
  * Using proper microservices principles
   * Independent
    * One app per release
    * Backward-compatible
    * No DB/Network/OS changes
   * No manual testing
   * No booking specific times
    * FIFO
    * All requests guaranteed within 24h
    * If timeframe required (eg July 1 tax time) release early with a feature flag disabled
   * Must comply with latest standards
  * Only available if you follow the rules
   * Incentivise people to get compliant - to get their code out quicker
  * Dev teams could opt for load testing if they wanted (not mandatory). Generally abandoned.
  * Visualisation in confluence
  * Chatroom events
  * Release time added to each release page - to promote release time to a first-class citizen
* Continuous Delivery vs Deployment
 * Delivery: packages made automaticaally but decision to deploy is made by human
 * Deployment: packages deployed ot prod as soon as ready
* Lessons
 * Balance
  * Rules vs no rules - implement standards but keep them nimble
 * Chip away
  * Tackle the most obvious problems first - can't do anything
 * Ease of migration
  * When new standards come out, add a little paragraph saying what to do to adopt it. Make it easy.
 * Use the carrot rather than the stick
  * Offer a great alternative (SLIPway)
  * Make it optional!
  * Help people migrate
  * Management buy-in
   * Whole business working together
   * Managers allowing resources to
 * Strongly type discussions
  * Choose catchy names
  * Helps make decisions
 * State transition tables
  * Commands : State
  * Telling Ops what to do in what state
 * Be opinionated, not arrogant
 * Warranty period
  * Can't get standards 100% right
  * But need to lock them down
  * Two-week period
 * Small batch size for standards
  * Minor updates every 1-2 months
  * Fast feedback
  * Enable innovation
  * Easier to update
 * Embrace legacy
  * You're creating legacy
  * Make migration easy
  * Incentivise catch-up
* Consistent and predictable interface between Dev/Ops
 * Not embeddeding Ops in Dev
* Cultural choices > tool choices
* Prioritise fast feedback to devs
* Fast releases -> smaller batch size -> lower risk -> happier customers


