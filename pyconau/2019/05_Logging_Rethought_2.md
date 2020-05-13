# Logging Rethought 2: The Actions of Frank Taylor Jr.
## Markus Holtermann

* Structure Logging
    * `import structlog`
    * fluentd -> Crate
* Tracing Events
    * `import uuid`
    * Use a uuid to trace events through the system 
    * `request.META.get('HTTP_HEADER_X_UUID')` if one exists, or create new one
    * Do the same for `userid` to track userid across calls
* Data
    * Be explicit about the specific fields you want to log
    * Don't log secret data (UUID)
