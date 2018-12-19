# Deprecating Simplicity
## Casey Rosenthal

* A complex system
    * No human can retain a mental model in their head
    * Components can behave correctly (even in failure)
        * But in concert they have unexpected/undesirable effects
        * Because no human can retain a mental model of all services interacting
* Optimisation
    * Performance
    * Availability
    * Fault Tolerance
    * Feature Velocity
        * New from Netflix!
        * Microservices: Decoupling services allows for more iterations
* Complexity
    * Accidental
        * It's going to happen
        * There's no known way to stop this happening
        * As you continue to add features, you will add accidenta complexity
        * Some theories attempt to reduce, but none are perfect
    * Essential
        * Complexity required to satisfy business goals
* Approaches
    * Simplicity
        * Removing complexity is impossible. Don't bother.
    * Redundancy
        * Can encourage engineers to take more risks
        * E.g. o-rings on Challenger
        * E.g. dual motors on BlackHawk helicopters
        * E.g. Redis in front of Primary Datastore
    * Avoiding Risk
        * You have to be exposed to risk to know how to handle it
        * Being careful, avoiding risks and having redundant systems can work against you
* Economic Pillars of Complexity
    * 4 pillars:
        * States
        * Relationships
        * Environment
        * Reversability
    * Look at which of these we *can* control
        * Reversability: software is good at this
            * Blue / Green deploys
            * Feature toggles
        * Make architectural decisions that allow you to reverse things
* Chaos Monkey
    * If you want a developer to deal with something, make it a problem and put it right in front of them.
    * Chaos Monkey did this for small service outages and it worked
    * Chaos Kong did this for entire regions
* Boundaries
    * Economic
        * Run out of money: out of business
        * We have a good sense of this
    * Workload
        * Try to do too much work: out of business
        * We have a good sense of this
    * Safety
        * Break things: out of business
        * We likely *do not* have a good sense of this
        * We overrun the safety boundary to stay within the economic and worklaod boundaries
* Software Engineering: The Burecractic Profession
    * Different people
        * The people who decide *what* gets done
        * The people who decide *how* to do it
        * The people who *do* it
    * Constantly shifting priorities
        * Too many influences on how to build the system
* Alternative to Burecracy Model: The Kitchen Model
    * Like Thanksgiving dinner
        * Everyone in the kitchen
        * Nobody directing
        * Everything gets done
        * Sometimes you finish something and notice you're in everyone's way
            * We have a mental model of when we're an obstacle to others
        * Lously Coupled
        * Highly Aligned
    * Embrace complexity and navigate it
    * Provide opportunity for teams to practice working together
    * Optimise for reversability

