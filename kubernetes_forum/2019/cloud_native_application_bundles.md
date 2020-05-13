# CNAB

* Standard spec
    * Designed to be machine-readable
* Implementations
    * Porter
    * Docker App
* Porter
    * Build + distribute + deploy CNABs
    * Contains porter.yml
        * Mixins
            * Helm - apply helm charts, install tiller etc
            * Kubnernetes
            * Can produce outputs to be used in later steps
        * Credentials
        * Metadata
        * Install
        * Uninstall
        * Upgrade
        * Outputs
            * Hostname
            * IP, etc

