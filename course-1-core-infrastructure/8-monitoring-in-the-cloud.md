# Module 8: Developing, Deploying and Monitoring in the Cloud

- ***Cloud Source Repositories*** provides Git version control to support team's development of any application or service, including those that run on App Engine, Compute Engine, and Kubernetes Engine.
- Cloud Source Repositories also contains a source viewer so that you can browse and view repository files from within the GCP console.
- ***Cloud Functions*** can trigger on events in *Cloud Storage*, *Cloud Pub/Sub*, or in *HTTP call*.
- ***Deployment Manager*** is an ***Infrastructure Management Service(Infrastructure as a Code)*** that automates the creation and management of Google Cloud Platform resources.
- Deployment Manager relies on a ***template file*** using either the `YAML` markup language or Python that describes the components of the environment.
- ***Stackdriver*** is GCP's tool for monitoring, logging and diagnostics. Stackdriver gives access to many different kinds of signals from GPC infrastructure platforms, virtual machines, containers, middleware and application tier, logs, metrics and traces.
- Stackdriver's core components: *Monitoring*, *Logging*, *Trace*, *Error* *Reporting* and *Debugging*.
- ***Stackdriver Monitoring*** checks the endpoints of web applications and other Internet accessible services running on our cloud environment. We can configure *uptime checks* associated with URLs, groups or resources such as Instances and load balancers. We can set up *alerts* on interesting criteria, like when health check results or uptimes fall into levels that need action.
- ***Stackdriver Logging*** also lets us define *metrics*, based on log contents that are incorporated into dashboards and alerts. We can also export logs to *BigQuery*, *Cloud Storage* and *Cloud PubSub*.
- ***Stackdriver Trace*** samples the latency of app engine applications and report Per-URL statistics.