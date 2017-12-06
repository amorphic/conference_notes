# Frontend At Scale: Designing Infra For Big Teams Infrastructure & Environments
## Josh Duck
@joshduck
 
* FB found individual team infra can't scale 
* Shared infra
 * Teams can focus on products
 * Can chase long tail of optimisations
 * Transferrable knowledge
 * Shared Tooling + Process
* The right infra changes over time
 * What works for a small team too unstructured for a big time
 * What works for big team to constraining for a small team
* Start with Specialisation
 * Understanding on the domain (scribe example)
* Then Simplification
 * E.g. typewriter
 * Trade flexibility for speed and ease of use
 * Early specialisation helped us understand what was important
* THen further abstraction
 * Email/web

* Server rendering
 * Goal: Turn data into markup
 * Medium: Strings + concat
  * Need a lot of domain knowledge
   * HTML syntax
   * HTML tags
   * Escaping Output
   * x-site scripting
  * One small error breaks the whole page
  * Ultimate flexibility comes at too high a price
 * Medium: Object composition
  * > string concat
  * XHP: DSL for components
  * Components == massive win for code quality
   * Encourage engineers to create loosely couple code
  * Further:
   * components worked well
   * Some argued for "good ole" MVC because no separation
    * But MVC abstraction was fuzzy at best
    * Don't be afraid to question established architectures
  * Declarative interface leaves the door open for future changes
* Client Rendering
 * Similarities to server-side
 * Domain knowledge
  * DOM APIs
  * Browser compatibility
  * tracking global vars etc
 * jQuery simplifies DOM APIs
  * Still need to track vars 
  * Constant UI updating
* React
 * Back to theme: Good infra doesn't come from working in isoation
  * Work directly with product teams to understand their needs
   * Product teams and Framework teams in the same room
   * Framework teams see Product team "bending" their framework... use that input to change it!
   * WOrking with less assumptions: easier to change w/4 users than 100 
 * On laucnh
  * Lots of negative feedback
   * html in js - oh noes! Unlike established bet practice
 * Iterating on a core lib is really hard
  * Minimise public interfaces
  * Update call sites alongside infra changes
  * Use tooling to automate
   * FB share update scripts on changes
  * Deprecate, log, monitor
 * Slowly iterate over time
* Evolution
 * React Native
  * Unplanned but now used everywhere
 * Flux
  * Chat problem
   * 1 Message, then 0, then 1
  * Open-sourced the pattern rathen than the code
  * Other implementation *before* Redux
 * Relay
  * Replaces manual data management 
  * Immutable Data
  * Automated Data Fetching
  * Flux was imperative
   * Needed to fetch data first
  * Declarative interfaces
   * Declarative code <3 static analysis
   * Extract data requirements as a build step
   * Fetch data without running JS
   * Not possible with imperative code
* Clearly define the problem
 * Don't just frame the problem around assumption
* Understand product's needs
 * Work direct with a team
 * You should be writing product code too (dogfood)
* Plan to iterate
 * Escape hatch for legacy
 * Support incremental Adoption
 * Plan to iterate your own absration too!

