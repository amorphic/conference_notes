# The Technical Debt Trap
## Doc Norton

> Technical Debt has become a catch-all phrase for any code that needs to be re-worked. Much like refactoring has become a catch-all phrase for any activity that involves changing code. These fundamental misunderstandings and comfortable yet mis-applied metaphors have resulted in a plethora of poor decisions. What is technical debt? What is not technical debt? Why should we care? What is the cost of misunderstanding? What do we do about it?

> Doc discusses the origins of the metaphor, what it means today, and how we properly identify and manage technical debt. In this talk I’ll share how these four principles power world-famous companies and how they can help you work with greater speed, simplicity, safety and success.

* Technical Debt is
    * A strategic design decisions
        * To get to market and learn
    * A metaphor for *"here be danger..."*
        * But metaphors go wrong
        * Financial metaphor extended
* Fowler's tech debt quadrant
    * Reckless/Prudent vs Deliberate/Inadvertent
* *"Ability to pay back debt depends upon you writing code that is clean enough to be able to refactor as you come to understand your problem"*
    * Refactor changes internal structure without external behaviour
    * Thus clean code and tests are a requirement to repay the debt
        * Otherwise it is not tech debt. It is cruft
        * A Financier vs a Pawnbroker
* Reckless behaviour
    * Deliberate = Irresponsible
    * Inadvertent = Incompetent
    * So neither of these can be Technical Debt. They are cruft.
* Cruft or debt can come down to team standards
    * Some things are acceptable and some are not
* Don't deliberately create cruft
    * Sets precedent for speed over quality
    * We think can move fast - will only work in the short term
    * Expectation of increased velocity
    * Cruft slows you down
    * Must write more cruft to keep up
    * When cruft leads to more cruft
        * You have to ask permission to do your job correctly
* Managing Cruft
    1. Failing strategy: Cleaning iteration
        * Scheduled iterations for tidying
        * Quality deferred to cleaning sprint
        * Focus on speed/velocity at other times
    2. Winning strategy: Clean constantly
        * Never make an intentional mess
        * Monitor you "technical debt"
        * Follow the Boy Scout Rule
        * Never ask permission to do job correctly
* Monitoring Cruft
    * Code Coverage
    * Code Complexity
        * Lines of Code is the key complexity metric!
    * Churn
    * Maintainability
    * Monitor trends, not points
        * Is it trending in the way we expect for the strategy we've chosen?
