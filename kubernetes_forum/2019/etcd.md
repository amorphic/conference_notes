* Etcd + datastores

* etcd - key value store for the cluster
* Rules
    * etcd doesn't run on the main cluster
    * Make nodes immutable
    * Make AWS work for us
* Tried first
    * Static, named nodes
    * etcd nodes in an ASG - don't do this!
    * immutable instances? - how do you keep the data?
* Settled on for etcd
    * Immutable OS partition
    * Separate data partition, mounted by a small program on boot
        * Partition lifecycle
    * Lifecycle protection for instances via Terraform
        * For safety - manual process is ok for this process
* Do differently
    * Don't manage etcd!
    * etcd 3.4 and then 3.5 to get the new Learner state
        * Avoids split brain, loss of quorum
    * Spend more time using DNS discovery for dynamic node provisioning
* Problems
    * Leader election storms
        * Timeout expiry: heartbeat and election
        * While this happens, no DB writes can happen
        * Caused by I/O or network latency
        * Fix it by
            * Tune things in tuning.md
            * Watch disk metrics, particularly the fsync ones
            * Watch the "leader elections total" metric to catch this early!
    * Filling the database
        * Compaction broken
        * Too much stuff stored
        * Default max size is 2.1GB
        * By default all revisions are kept
            * Compacted by default but requires root privileges
        * When db is maxed an alarm is tripped and etcd goes into read-mode
        * Fixing
            * Stop all the load
            * Compact and defrag DB on each machine
            * Allow apiservers to talk to db, but nobody talk to apiservers
            * Wait for size to go down
    * Nore etcd outage is full control plan outage
        * Not a workload outage
        * Can failover to another cluster
        * Commands in maintenance.md
* Avoiding
    * Avoid adding and removing nodes for upgrades if possible
        * Identity comes from:
            * Node name (DNS name)
            * IP Address
            * Data directory
        * If the nodes identity is the same you can swap etcd versions and everything works (probably)
        * If you can't do this, understand how it works
    * Watching the database
        * Watch the metrics!
            * fsync duration
            * commit duration
            * leader changes
            * db size
    * Write recovery runbook and try it regularly

