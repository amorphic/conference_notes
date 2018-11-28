# Don’t be a fail whale: secure your containers
## Sarah Young

* Threats
	* Contianer image
	* Orchestrator
* Auditing
	* Docker Bench Security
		* From Docker
		* Sets Baseline
	* OpenSCAP
		* PCI-DSS
		* STIG
		* FISMA
* Image security
    * The most important thing!
	* Notary image repo
	* Digitally signs images to be pubished
	* Also: Clair
* Heuristics/IDS
	* Sysdig Falco
	* Detects anomalous activity
	* Requires analysis
* Orchestrator/control channel security
	* E.g. Rancher - management for Kubernetes has security features
* Vulnerability scanning
	* Tenable Flawcheck/Container security
