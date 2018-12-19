# Return of the Fat Client?
## Erwin van der Koogh

* Thin vs Thick client
    * Changes over history
    * Optimising for:
        * Richness/Responsiveness
            * Locally-installed applications
        * Ease of Management
            * Mainframes
    * Web pages: more Richness/Responsiveness than Mainframes
    * Mobile applications: more Ease of Management than Locally-installed
    * Web applications: Richness/Responsiveness *with* Ease of Management
* Problems
    * Performance
        * Shipping bigger and bigger JS bundles
        * Long load times lose users
    * Deployment
        * We treat front-end web apps as static websites
        * We have one bundle per environment (test, staging, prod)
            * `my-app-2.3.1-xyz123-prod.min.js`
            * `my-app-2.3.1-abc456-dev.min.js`
            * Are these the same?
        * Indexing doesn't work brilliantly
        * If you care about indexing, SEO, metatags etc: HTML is king
* Final Frontier
    * Not just Client-Side-Rendering
        * Good to have server-side decision making
    * Power of 3
        * Prod-worthy
            * 1 bundle through the entire pipeline (no test/dev/prod)
            * Canary deployments and AB tests
            * Security Headers: unique values per request
            * Crawlable
        * Performance
            * Caching Headers
                * Different depeding on content
                * Chunking/Preload Headers
            * Server-side Rendering
        * Personalisation
            * Different experience based on
                * Location
                * Language (ACCEPT header)
                * User-Agent (only ship polyfills if browser need it)
                * Cookies (Customer A experience vs Customer B experience)
* Solution: Front-end Applicaiton Bundles
    * Front-end tooling (react/vue cli) -> FAB
        * Common output
    * Structure
        * Static Assets
            * Fingerprinted
            * Available for up to 1 year
        * Server
    * Small, portable
    * Linc server
        * Can serve different FABs dynamically
        * Does server-side rendering etc
        * Can be pushed to cloudflare
    * Fills the gap between:
        * Bare single-page app w/no server-side (small orgs)
            * They accept the drawbacks
        * Rich server-side rendering etc (large orgs)
            * Generally built in-house
            * Not standard
* Github: FAB spec
