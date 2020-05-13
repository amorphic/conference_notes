# How I Learned to Stop Worrying and Love Misery

* The "we only want to show good things chart"
    * 95th percentile spike
    * Hides the 99th percentile which can be a lot
    * The average of the 95th percentile means *nothing*.
    * Tip: You can't average percentiles. Period.
* Is 99% a good indicator?
    * What are the changes of a single web page view experiencing >99% latency of:
        * A single search engine node
        * A single X
    * But clicks do lots of page loads!
    * So a large number of users will experience the 99%
* Latency "wishful thinking"
    * Latency doesn't follow a normal distribution
    * 2-3 OOM between common case and 99.999% case
    * But we don't usually have enough data to see the 99.999%
    * Check HdrHistogram
* The coordinated omission problem
    * The coordinated ommission of bad results
    * Measuring latency: need to keep polling at same rate otherwise the number is meaningless
    * Service time vs response time
    * We tend to only look at response time and mistake it for service time
* Use misery metrics
    * Red/green
    * Number of
        * Timeouts
        * Retries
        * Angry calls
        * Abandoned carts
    * Load vs Misery
        * E.g. load vs 98% transaction success rate
    * Float the misery up so you can still perceive it amongst lots of services
    * Do you even bother showing the green? It's a distraction.
        * 95% non-misery is 5% misery which is bad
        * Focus on fixing hte 5% misery
* Don't aim to make %ile acceptable
    * Instead aim for an acceptable %ile of misery
