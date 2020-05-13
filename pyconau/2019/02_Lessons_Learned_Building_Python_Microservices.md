# Lessons learned building Python microservices
## Richard Jones

* All calls encapsulated via APIs and API libraries
* Common requests-bases http layer
* Backends-For-Frontends
    * zzz
* Git submodules
    * Use these to work on a library repo within a service repo (pinned).
    * Well supported by pycharm
    * Single commit/push to change both service and library
        * Push changes direct - no release process!
* Tools
    * Attrs in the code (?)
    * Cookiecutter
        * E.g. settings file in the same place.
    * Tox
        * Managing venvs
    * Pytest/coverage
    * Flake
    * Black (Prettier for html/js/css)
    * Pycharm
        * Introspection
        * Multi-cursor editing
* Inconsistency
    * Crept in due to inexperience
    * If you're going to do this ensure consistency across all teams. Catch pain points.
* Interoperability
    * Contracts
        * pact.io
            * Declare and enforce contracts between services
            * No need for expensive integration tests. Checks:
                * Use is valid
                * Change desn't break integration
            * See: Silvia Yap (PyCon AU 2018)
            * `reecetech/pactman` - pure Python implementation
    * Keepalive
        * Unsupported by uwsgi: Client thinks keepalive supported, uwsgi has dropped.
        * Not a problem behind nginx/apache etc. But a problem when using uwsgi direct.
        * Replaced by apache/modwsgi
* Resilience
    * Lots of places where this can fail
    * Turn on TCP/HTTP retries in libs (for certain types of TCP/HTTP error)
    * Turn on DB connection retries in libs
        * Connections are generally long-lived
        * Implement database connection health check.
    * Per-team Grafana dashboards!
        * Build statuses, HTTP errors, applciation errors etc
        * All exceptions, errors etc for to Sentry
        * Use ELK + Prometheus to collate 
        * Also some custom code to pull metrics and dump in Postgres DB, backed onto by Grafana
* Data
    * Django
        * Wrapped in Django REST Framework
        * Replaced the frontend interface with Swagger
    * Transient service user data stored locally in sqlite
* Background Processing
    * Celery (RabbitMQ or Redis)
* Performance
    * Mostly not an issue
        * Smallish-services, specific domain, couple of tables, fast response times
    * Less performant - required profiling
        * Django debug toolbar (get only, very thorough) + silk (code, db, get/post)
        * Custom profiling in code
        * Newrelic (but hard to understand)
    * Reduce SQL queries as much as possible
    * Batched requests
        * Price 100's of items into a single REST call
        * Allows for SQL optimisation
    * Caching
        * Fan-out/in microservices can cause enormous request counts
        * Caching 
        * @lru_cache si the simplest way
