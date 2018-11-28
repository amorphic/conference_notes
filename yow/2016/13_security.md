# Simplicity, Complexity and Security
## Laura Bell

* Pioneers, Settlers and Governors
* Security team
 * Generally one person a-la "Wizard of Oz"
* Security usually comes late
 * "Maturity drive"
 * Goes badly wrong
* Architecture
 * Architects
  * Person who has been there the longest
  * People from other disciplines
 * Monoliths vs Microservices
  * Monolith
   * One big ball of hard-to-rationalise ball of code
  * Microservice
   * Lots of hard-to rationalise balls of code
   * If you can't draw your architecture on one page how will you find the gaps?
   * Service dependency -> cascading failure
    * E.g. authentication/authorisation
    * Fail open or closed?
  * IoT evolves the threat 
  * Frequently changing architectures
* Heterogenous environments
 * Languages have a cost of ownership (like puppies)
  * If you take a language on, accept this cost
* Open Source
 * Everyone uses it
 * Very few people contribute back
 * But this is our foundation
 * Big fish should feed small fish, not just eat them
* Objectives
   * Architecture doesn't matter
   * Lang doesn't matter
* How things work
 * Now:
  * Split
  * Code
  * Ship
  * Forget
 * Shared component for builds etc
  * CI/CD
  * Easy attack vector
  * Well documented
 * Attackers like simple
  * They are lazy
* Containerisation
 * Gets there super-fast
  * But is there where you want to be
 * Manual setup was slow but we saw how it works
  * services running
  * accoutns etc
 * By all means do auto but take the time to investigate
 * Only run applications from a trusted source
 * No verification happening
  * Check if it's coming from the real source
  * Decide you are going to say No to bad security
* ToDo
 * Document your architecture
  * Informal is fine
  * Multiple views / multiple layers
 * Idenitfy threats + risks
  * Who would cause your harm?
  * How?
 * How many technologies do we have in our environment?
  * Each has potential for vulnerabilities
  * Using langs/frameworks that are out-of-date?
 * Know your stack
  * OS
  * Installed Apps
  * Installed services
  * Containerisation software
  * SAAS products
 * Which components would bankrupt the organisation?
 * Monitor for threats
 * Patch and update
 * Manual open source research
  * Twitter
  * Mailing lists
 * Auto dependency check at build
  * OWASP Dep Checker
  * Libraries.io/DependencyCI
 * Shared components
  * Choose appropriate tech
  * Restrict access
  * Monitor aggresively
  * COnfigure well
  * Challenge assumtions
  * Play with it
 * Containerisation
  * Verify the source
  * Minimise services and port
  * Automate and patch
  * Benchmark security
  * Find things you can monitor automatically
* In a world that celebrates pioneers be the settlers instead
