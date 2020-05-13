# Tunnel Snakes Rule!
## Evan Brumley

* How to track?
    * Old approach
        * Buy/rent sensors
        * Install onsite temporarily
        * Pull csv data and use excel
    * Modern approach
        * Proprietary Sensors
        * SaaS platform
        * Too generic - still end up pulling csv and using excel
* Requirements
    * Collect
        * Noise, vibration, air quality
        * Variety of sensors
    * Validate
        * Peak load 1 billion records/month
        * Losing data is critical - audits possible
    * Analyse and process telemetry
        * Env requirements don't map cleanly to sensor data points
        * Calculations complex and liable to change
        * Near real-time
    * Provide Access
        * Access to raw data and analysis for internal teams
        * External access to limited data sets
        * Near real-time
    * Alerting
    * Reporing
        * Alerts documented/resolved
        * PDFs sent to stakeholders
* Timeframe
    * Four months
    * Hard deadline - construction work had to start
    * 6 more months for feature complete
* Team
    * Joint dev team (two companies)
    * Average 2-3 devs + 1 PM at any one time
    * People swapped in and out
    * Fully self contained because not owned by any one org
        * Bitbucket
        * AWS
        * KIRA
* Build
    * Device Agent
        * Collects Device Readings
        * Pulls data from device or receives data from device
        * Publishes data to platform
        * Implementation
            * API Polling 
                * Python scripts polling vendor API
                * Packaged into Docker containers and deployed via Elastic Beanstalk
                * Simple state maintained in AWS DynamoDB (device/timestamp: state)
                * Heavily multithreaded - could be done better with asyncio
            * FTP Server receiving
                * Custom via pyftpdlib
                * Allows for event callbacks (e.g. whena file is uploaded - parse/extract/push to pipe)
                * TCP Load balanced (TCP Proxying)
    * Buffer Device Readings
        * Kinesis pipeline
    * Log For Audit
        * Takes sensor data
        * Wraps in JSON blob (timestamp, etc) in Lambda
        * Kinesis Firehose -> S3
    * Streaming Analytics
        * Validate and Store (not in Python)
        * Implementation
            * InfluxDB
            * Apache Flink
                * Scala
            * Buffering/Checkpointing/Error handling is important if (eg InfluxDB goes down)
            * Kinesis Streaming Analytics
                * Fully managed Flink service - use this!
    * Analysis
        * Django + Celery + React
        * Alerting rules using Django admin
        * Read-only access to TSDB
        * Lots of Pandas + Scipy
            * Transform raw data live and on request
            * Backs onto InfluxDB
            * You can get away with on-demand processing because dataframes are awesome!
* Other
    * Perform rollups at different points in the system (even on the agents if required!)
