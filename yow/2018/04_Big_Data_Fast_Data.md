# Big Data, Fast Data @ PayPal
## Sid Anand

* 3 stages of data
    * Web
    * Analytics
    * ML
* Data Plane (where the data lives)
    1. Data lands in Oracle DB
    2. Oracle Golden Gate: exports commits in Oracle propietary format
    3. CDH Replicat
        * Converts Oracle format to Avro
        * Gets column updated and primary key
        * Checks for schema change
        * Looks up Avro schema registry and decodes message
            * Fills in blanks: creates separate messages for various destinations based on security requirements
    4. Router: sends data to destination
* CDH Control Plane (where the data is consumed)
    * Service-oriented architecture
        * Other teams can create requests for data pipelines via API
    * Mesos!
* Challenges
    * Single Points of Failure
    * Performance Bottlenecks
        * Hydration query to is intensive
    * Data corner cases
        * Ignore LOBS because unpredictable
        * Types: everything is a string (Oracle `num` type is impossible to convert)
    * Deployment
        * If there's a bug it breaks data downstream
        * Alternative:
            * Ansible
            * Stop system, set checkpoint, deploy, test, continue/rollback
            * No broken data!
    * Variety
        * Users, Tools, Datastores
            * Analysts like SQL (Spark SQL + Jupyter notebooks)
            * Engineers like writing Spark queries
        * Access Simplified with Gimel Data API (gimel.io)
* Data Engineering
    * Multi-disciplinary field
    * Requires people from a wide range of backgrounds
    * No test systems!
        * There's too much data to reliably replicate
        * Make prod systems self-healing
