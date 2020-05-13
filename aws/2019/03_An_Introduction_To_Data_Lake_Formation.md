* Process
    * Find Sources
        * RDS
    * Move to buckets/S3
    * Configure access policies
    * Map tables to S3 locations
        * Athena, other analytical services
* Lake Formation
    * Automates process above
        * Identify/Ingest/Clean
        * Enforce policies
        * Provide access
    * Process
        * S3 Storage layer
            * Simply register existing S3 buckets
            * Or DL creates for you
        * Blueprints
            * Facilitates data schema import
            * Auto converts to target format
            * Auto paritions based on parittioning schema
            * Track changes
            * All customisable - built on Glue
        * Define security policies
            * Add at the table/column level rather than bucket/object level
        * Make available for analytics
