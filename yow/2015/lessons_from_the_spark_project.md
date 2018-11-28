* Scala and the JVM as a Big Data platform: Lessons from the Spark Project
** Dean Wampler

* http://typesafe.com/reactive-big-data
* http://polyglotprogramming.com/talks

* Spark Hello World
 * Much simpler syntax than MapReduce
 * RDD jobs
 * textFIle->map->flatMap->reduceByKey->map->groupByKey->map->saveAsTextFile
* Simplifies Streaming
 * MapReduce was designed for batch processing
 * Spark was implemented as a batch system but able to do 'mini batch' processinig due to efficiency
  * This looks like a stream :DStream
  * Batch constrained by a given time interval
  * Also provide windowing functions for moving averages etc
 * Could not handle sub-second event latency: use a real message queue
* Robustness
 * Handling backpressure
  * Dynamically ireduces the amount of data per batch (new in Spark 1.5)
  * Need to be able to tell the producer to back off
   * Reactive Streams allow consumer to talk to the producer
   * Support coming soon
* SQL/Dataframes
 * Alternative to the usual Extract/Transform/Load process
 * Wraps RDDs
 * Allows relational-like queries
 * Query planner/optimiser
 * Inspired by Python Dataframes
 * sqlContext
  * returns Dataframes
 * Also reads from JSON, parquet (column-based)
* JVM as a platform
 * Known operational platform
 * Lots of Java developers
 * Performance Problems
  * GC - heaps of 10s-100s of GB
   * GC Pauses
  * With Spark too many cached RRDs breaks things
  * Extensive GC tuning required (see online)
  * Java Object Model
   * 48-byte object required for a 4-char string
   * Object references - everything is stored in arrays referring to other objects
  * Spark jobs are CPU bound
   * Network improvements ~2%
   * Disk improvements ~20%
   * Use IO smarter - pruning, caching, smarter formats (parquet)
    * But this needs more CPU!
 * Tungsten project
  * Dataframe API
  * Same performance for all languages: Scala and Python!
  * Moving from many smaller objects to fewer large objects for better GC performance
  * Objects inline for better caching
  * Custom memory management for better object layouts (new CompactRow type)
  * Byte code generation
 * Arrays indexed by integer, limited to 2GB
 * No value types
 * Richer data types exist in Python & R
* Scala
 * Pragmatic OOP + FP
 * Can write functional abstractions but can also go to mutability when required for optimisation.
 * REPL
 * Inferred types
 * DSLs
 * Spark is driving adoption of Scala
* Spark
 * Still problems
  * Not purely funcitonal inside
  * Technical debt
  * Limited tests
  * Interface separation from implementation
 * Spark + Mesos is the platform of the future
  * Typesafe and Mesosphere in agreement
