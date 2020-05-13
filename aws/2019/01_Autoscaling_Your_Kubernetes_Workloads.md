# Autoscaling Your Kubernetes Workloads

* Kubernetes HPA
    * Originally based only on cluster internal metrics (CPU utilisation etc)
    * Then custom metrics *within* the cluser
    * Finally custom metrics from *outside* the cluster
* Metrics to use
    * Work Metrics (customer-facing, e.g. *"Can a user access the webpage?"*
    * Resource Metrics (internal, e.g. *"
    * Work Metrics lead to Resource Metrics, which become temporary Work Metrics
        * Recursion
        * No need to monitor temporary Work Metrics.
    * Autoscaling can be an alternative to Pager alerts.
    * Choose
        * Work Metric that's reasonably abstract
        * Resource metric that's sufficiently predictive as an early indicator of a problem (high response time, long queue length)
* DataDog
    * Cluster Agent autoscales based on any DataDog metric
