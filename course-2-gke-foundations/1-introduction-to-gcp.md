# Module 1: Introduction to Google Cloud Platform

- Cloud computing has five fundamental attributes:
  - Computing resources are ***on-demand*** and ***self-service***.
  - Resources are accessible *over a network from any location*.
  - Providers allocate resources to customers from a *large pool*, allowing them to benefit from economies of scale.
  - Customers pay for only *what they use or reserve* as they go.
- Google Cloud provides resources in ***multi-region***, ***regions***, and ***zones***. It divides the world up into three multi-regional areas, the *Americas*, *Europe*, and *Asia Pacific*. Next, the three multi-regional areas are divided into regions, which are independent geographic areas on the same continent. Within a region, there's fast network connectivity, generally *round-trip network latencies of under a millisecond, and that's at the 95th percentile*. Finally, regions are divided into zones, which are deployment areas for GCP resources within a focus geographic area.
- Google's datacenters around the world are *interconnected by the Google network*, which by some publicly available estimates, carries as much as *40 percent* of the world's Internet traffic every day.
- When an Internet users sends traffic to a Google resource, Google responds to the user's request from an ***edge network location*** that'll provide the lowest latency or delay. Google's edge caching network places the content close to users to minimize that latency.
- ***Zonal resources*** operate within a *single zone*, which means that if the zone becomes unavailable, the resources won't be available either. A simple example would be a Compute Engine virtual machine instance and its persistent disks.
- ***Regional resources*** operate across multiple zones, but within one region. Now, application using these resources can be redundantly deployed to improve its availability.
- ***Global resources (multi-regional)*** can be managed across multiple regions. These resources can further improve the availability of an application. Some example of such resources include HTTPS load balancers and VPC or virtual private cloud networks, which GKE users benefit from too.
