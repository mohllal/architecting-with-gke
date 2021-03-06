# Module 1: Introducing Google Cloud Platform

- ***Cloud computing*** is a way of using IT that has these five equally important traits:
  - First, we get computing resources *on-demand and self-service* by using a simple interface to get the processing power, storage, and network we need, with no need for human intervention.
  - Second, we access these resources *over the net from anywhere* we want.
  - Third, the provider of those resources *has a big pool* of them and allocates them to customers out of that pool.
  - Fourth, the resources are *elastic*.
  - Lastly, the customers *pay only for what they use or reserve as they go*. If they stop using resources, they stop paying.
- The cloud computing history:
  - The first wave of the trend that brought us towards cloud computing was ***colocation (user-configured, managed, and maintained)***, which IT shops have been doing for decades. Instead of building costly capital intensive data centers, they can rent space in shared facilities.
  - The second wave of the trend that brought us towards cloud computing was ***virtualization (user-configured. provider-managed and maintained)***. The components of a virtualized data center are separately manageable from the underlying hardware.
  - The third wave was a ***container based architecture, an automated elastic*** built from automated services.
- ***IaaS*** offerings provide raw compute, storage, and network organized in ways that are familiar from data centers. In the IaaS model, we pay for what we allocate.
- ***PaaS*** offerings, bind application code we write to libraries that give access to the infrastructure our application needs. In the PaaS model, we pay for what we use.
- As Cloud Computing has evolved, *the momentum has shifted towards managed infrastructure and managed services*.
- A ***zone*** is a deployment area for Google Cloud Platform Resources. A zone doesn't always correspond to a single physical building.
- Zones are grouped into ***regions***, independent geographic areas. Locations within regions usually *have round trip network latencies of under five milliseconds*.
- As part of building a fault tolerant application, we have to ***spread their resources across multiple zones in a region***. We can run resources in different regions too. Both to *bring our applications closer to users around the world*, and also to *protect against the loss of an entire region*, say, due to a natural disaster.
- Zone <> Region <> Multi-Region.
- Google gives customers the ability to run their applications elsewhere, if Google becomes no longer the best provider for their needs:
  - GCP services are compatible with open source products such as *Cloud Bigtable* and *Cloud Dataproc*.
  - Google publishes key elements of technology using open source licenses such as  *TensorFlow*.
  - Many GCP technologies provide interoperability such as *Google Stackdriver* which lets customers monitor their workloads across multiple cloud providers.
- Google Cloud Platform's products and services can be broadly categorized as *compute*, *storage*, *big data*, *machine learning*, *networking* and *operations and tools*.
- Google designs custom chips, including a hardware security chip called ***Titan*** that's currently being deployed on both servers and peripherals. Google's infrastructure provides *cryptographic privacy and integrity* for remote procedure called ***data-on-the-network***, which is how Google services communicate with each other.
- Most applications at Google access physical storage *indirectly* via ***storage services*** and encryption is built into those services. Google also enables hardware encryption support in hard drives and SSDs.
- Google services that want to make themselves available on the Internet register themselves with an infrastructure service called the ***Google Front End***, which checks incoming network connections for *correct certificates* and *best practices*. The GFE also additionally, *applies protections against denial of service attacks*.
- GCP provides four tools to help monitoring GCP bill: *budgets and alerts*, *billing, export*, *reports* and *quotas*.
- We can define ***budgets*** either *per billing account* or *per GCP project*. A budget can be a *fixed limit* or you can tie it to *another metric*.
- ***Billing export*** lets us store detailed billing information in places where it's easy to retrieve for more detailed analysis, such as a ***BigQuery dataset*** or a **Cloud storage bucket**.
- ***Reports*** is a visual tool in the GCP console that allows us to monitor our expenditure.
- ***Quotas*** are designed to prevent *the over-consumption of resources*, whether because of error or malicious attack. There are two types of quotas: ***rate quotas*** and ***allocation quotas***.
- Rate quotas *reset after a specific time*. Allocation quotas, on the other hand, *govern the number of resources* you can have in your projects.