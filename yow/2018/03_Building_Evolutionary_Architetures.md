# Building Evolutionary Architectures
## Neal Ford

* Evolutionary architecture: architecture that ages gracefully.
    * *"Supports guided, incremental change across multiple dimensions"*
    * Resilient architcture that adapts to change.
    * Architects sometimes treat architecture as an equation to be solved once and forever. But it is constantly evolving.
* Evolvability
    * Can you preserve these characteristics over time as things change?
    * Business-driven change
        * Changing requirements - markets, mergers etc.
        * Agile is about this and we've gotten better at it.
    * Tech-driven change
        * Changing dynamics of tech - cloud, containerisation etc.
        * We've not done this so well.
    * Everything changes all the time.
        * How is long-term planning possible when things constantly change in unexpected ways?
        * But why are we trying to plan to be able to deal with change?
        * Why not make change easy?
* EA Concepts
    * Guided
        * Architectural Fitness Function: *"an objective integrity assessment of some architectural characteristic(s)."*
        * Define the architectural characteristic but also *the means by which to constantly measure it*.
    * Incremental
        * Tests, CI etc
    * Multiple Dimensions
        * Auditability
        * Performance
        * Security
            * Not often considered in architecture.
        * Data
            * Changing datastores definitely influence architecture.
        * Legality
        * Scalability
* Fitness Functions
    * Unit tests, metrics, monitors, chaos engineeering etc.
    * Aspects
        * Atomic (single dimension) vs Holistic (multiple dimensions)
        * Triggered vs Continuous
        * Automated vs Manual
        * Dynamic vs Static
        * Temporal
        * Domain Specific?
            * Architectural characteristics *divorced* from the problem domain
            * May use the same methods (UAT etc) but measure different things.
            * "Can I discuss this characteristic with no knowledge of the problem domain?"
                * Yes: architectural fitness characteristic
                * No: traditional domain-specific test
    * Examples
        * Cyclic Dependency Function
            * Create a unit test that a package import does not create any cyclic deps.
        * Tight Coupling
            * Create a unit test that checks for coupling between modules that *shouldn't be*.
        * Consumer Driven Contracts (Martin Fowler)
            * Triggered atomic fitness function
            * Looks at a single characteristic
        * Holistic fitness function
        * Continuous fitness function
            * Traditional logging/monitoring
        * Continuous holistic fitness function
            * Chaos Monkey
            * Security Monkey
            * Conformity Monkey
        * System-wide fitness functions
    * Governing Code Quality
        * Complexity checking
        * Specific tests that define who things should be called across the architecture
        * Code rules
            * "no class should throw generic excpetions"
            * "no code should log to the default logger"
            * "don't use interface names that end in "interface"
            * "no classes in PackageA should access classes in PackageB"
            * "ensure that Open Source lib license changes are noted and signed off"
        * These rules often reside in a wiki: write once, read never.
            * Once the rules are codified they become enforced
            * Example: ArchUnit for Java
            * Example: BellyButton for Python (though only a linter)
        * Switch from a "heartbeat" ("it's ok, it's ok") to constant checks ("is it ok? is it ok?")
    * Process
        * Identify Dimension
            * Helps with:
                * Prioritisation
                * Cost to implement and maintain
                * Change variable "fix it" cost to a constant maintenance cost (because you're much less likely to "fall off a cliff")
            * Doesn't matter what languages, platforms etc are used, as long as the dimensions is measured
        * Create fitness functions
        * Use deployment pipelines and/or continuous fitness functions
            * DevOps teaches us that once things are automated you have a platform that you rely on.
            * E.g. if you have a Security Fitness Function it's easy to check for new vulnerabilities across the estate
        * Incremental Change
            * Github Scientest
                * Try the new code but Use the new code and analyse the difference.
                * After 24h of no diffs, go live.
* Building Evolutionary Architetures: Support Constant Change
