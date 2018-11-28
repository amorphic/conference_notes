# Watch out for Safety Bandits!
## Tennessee Leeuwenburg 

* Safety
    * For problems other people made
    * Testing:
        * `pip install insecure-package`
        * `safety check`
    * `pyup.io`
* Bandit
    * For problems you made
    * Introspects program
        * Follows the AST and follows calls
        * Rather than analyse syntax
    * Examples
        * Known broken SSL
