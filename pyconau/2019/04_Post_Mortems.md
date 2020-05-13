# Post-mortems: Building better software together
## Thomi Richards 

* Root Cause Analysis
    * Cause/Effect
    * Blame
        * Makes engineers feel bad
        * Documents fault
        * People try to hide mistakes
    * Results in very small, localised changes
* Cynefin Framework
    * Exists to help leaders decide how to respond to a problem
    * Determined by the type of system, categorised by how cause/effect are linked
        * Complex
            * Cause and effect are not determinable in advance
        * Complicated
        * Chaotic
        * Obvious
* Code is a Complex System
    * To change the code you must understand the code: develop a mental model
    * We try to understand the Effect of the changes we make
    * Produced by teams, not by individuals.
    * According to Cynefin we should (similar to Agile):
        * Probe
        * Sense
        * Response
* Incident Analysis
    * Instead of root cause analysis
    * Looking at the systems that the Engineers use to make changes:
        * What systems prevented us from Probing (treating the changes as experiemental)
        * What systems prevented us from Sensing (understanding the impact of the change)
    * E.g.
        * Missing information: the Engineer didn't have info to understand their change would cause a big problem.
* Running a Post-Mortem
    * Depends on:
        * Software being built
        * Who custoemrs are
        * Company culture
        * Money
    * Analysis != Response (fix production, then improve resiliency)
    * Not trying to find what went wrong. Trying to find what to do differently
    * Analysis Facilitators
        * Keeps conversation on track
        * Ensures people
            * understand the Complex framework
            * what's happenign and why
            * people dig for a deeper truth rather than gloss over
            * everyone gets input
            * entire company gets input (not just engineering)
            * are not scared by the process
    * Timing: 24h *after* outage
        * Incidents are complex, allows people to unwind
        * Allows for global participation
    * Video Conference
        * While most things are done async, this requires people in the same "room" having discussions.
        * Facilitator follows a handbook: ensures structure
            1. Collaboratively edit document: objective record of events with UVC timestamps
                * Ensure *everyone's* input
                    * SRE people talk about pagerduty alerts
                    * Devs talk about git commits
                    * Support talk about tickets etc
                * Ensure going back far enough to capture important previous events
                    * E.g. had an alert been going off a day earlier? A week?
            2. Systems Analysis
                * Everyone has an opinion
                * "5 Whys", "Infinite Hows"
                * Facilitator needs to take notes
                * Eventually suggestions dry up, 2-3 major things will become apparent
                    * We want to fix the things which are low-cost, high-impact (e.g. misleading text in an alert)
            3. Action Items
                * Ticket/Card in Backlog
                * Facilitator may chase these up
    * After Video Conference
        * Document and recording posted to entire org
            * So everyone can understand what conclusions were reached and why
        * Ask other facilitators for feedback (in video)
            * How can I improve? *"If you had asked Question X at 12:34 you might have learned something useful"*
        * Bake into the process a method for improvement (similar to a retrospective)
* Reading
    * How Complex Systems Fail
    * github.com/thomir/talks
