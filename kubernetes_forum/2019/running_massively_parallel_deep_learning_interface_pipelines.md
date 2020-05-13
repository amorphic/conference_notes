
* ALl about processing DAGs
* Primarily AWS spot instances
    * But cloud-agnostic: uses GCP if AWS runs out of spot instances
* Use ephemeral node
    * 3 masters
        * Use pod priority + placements to ensure critical jobs are running
    * 1-3 on-demand CPU nodes
    * 0-n*100 spot CPU nodes
    * 0-100 spot GPU nodes
* Queuing
    * Separate db-backend service
* I/O
    * Stateful with cross-AZ storage
    * Isolate persistent volumes for jobs and delete when finished
        * Avoids hitting I/O limits
    * Can mean nodes are orphaned when storage isn't attached correctly
        * Still an ongoing problem
        * Solved with custom agent: drains unhealthy nodes
    * Manually reserve resources in cluster spec
* Routing
    * Route table limit of 50 entries
    * CNI change from kubenet to flannel could allow for >50
* Auto-scaling
    * Issues beyond 80K pods & ~650k nodes
    * Home-rolled solution when problems begin
* Running out of spot GPU 
    * Multi-cloud
        * Centralised with Itsio
    * CircleCI
    * Kops
    * Terraform
* Data integrity
    * S3 syncs sometimes fail
    * Data verification to confirm things are right
* Infrastructure limits
    * Provisioning
* Shared GPU
    * Tensorflow doesn't guarantee isolation even when fractioned
    * Exposing GPU as extended resource 
    * In the end optimising code for GPU was the solution
    * Monitoring GPU utilisation
