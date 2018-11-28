# How Python saved a rescue dog - a foster fail story
## Andreas Moll

* Version 1
    * Onion Omega2
    * Full linux + Python
    * Script polling -> Flask/Redis
* Version 2
    * Gateway Service
    	* pI3
    	* Web service / RESTful
    	* Docker container + compose + registry
		* Service discovery
	    * Consul Server
	    * Registrator
    * Feeder: Servo1/Servo
	    * PiZero
	    * Consul Agent
		* Registrator
    * Lamp
	    * PiZero
	    * Consul Agent
		* Registrator
* Version <future>
    * Websockets instead of polling
	* Events with MQTT
	* Web interface (react)
