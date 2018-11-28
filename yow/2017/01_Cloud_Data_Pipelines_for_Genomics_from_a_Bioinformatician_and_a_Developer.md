# Cloud Data Pipelines for Genomics from a Bioinformatician and a Developer
## Lynn Langit / Denis Bauer

> Dr.Bauer and her team have been working to build genome-scale data pipelines that address the computational challenges and limits present in today’s cancer genomic (bioinformatics) data workflows.
> Dr. Bauer and her team have built solutions which use modern architectures, such as serverless (AWS Lambda) and also customised machine learning on Apache Spark. AWS Community Hero and cloud architect Lynn Langit is also collaborating with the CSIRO team to push solutions at the cutting edge of bioinformatic research which best utilise advances in cloud technologies..
> In this demo-filled session Lynn and Denis will discuss and demonstrate some of the latest cloud data pipeline work that they’ve been working together to build out for the bioinformatics community. 

* Building a platform for use of big data in genomics
    * Looking for 4 letters in 3-billion letter genome
    * Bioninformatician working with Developer to help build platform
* Platform
    * CSIRO [VariantSpark](http://bioinformatics.csiro.au/variantspark)
    * Based on [Databricks](https://databricks.com/) + Apache Spark
	* Future
    	* Python API
	* Spark as a Service doesn't exist
		* Researchers don't have internal IT expertise to tune Spark clusters etc
		* But for now they have to use Spark Server Cluster
* Random Forests
    * Decision Trees are the funamental primitive
        * A -> All people with X
        * B -> All people without X
* Scale
    * 50M vars + 10k samples
    * Scales linearly
    * Economies
    * $9k for a test run on AWS(!)
* GTC-Scan2
    * Genome Search Engine
    * Using standard cloud service too expensive
		* Cost vs Scale
	* Serverless
		* Lambda
		* S3
		* DynamoDBDB
		* API Gateway
	* Logs
		* Amazon Watchlogs
		* Hard to make sense with multiple Lambdas, DBs etc
        * Log readers emerging to deal with noise
			* X-Ray
			* Annotations now possible
		* Use to find functions
			* Being called more often than others
			* Using more time than others
			* Example: 2 mins to 30 sec, 75% $$$ saving
	* Lambdas spawn lambdas
	* Looking at service value
		* State service example
		* Useful, but not enough to justfiy cost
