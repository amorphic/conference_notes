# Using Docker Safely
## Adrian Mouat

Books
* Wrote "Using Docker" (O'Reilly)
* https://www.openshift.com/promotions/docker-security.html

* Image security
  * Lots of negative feedback
  * But they can be used security
* The Benefits of Security
  * Alas you get nothing back for being secure.
  * But you save the business
* Container Attack Vectors
  * Kernel attacks
    * Docker containers share the kernel with other containers *and* the host
      * Kernel panic brings down the host and all 
    * Starve memory
 * Container Breakouts
   * Assume possible - but unlikely
 * Poisoned Images
   * Images from Dockerhub - are they vetted?
 * Sniffing Secrets
   * Often set manually on VMs
   * But containers need them injected automatically
* Paradigms
  * Defence in depth - use mutliple layers of security
    * Encrypt data at rest
    * Use containers in isolation
  * Monitoring
  * Least privilege
    * Container should only have access to the resource and data *essential* to its function
      * Eg no access to CC data volume if not required
      * Eg no access to >1GB RAM if 1GB is all that is required
    * "Least privileges in containers" 
* Tips + Techniques
  * Put containers inside VMs to segregate groups of containers
    * Multiteneancy
      * Each user's containers in separate VMs
    * Different security levels
      * Containers doing frontend in one VM
      * Containers doing CC backend in another VM
   * Docker privileges == Root privileges
     * Secure remote API
     * Systems Users not namespaced
  * Root container (UID 0) is root on the host
    * Being addressed in Docker 1.9 experimental - mapping
    * Set a user
      * Create a user in Dockerfile
      ```
      RUN groupadd -r user && useradd -r -g user user
      // maybe a chown?
      USER user
      ```
    * Change to the user via USER or `su/sudo/gosu`
  * Deleting via `rm` doesn't work
    * Set container FS read-only if possible
      * pass `--read-only`
      * Poke holes using volumes
  * Set volumes to read-only
  * Drop capabilities
    * ~30 capapbilites - each allows set of kernel calls
    * By default docker container can make lots of calls
      * `--cap-drop SETUID `
      * `--cap-drop ALL --cap-add ...
    * Some calls (like `net-admin`) drag in lots of others
    * Next release introduces `set-comp` for lots more
  * Set resource limits
    * Set CPU shares - only
    * Set Memory limits
      * control memory
      * control swap
  * Defang setuid/setgid
    * find binaries that run setuid (using `find --perm +6000 -type f` and remove setuid bit or rm them
  * Minimal images
    * Less software = less attack service
    * E.g. Alpine linux
      * Small (~5MB) but with a great package manager to 
  * Static binaries
    * Add directly into base image
  * Disable inter-container communication `--icc=false`
    * Then only linked containers can communicate
    * Uses iptables
  * Linux security modules
    * SELinux (PITA - don't use it)
    * AppArmor
     * Limits container access to host files and kernel caps
     * Tool called Bane which makes creating profiles easier
  * Security hardened kernels
    * grsecurity
     * PaX - changes the way code is handled in memory
      * makes code read only
      * randomises locaiton in memory
    * Lags behind latest version
    * problem because Docker usually needs latest kernels
  * Verify Images
    * Know what you're running and where it came from 
      * Is it running an old/vulernable version of something like nginx?
    * Enable Docker Content Trust!!! (env)
      * Not all images have been added
    * Pull by digest
      * Uses a hash
      * Need to get the hash in advance
    * Be careful which images you use
      * Official images ok - verified by docker
      * Automated builds
      * Check the Dockerfile!
    * Auditing
      * Immutable infrastructure!
      * Audit images, not containers
      * Verify via docker diff
      * Scanning tools
  * Sharing Secrets
    * Don't bake into image (of course)
    * Env vars - works but can be seen in many places
      * linked containers
      * docker inspect
      * can't be deleted
      * often in reports
    * Mount as a volume
      * best way for now but files get checked in accidentally etc
    * Secure k/v store
      * vault
      * keywhiz (square)
      * leases, store encrypted
      * still requires authentication
        * one-time 
      * Coming: volume plugin that talks to the store and gets it at startup
      * Kubernetes has this functionality built in
