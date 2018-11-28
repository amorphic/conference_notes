# Production Haskell
## Reid Draper

* Advantages
 * Low defect rate
 * Easy to refactor (given the type system)
 * OSS libs for everything
 * Statically compiled bins - easy to deploy
* Building
 * cabal sucks, use stack - stack.yaml 
 * dependencies
  * ghc dependencies - for a specific version of haskell
  * snapshot - stackage: a group of common dep versions which work together
 * project specific
  * override libs from within stackage
  * add project libs, closed source libs etc
  * only these need to be rebuilt from scratch on update
 * similar to docker container images!?
 * Build times are fast!
 * Can run interpreted
  * For REPL
  * For running in dev (web server etc)
  * Advantage over other static languages
* Deploying
 * Simple with binary
  * Symlink to latest version
  * Restart app
 * Easy to write code which takes advantage of all cores
  * Greenlets -> Threads -> CPUs
* Monitoring
 * ekg - simiar to java 'metrics'
 * run on host - web + json api interface to
  * app metrics
  * system metrics
 * logging
* Testing
 * QuickCheck
  * encode - automatically checks inputs/outputs without manually writing

