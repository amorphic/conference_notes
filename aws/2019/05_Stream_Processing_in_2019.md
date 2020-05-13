* What do we need?
    * Consumption MOdels
        * Event Driven
        * Source for batch
    * Loosely Coupled
        * Microservices
        * Schema Felxibility
    * Operations
        * Elasticity
        * Scalability
* Brokers
    * Kinesis - more than just the stream
        * Data Streams
        * Data Analytics
            * Aggregate, Filter, Enrich
            * SQL statement or Java-based
        * Data Firehose
    * Kafka
        * Broker Replicas
            * Resilience
                * Across AZs
            * Performance
                * More Consumers
* Consumers
    * Kinesis COnsumer Lib
    * Open Source Tools
        * Apacke Spark
        * DataDog
        * Confluent KSQL (SQL over streams!)
    * Flink
        * Easy API
        * In-memory computing
        * Maintains short-term state
        * Guaranteed process-once
        * Run SQL statements
        * Tumbling/Sliding Windows
