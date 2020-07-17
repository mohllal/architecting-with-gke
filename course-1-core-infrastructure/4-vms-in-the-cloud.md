# Module 4: Virtual Machines in the Cloud

- The Virtual Private Cloud networks have ***global scope***. They can have subnets in any GCP region worldwide and subnets can span the zones that make up a region. Subnets have ***regional scope***.
- We can dynamically increase the size of a subnet in a custom network by expanding the range of IP addresses allocated to it. Doing that doesn’t affect already configured VMs.
- A preemptible VM is different from an ordinary Compute Engine VM in only one respect, compute engine has the permission to terminate it if it's resources are needed elsewhere.
- Much like physical networks, VPCs have ***routing tables***. These are used to forward traffic from *one instance to another instance* within the same network. Even *across sub-networks* and even *between GCP zones* without requiring an external IP address.
- We can simply establish a *peering relationship between two VPCs* so that they can exchange traffic, that's what ***VPC Peering*** does. On the other hand, if we want to use the full power of IAM to control who and what in one project can interact with a VPC in another, that's what ***Shared VPC*** is for.
- ***Cloud Load Balancing*** is a fully distributed, software-defined managed service for all traffic. We don't have to worry about scaling or managing them. We can put Cloud Load Balancing in front of all our traffic - *HTTP and HTTPS*, other *TCP and SSL* traffic, and *UDP* traffic too.
- With Cloud Load Balancing, ***a single anycast IP*** frontends all our backend instances in regions around the world. It provides ***cross-region load balancing***, including ***automatic multi-region failover***, which gently moves traffic in fractions if backends become unhealthy. Cloud Load Balancing reacts quickly to changes in users, traffic, backend health, network conditions, and other related conditions.
- Google VPC offers a suite of load-balancing options:
  - Global HTTP(S): For HTTP or HTTPS traffic.
  - Global SSL: For non-HTTPS SSL traffic.
  - Global TCP: For non-SSL TCP traffic.
  - Regional: For any TCP or UDP traffic.
  - Regional internal: For internal traffic inside VPC.
- Google has a highly developed DNS infrastructure. It makes ***8.8.8.8*** available so that everybody can take advantage of it. But what about the internet host names and addresses of applications built in GCP? GCP offers ***Cloud DNS*** to help the world find them. It's a managed DNS service running on the same infrastructure as Google. It has low latency and high availability and it's a cost-effective way to make applications and services available to end-users.