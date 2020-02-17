# Risk and Gap Analysis

The file outlines the risks and mitigation (if any) about this
software and its recommended configuration

  * There is API rate limiting or DDoS protection. Therefore, it is possible 
    that a bad actor or misconfiguration upstream can bring down or severely
    degrade your application.
  * Logging is not sent to a remote server. Nor is it dumped to disk external
    to the container. Therefor it is possible that a long-running traefik
    process will generate enough logs to fill the host disk and crash
    the system. 