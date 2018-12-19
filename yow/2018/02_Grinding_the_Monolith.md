# Grinding the Monolith
## Michael Nygard

* What's the problem with a Monolith?
    * Advantages
        * All code in one place (IDE).
        * Lower operational complexity (builds etc).
        * Simple, easy to construct.
        * If you can't build a well-structured Monolith, how will Microservices help?
    * Disadvantages
        * Lego hypothesis
            * Flawed
                * Lego has a simple, standard interface.
                    * Software has many and varied interfaces.
                * Can only be connected in the XYX axis.
                    * Software components will sometimes have *dozens* or even *thousands* of collaborators ("util", "manager")
                    * Need 10000+ dimesional space to represent this
                * Changes in one place have ramifications far away across many dimensions.
                    * *Micelea* is a more appropriate metaphor
                    *  Chemical change in one 
        * When all code is in the Monolith, people start breaking the rules.
            * "Just this once", "I know what I'm doing".
            * Calls across domains.
            * Calls up and down layers.
            * Soon any change has to worry about far-reaching ramifications *within* the monolith.
    * Architectural erosion *matters* because it effects *everything*.
    * Safety
        * Stronger boundaries between components mean damage can happen but is contained.
        * Breakdowns always lead to review processes (human rather than automated safety).
            * But these gradually erode.
            * ...until an Event happens and the process is re-visited.
            * *"The Fear Cycle"* : Rather than treating tech as an asset they treat it as something the don't want to change
        * No limits to effect of bad code
        * Common-mode failures in shared code
        * Latent semantic coupling (a component that 
* Microservice Migrations Killers
    * Impatience
        * We built it over 10 years but we want to "transform" in 2.
    * Unrealistic expectations
        * We're going to rebuild 10 years of monolith in a new language with a new datastore *and* move to cloud.
    * Hubris
        * "We know better - we're going to redesign from scratch"
* Approaches
    * Clean Then Separate: __Failed__
        * *"Refactor to create unterfaces between subdomains, then turn those into HTTP interfaces"*
        * Failure modes
            * Takes too long.
                * Exectutive impatience will defeat the plan.
                * They will never accept "no new features for 2 years".
            * Ongoing feature work introduces new deps *faster than they are removed*.
                * The "B team" 
                    * Are not doing the new shiny aren't motivated to do the hard work of keeping their work future-proof.
                    * Like 1 person with a mop + bucket trying to clean up after 5 people walking with muddy boots.
    * Entity Services: __Failed__
        * *"Make yur key domain objects into services"*
        * Failure modes
            * Makes deployments more disruptvive.
            * Starts to look like "distributed monolith".
            * Creates common deps from many features to the entity services.
            * CRUD usually means entity services.
    * Project Teams: __Failed__
        * *"Keep developer utilisation high by drawing them from a pool for the duration of the project"*
        * *"When the project is done, throw the devs back into the pool"*
        * Failure modes
            * Project-orientation favours deadlines over code health & architecture initiatives.
            * Devs who do the hard work of refactoring should be able to enjoy the fruits of their efforts.
        * Instead
            * *Product* teams over *Project* teams.
            * Product team might still have projects, but it's the same team.
    * Clean-Sheet Design of New Services
        * *"We know the domain, let's design new services to leave the past behind"*.
        * Failure modes
            * We make the same mistakes over and over.
            * "Second system effect"
                * Feature bloat to do all the things missed the first time.
                * Designer optimism not supported by any past evidence.
        * Instead
            * Design in context of what you already have
                * Accept the scars of the past.
                * You might get a clean sheet right, but you probably won't.
            * Dont worry - the system will continue to evolve.
    * The Strangler: __Partial Success__
        * *"Create an intercepting proxy that can divert some kinds of traffic to one new service at a time"*
        * Experience
            * *Sometimes* works.
            * Service design will be unpleasant - it has to exist in the context of the monoloith.
    * Clone and Slash: __Partial Success__
        * *"The current system works"*
        * *"Devs know what's needed in their own areas but afraid of far-distance effect of changes"*
        * Experience
            * Product teams rather than project teams.
            * Each team gets the entire codebase and slashes what they don't need.
        * Problems
            * Services will be larger than you'd like.
            * Still likely to use common DB.
    * Continual Redesign/Rebuild: __Success__
        * Microservices are never "done".
        * Keep the pressure on simplifying design.
        * Problems
            * Devs are uncomfortable with the idea of services being disposable.
    * Service by Lifecycle: __Partial Success__
        * *"Objects with long lifespans that serve multiple uses are hard to change"*
        * *"Therefore find major boundaries in the business processes and make the before and after parts into separate services"*
        * Reality
            * Phases (such as a loan - the process only ever moves forward).
            * Isolate the phases and make them into separate services.
    * Domain Objects on the Wire: __Failed__
    * Refactor to Hexagons: __Success__
        * Create Adaptors between the external interface and the domain.
* Questions
    * Avoid attempts to re-wrap off-the-shelf software.
    * __Finish transitions from legacy__!
        * Temptation once the initial pain has subsided to not worry about the last 10-20%.
        * The value on retiring legacy systems is in reducing the complexity of the environment and the resulting need for expertise/understanding.
    * New pattern: separating out UIs
        * "Micro frontends"
