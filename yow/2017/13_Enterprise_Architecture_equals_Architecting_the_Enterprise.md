# Enterprise Architecture = Architecting the Enterprise?
## Gregor Hohpe

> Architects in the enterprise are often regarded as ivory tower residents who bestow their utopian plans upon project teams in the form of colorful diagrams that bear little to no resemblance to reality. The most suspicious in this group are often the “Enterprise Architects” who are perceived as being furthest from actual technical problems.
> However, large-scale IT operation and transformation require transparency across hundreds or thousands of applications running on all sorts of middleware in data centers around the globe. The very enterprise architects are likely the only ones who stand a chance to bring transparency into such an environment and who can direct IT investments in the hundreds of millions of Euros towards modernization and run-cost reduction. This sounds a lot more exciting and valuable than drawing pictures!
> This session takes a serious but light-hearted look at the role of enterprise architects in modern IT organizations.

* If things are broken at the Enterprise Architecture level it's impossible to put right 
* Misconceptions
    * Ivory Tower - writing pictures and sending them down for others to debug
    * Architect - doesn't have to get involved in implementation
* Purpose of Enterprise Architecture
    * Glues between Business Architecture and IT Architecture
    * If business and IT is tightly intertwined there is less E.I. (e.g. Google)
* Value Chain
    1. Understand Business Strategy
        * Products
            * E.g. Allianz doesn't just sell policies, they have departments that inspect risk in different areas
        * Processes
        * Where money is made
    2. Translate into IT Strategy
        * Divisions and Business Lines
        * Understand perceived role of IT
            * Cost Center?
                * Focus on Cost
                * Cuts business cost through automation
                * CIO reports to CFO
                * Outsource
            * Asset?
                * Focus on ROI
                * CIO reports to COO
                * Harmonise/rationalise
                * Economies of Scale
            * Partner
                * Focus on Business Value
                * CIO reports to CDO (Digital)
                * Insource IT
            * Enabler
                * Speed & Innovation
                * CIO 
                * IT = business
                * Economies of *speed*
        * If mis-aligned at this level, everything underneath falls over
        * Need to understand where the org is at:
            * E.g. You can't sell speed to someone who cares about *cost* (CFO)
            * So you have to change your pitch: focus on money saved
        * Strategy is:
            * Not reality
            * Defning what you *won't* do
                * E.g. not investing in fixing an existing problem if a solution is in the pipeline
            * *Not* the vendor's product road map
        * Enterprise Arch as Strategy Quadrant
            * Integration vs Diversity
    3. Create Transparency
    4. Define IT Target Picture
        * Management loves a plan
            * Problem -> Solution
        * E.g. talk about problems with application silos
            * Words like "Duplication" indicates cost.
        * Coming to a simple, clear picture takes time
            * Distill the message to the essence
    5. Define a Roadmap
    6. Harmonise and Govern
        * E.g. noticing that Infrastructure was Diverse and Applications Prescriptive
        * Want Infrastructure to be Harmonised and Applications Flexible
    7. Obtain Feedback and Refine
        * Like everything else, feedback cycle is important
            * Cycle is slow in E.I.
        * Get E.I. involved in projects to see the problems
        * E.g. Architects design system using SOAP/XML
            * Too late to fix/scale
    8. Coach and Mentor
        * You need support
        * You'll also be short of skills
            * So nurture them
* Thinking like and Enterprise Architect
    * Architecture provides Options (same as financial options)
        * E.g. buying cloud allows horizontal scaling - a little extra for the option
        * Options increase in value with volatility (and we live in a volatile world)
            * E.g. ~100 users is predictable, options isn't that value
            * but 100-100k users, option is very valuable
    * Connections
        * Nobody cares about your architecture
            * They care about the properties that your architecture gives the system
                * Speed, Flexibility etc
            * Properties largely result form how it's put together
            * People tend to look at ingredients (boxes) rather than combinations/connections
                * As architect you need to be a good chef, not a good ingredients buyer
        * Connections between Layers, Systems, Functions
    * Abstraction
        * Everything is becoming more complex
        * Pictures are the best way to deal with complexity
        * Pictures are a model
            * For a good picture you need to know what question it is supposed to answer
            * There are no good or bad models, just those which are fit for purpose or not
        * Don't try to draw reality
            * It is a *model* of reality to help us reason better
    * Decisions
        * You will never have all of the answers
            * If you try to gather all of the answers things will change by the time you finish
        * Don't try to fix everything at once
            * Pick a focus and make an impact
                * Get feedback cycle.
* Not Black Magic
    * Much of it is common sense
    * Many people
        * Get lost in the complexity
        * Become enamoured with frameworks
* Good Architecture is about combining multiple viewpoints
    * An interesting career as an architect is also about combining multiple viewpoints
    * Change sides more often, have a differnent PoV
    * Be value driven and achieve measurable results
    * If you can do it you can be an enterprise architect
        * THere is great demand for good ones - an interesting and lucrative career

* Resources
    * Enterprise Architecture as Strategy: website for the book has all of the good diagrams
