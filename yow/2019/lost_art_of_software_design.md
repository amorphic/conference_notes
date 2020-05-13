# The lost art of software design

* Big design up front is dumb. No design up front is dumber.
* Books
    * Clean Architecture
    * Just Enough Software Architecture
    * Evolutionary Design
    * Building Evolutionary Architecture
    * https://leanpub.com/b/software-architecture/c/yow19
* If you can't see the solutions you can't understand them. If you can't understand them you can't evaluate them.
* UML
    * Generally 1/10 people use it 
    * Reasons to not use UML
        * I don't know it
        * Not everyone on the team knows it
        * I'm the only one on the team who knows it
        * You'll be seen as old-fashioned
        * Don't want to tell devs what to do
        * Tooling sucks
        * Too detailed
        * Not expected in agile
* Superficial upfront design
    * If you don't engage in the problem you end up with a very simplified and superficial view of the solution
    * Discussion reveals (devil in the) details
* Technology decisions
    * We don't want to impose *everything* but we need to make some decisions up front.
    * Without some structure and direction and guidance we'll end up with 
    * People are hesitant to put tech choices on early diagrams.
        * But people need tech choices to make sense of diagrams
* Up front design
    * People wonder if they are even allowed to do up-front design in agile.
    * People misinterpret the Agile Manifesto as saying not to do design
        * Agile discourages *Big* up-front design
        * Agile recognises that a good architecture 
    * Many teams don't have a lot of experience
    * Some up-front design reduces anxiety about the project
    * It's not about creating perfect design up front
    * Up-front design creates a *starting point* and a *direction*
        * We can always change direction later if we need to
        * Discovering the unknown unknowns
    * Not trying to make every decision
* Architecture represents the *Significant decisions*, where significance is measured by *cost of change*.
    * Certain up-front decisions become baked in and *very hard to change*.
    * Evolutionary architecture is hard to do and still requires significant decisions.
* We don't have a common language. C4 model is an option.
    * c4model.com
    * Diagrams are maps: they have levels of detail
        * A visual checklist for design decisions
    * System Context Diagram
        * What are we building?
        * What will it talk to?
        * etc
    * Container Diagram
        * High level tech building blocks
        * Applications, datasources, interactions, languages
        * Should spark meaningful conversations
            * If the diagram is complicated, the system is complicated.
            * Identify and mitigate risks ("Risk-storming")
* How much?
    * Iterative and incremental process.
    * Stop when:
        * We understand the significant architecural drivers (requirements, quality attributes, constraints)
        * We understand the context and scope of what we're building (context diagram)
        * We understand the significant design decisions we're making (i.e. technology, modularity [monoliths vs microservices etc])
        * We have a way to communicate our technical vision to other people
        * We are confident that our design satisfies the key architecural drivers
        * You have identified and are comfortable with the risks associated with building the software
* Techniques:
    * Workshops
    * Interviews
    * Impact mapping
    * Events storming
    * Domain modelling
    * OOAD
    * CRC
    * DDD
    * Architecture reviews
    * ATAM
    * Architecture dry runs
    * Risk storming
    * Concrete experiments
    * C4 model
    * ADRs
