# Module 7: Applications in the Cloud

- The App Engine platform manages the *hardware and networking infrastructure* required to run your code.

- App Engine provides a built-in services that many web applications need. *NoSQL databases*, *in-memory caching*, *load balancing*, *health checks*, *logging* and a way to *authenticate* users.

- App engine ***will scale the application automatically*** in response to the amount of traffic it receives.

- App Engine ***Standard*** Environment offers a simpler deployment experience than the ***Flexible*** environment and fine-grained auto-scale. Like the Standard Environment, it also offers a free daily usage quota for the use of some services.

- In App Engine Standard Environment, you use a runtime provided by Google. App Engine Standard Environment provides runtimes for specific versions of *Java*, *Python*, *PHP* and *Go*. The runtimes also include libraries that support App Engine APIs.

- The Standard Environment also enforces restrictions on the code by making it run in a so-called ***Sandbox***. That's a software construct that's *independent of the hardware, operating system, or physical location* of the server it runs on.

- In App Engine flexible environment the application runs inside *Docker containers* on Google Compute Engine Virtual Machines, VMs. App Engine manages these Compute Engine machines. They're *health checked*, *healed as necessary*, and we get to choose which geographical region they run in, and critical *backward-compatible updates* to their operating systems are automatically applied.

- Comparing the App Engine environments
  
  |                     | Standard Environment    | Flexible Environment                  |
  | ------------------- | ----------------------- | ------------------------------------- |
  | Instance startup    | Milliseconds            | Minutes                               |
  | SSH access          | No                      | Yes (not by default)                  |
  | Write to local disk | No                      | Yes (writes are ephemeral)            |
  | 3rd-party support   | No                      | Yes                                   |
  | Network access      | Via App Engine services | Yes                                   |
  | Pricing model       | Pay per instance class. | Pay per resource allocation per hour. |

- Comparing the App Engine environments VS Kubernetes Engine
  
  |                  | Kubernetes Engine          | App Engine Flexible                         | App Engine Standard          |
  | ---------------- | -------------------------- | ------------------------------------------- | ---------------------------- |
  | Language support | Any                        | Any                                         | PHP, Python, Go, and Java    |
  | Service model    | Hybrid                     | PaaS                                        | PaaS                         |
  | Primary use case | Container-based workloads. | Web and mobile + container-based workloads. | Web and mobile applications. |

- ***Cloud Endpoints*** implements many capabilities using an easy to deploy proxy in front of software services, and it provides an API console to wrap up those capabilities in an easy-to-manage interface.

- ***Apigee Edge*** is also a platform for developing and managing API proxies. It has a different orientation though. It has a focus on *business problems like rate limiting, quotas, and analytics*.
