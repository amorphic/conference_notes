# Devpi for teams
## Graham Williamson 

* DevPi
    * PyPI mirror (transparent caching proxy)
        * TTL 30 mins by default
    * Auto-testing (tox - results documented)
    * Personal indexes
    * Index inheritance
    * HA
* DevPi plugins
    * Web UI
        * Docs etc
    * Storage Backends
    * Lockdown
    * Auth
        * user/pass
        * LDAP
    * CI
        * Gitlab
        * Jenkins
    * github.com/devpi
* Inherited Indexes
    * All CI integrated.
    * /root/pypi (inherits from PyPI
    * /dev/<username> (personal for each dev)
    * /shared/testing (run unit tests, if successful copy to prestage)
    * /shared/prestage  (run integration tests, if successful copy to staging)
    * /shared/stage
    * /share/release
* Using
    * Can add config to `pip` so use `pip install` rather than `devpi install`
    * Test happen client side (`devpi test`) - uses tox + venev to run locally then uploads results
    * Can push package versions from one index to another!
