# All the Things We Didn’t Do
## Kresten Krab Thorup

> Humio is a startup on a mission to democratise log analytics. With limited resources, being successful is just as much about avoiding bad decisions, as it is about doing things right. This is a talk about trade-offs, technology and culture in building a startup.
> Working with log data introduces quite a different set of assumptions about how a data store should operate: you store a lot of data without known which part of it is relevant, and then after an incident, you want to be able to search it. Our biggest customers only look at 1% of the data they store. This is the opposite of how normal datastores operate: spend resources at ingest to make data easy to find. So we didn’t do it that way.

* Log Analytics and Why You Should Care
    * We are increasingly further from the "action" through layers of abstraction
        * Alludes to talk 01 - Lambda etc relies on good *logging*
        * Mission Control analogy
            * Big dashboard on big screens: High level to indicate thigns are normal
            * Guys at terminals: Drill down if things stop being normal
    * Record -> Monitor/Analyse -> Respond
    * Example dashboard
        * High-level graphs etc
        * Low-level (syslog) data on click
            * Interactive queries over logs + metrics (computed from logs)
    * Trade-offs
        * Logs vs Metrics
            * Events vs Series of Events
            * High Dimensionality vs Low Dimensionality
        * Historic vs Real-Time
            * Incident Response and Audit vs Historic Processing
        * Cloud vs On-Premises
    * Schema vs Ad-Hoc
        * Finding Known Issues vs Unknown Issues
        * DBA vs Everyone
        * Indexed vs Not (Speed)
            * Tradeoff of ingest time vs query time
            * Small user count vs large user count
    * Sweet Spot
        * Record *everything*
        * Generate metrics from logs in realtime
        * Interacetive/adhoc search on historical data
        * Installable on-premises
        * Affordable
* Building
    * Be The Customer
        * Humio had an engaged customer
        * Product development on site co-located with customer
        * Provide a hosted service for dogfooding
    * Safe Environment
        * Senior people should
        * "It takes all kinds"
        * Be open about personal strengths and weaknesses
            * Talk about it within the team
            * Build awareness
        * Open to learning and teaching new practices
    * Be in Doubt!
        * Discuss Trade-offs
        * No alpha males making decisions
        * Be open to different ideas
    * High BUS factor
        * We depend on people
        * Focussing on making replaceable reduces people's engagement
        * Everyone is responsbile
    * Technologies
        * Scala chosen by lead dev
        * Agile
            * Take small steps - frequent deployments
            * Define design goals and discuss tr
        * Own critical components
            * Pulling in lots of open source components creates deps
            * They write these themselves
            * *I disagree with this*
            * Made point about abstration layers *"Wasting" hardware
                * They own/write everything to not waste hardware on critical path
                * But this is unique to them building an on-prem solution. This is atypical in modern computing.
                * Ignores problems of on-prem hosting
                    * Lack of scale, need for redundnacy, expertise etc
        * Containerise to reduce deps
* Tech
    * Time-series data store
        * Minimal Index and compress data
        * Super-fast "grep"
        * 10GB chunks (start-time, end-time, metadata)
        * Compress to 1GB.
    * Uses a state machine with "steps"
    * Keeps state of current "counts" etc for fast querying
    * For historic data queries replay data through state machine
    * Filter -> Aggregate
        * Aggregates
            * count, avg, stddev
            * GroupBy (Time Boxing events
    * Filter
        * Metadata #tags -> specific data files
            * reduces files that must be read
        * load -> decompress -> search
            * but data ends up in main memory (slow)
            * decompress + search in 64k chunks it stays in CPU cache - super fast!
        * If files already in system file cache disk reads are eliminated
        * This is not new
            * "Why KDB+ is fast"
        * With a small user count it's worth getting good at really fast table scans
    * Kafka
        * All ingested data
        * Commit log
