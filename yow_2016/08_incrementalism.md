# Incrementalism: A Strategy For Adopting Modern Automation
## Sean Chittenden

* Hashicorp
* Factory architect metaphor
* Secrets
 * Nomad
 * It takes more effort to deal with static secrets than dynamic secrets
  * 
  * Passwords don't get rotated because it's too hard
 * Use a secrets service
* Service Discovery
 * DNS
  * Doesn't care about distances between datacentres
  * Nagios alternative
   * Cycle through services, checking...
   * Doesn't scale
  * Consul agents gossip
   * Runs every 200ms
   * Only informs on _state change_
   * Distributed failure detector
   * Something managed to ping the service <200ms ago
   * Can reason about the environment better
* Terraform
* Takeways
 1. Codify Everything
 2. Per-plan outcomes at build-time
 3. Create reproducible artifacts
 4. Idempotent APIs and Tooling
 5. Developer-Centric Operations
 6. Make small, well-understood changes
 7. Start where it makes sense for your org

Like X I too lived in an awful mostly-static CMDB universe for ~15 years...
