# Module 3: Kubernetes Architecture

- Each thing Kubernetes manages is represented by an ***object***, and we can *view* and *change* these objects, attributes, and state.
- Kubernetes follows the principle of ***declarative management*** as it expects us to tell it what we want the state of the objects under which management to be. It will work to bring to that state into being and keep it there.
- Various kinds of objects represent containerized applications, ***the resources that are available to them***, and the ***policies that affect their behavior***.
- Kubernetes objects have two important elements:
  - ***Objects spec***: With this spec, we define the ***desired state*** of the object by providing the characteristics that we want.
  - ***Object status***: It is simply the ***current state*** of the object provided by the Kubernetes control plane.
- Kubernetes ***control plane*** are the various *system processes* that collaborate to make a Kubernetes cluster work.
- Each object is of a certain type or ***kind***, as Kubernetes calls them.
- ***Pods*** are the *basic building block* of the standard Kubernetes model, and they're the ***smallest deployable Kubernetes object***. ***Every running container in a Kubernetes system is in a pod***. A pod embodies the environment where the containers live, and that environment *can accommodate one or more containers*.
- If there is more than one container in a pod, they are tightly coupled and *share resources including networking and storage*. Kubernetes assigns ***each pod a unique IP address***. Every container within a pod shares the network namespace including IP address and network ports. ***Containers within the same pod can communicate through local host, the famous 127.0.0.1 IP address***.
- Kubernetes consists of one VM called ***master*** and one or more VMs called ***nodes***. The job of the *nodes is to run pods*, the job of the *master is to coordinate the entire cluster*.
- Kubernetes master consists of multiple components:
  - ***Kube-API*** server: This components job is to *accept commands that view or change the state of the cluster*, including launching pods. Kube-API also ***authenticates*** incoming requests, determines whether they are authorized and valid, and ***manages admission control***.
  - ***ETCD*** is the ***cluster's database***. It's job is to *reliably store the state of the cluster*, this includes all of the cluster configuration data and more dynamic information, such as what nodes are part of the cluster, what pods should be running, and where they should be running.
  - ***Kube-scheduler*** is responsible for ***scheduling pods onto the nodes***. To do that, it evaluates the requirements of each individual pod, and select which node is most suitable. But it doesn't do the work of actually launching pods onto nodes. Instead, whenever it discovers a pod object that doesn't yet have an assignment to a node, *it chooses a node and simply writes the name of that node into the pot object*.
  - ***Kube-controller*** manager has abroad or job. It continuously ***monitors the state of a cluster through Kube-API server***, who whenever the current state of the cluster doesn't match the desired state, Kube-controller manager will attempt to make changes to achieve the desired state. It's called the controller manager because *many Kubernetes objects are maintained by loops of code called controllers*. These loops of code, handle the process of remediation.
  - ***Kube-cloud-manager*** manages controllers that interact with underlying cloud providers. For example, if we manually launched a Kubernetes cluster on Google Compute Engine, Kube-cloud-manager would be responsible for bringing in GCP features like load balancers and storage volumes when we needed them.
- Kubernetes node consists of multiple components:
  - ***Kubelet*** is the ***Kubernetes agent*** on each node. When the *Kube-API server wants to start a pod on a node, it connects to that node's Kubelet*. ***Kubelet uses the container run-time to start the pod, and monitors its lifecycle, including readiness and liveness probes, and reports back to Kube-API server***.
  - ***Kube-proxy***'s job is to ***maintain network connectivity among the pods in a cluster***. In open-source Kubernetes, it does so using the *firewall and capabilities if IP tables*, which are built into the Linux kernel.
- ***How does Kube-scheduler decide where to run a pod***? It knows the state of all the nodes, and it will also obey constraints that we define on where a pod may run based on hardware, software, and policy.
- The world of Kubernetes offers several choices of container runtimes, but the Linux distribution that GKE uses for its nodes, launches containers using ***containerd***, The run time component of docker.
- There's an open-source command called `kubeadm`, ***that can automate much of the initial setup of a cluster***. But if a node fails or needs maintenance, a human administrator has to respond manually.
- GKE ***manages all the control plane components*** for us. It's still *exposes an IP address, to which we send all of our Kubernetes API requests*. But, ***GKE takes responsibility for provisioning and managing all the master infrastructure*** behind it. It also abstracts away having a separate master. ***The responsibilities of the master are absorbed by GCP***, and you are not separately billed for your Master.
- In any Kubernetes environment, ***nodes are created externally by cluster administrators***, not by Kubernetes itself. GKE automates this process for us. ***GKE launches Compute Engine virtual machine instances, and registers them as nodes***. We can still manage nodes settings directly from the GCP console. ***We pay per hour of life of our nodes, not counting the master***.
- GKE has a feature of ***selecting multiple node machine types by creating multiple node pools***. ***A node pool is a subset of nodes within a cluster that share a configuration, such as their amount of memory or their CPU generation***. Node pools also provide an easy way to ensure that workloads run on the right hardware within our cluster. *We just label them with a desired node pool*.
- GKE has various additional features such as **automatic node upgrades**, ***automatic node repairs***, and ***cluster auto-scaling*** at this node pool level.
- By default, a ***GKE cluster launches in a single GCP compute zone with three identical nodes. All in one node pool***. The number of nodes can be changed during or after the creation of the cluster. Adding more nodes and deploying multiple replicas of an application, will improve an applications availability.
- ***GKE regional cluster has a single API endpoint for the cluster***. However, it's ***masters and nodes are spread out across multiple Compute Engine zones within a region***. Regional clusters ensure, that the availability of the application is maintained across multiple zones in a single region. In addition, the availability of the master is also maintained. So that both, *the application and management functionality, can withstand the loss of one or more, but not all zones*. ***By default or regional, cluster is spread across three zones, each containing one master and three nodes***. These numbers can be increased or decreased.
- ***Private GKE Cluster masters can be accessed by Google Cloud products***, such as Stackdriver, through an internal IP address. They ***can also be accessed by authorized networks through an external IP address***. Authorized networks are basically IP address ranges, that are trusted to access the master.
- All Kubernetes objects are identified by a ***unique name*** and a ***unique identifier***. We define the objects we want Kubernetes to create and maintain with ***manifest files***. These are ordinary text files. You may write them in ***YAML*** or ***JSON*** format.
- ***API version*** describes which Kubernetes API version is used to create the object. The Kubernetes protocols version so as to help maintain backwards compatibility.
- ***Kind***, defines the object type, and ***metadata*** helps identify the object using name, unique id, and an optional namespace.
- YAML files ***should be saved in version controlled repositories***. This practice makes it easier to track and manage changes and to back out those changes when necessary. It's also a big help when we need to recreate or restore a cluster.
- ***Only one object of a particular kind can have a particular name at the same time in a Kubernetes namespace***. However, if an object is deleted, it's name can be reused. Alphanumeric characters, hyphens, and periods are allowed in the names with a maximum character length of 253.
- ***Each object generated throughout the life of a cluster has a unique ID generated by Kubernetes***. This means that no two objects will have the same UID throughout the life of a cluster.
- *Labels are key value pairs* with which we tag our objects during or after their creation. Labels help us identify and organize objects and subsets of objects.
- Pods don't heal or repair themselves and they're not meant to run forever. They are designed to be ephemeral and disposable.
- A Kubernetes service is a ***static IP address*** that represents a service or a function in your infrastructure. It's a *network abstraction for a set of Pods* that deliver that service. It hides the ephemeral nature of the IP addresses of the individual Pods.
- The Pods are selected using a label selector. By the way, you can also get a service quickly, by asking Kubernetes to expose a deployment. When you do that, Kubernetes handles selecting the right Pods for you.
- Whenever a service is created, ***Kubernetes automatically creates endpoints for the selected Pods*** by creating endpoint resources. By default, ***the master assigns a virtual IP address*** also known as a cluster IP to the service from internal IP tables. With GKE, this is assigned from the clusters VPC network.
- A container application can easily write data to the read-write layer inside the container, but it's ephemeral. *So when the container terminates, whatever was written will be lost*.
- ***Kubernetes volume*** is simply *a directory that is accessible to all the containers in a Pod*. The requirements for a volume are defined through the *Pod's specification*. This declares how the directory is created, what storage medium should be used, and its initial contents.
- A failing node or deleted Pod could be due its volume being deleted too. To avoid this, we can configure volumes using ***network-based storage from outside of our Pods***, to provide durable storage that is not lost when a Pod or node fails.
- Some examples of controller objects; ***deployments***, ***StatefulSets***, ***DaemonSets*** and ***Jobs***.
- Kubernetes allows us to ***abstract a single physical cluster into multiple clusters known as namespaces***. Namespaces provide scope for naming resources such as pods, deployments, and controllers.
- There are *three initial namespaces* in the cluster:
  - The ***default*** namespace, for objects with no other namespace defined.
  - The ***Kube-system*** namespace for objects created by the Kubernetes system itself.
  - The ***Kube-public*** namespace for objects that are publicly readable to all users. Kube-public is a tool for disseminating information to everything running in a cluster.
- Services ***provide load-balanced access to specified Pods***. There are three primary types of Services:
  - ***ClusterIP***: Exposes the service on an IP address that is only accessible from within this cluster. This is the default type.
  - ***NodePort***: Exposes the service on the IP address of each node in the cluster, at a specific port number.
  - ***LoadBalancer***: Exposes the service externally, using a load balancing service provided by a cloud provider.
- In Google Kubernetes Engine, LoadBalancers give us access to a ***regional Network Load Balancing configuration by default***. To get access to a global HTTP(S) Load Balancing configuration, we can use an Ingress object.
- Kubernetes controller objects:
  - ***ReplicaSets***: Ensures that a population of Pods, all identical to one another, are running at the same time.
  - ***Deployments***: Manages their own ReplicaSets to achieve the declarative goals we prescribe. Deployments let you create, update, roll back, and scale Pods, using ReplicaSets as needed to do so
  - ***Replication Controllers***: Replication Controllers perform a similar role to the combination of ReplicaSets and Deployments, but their use is no longer recommended. Because Deployments provide a helpful "front end" to ReplicaSets.
  - ***StatefulSets***: A StatefulSet is similar to a Deployment in that the Pods use the same container spec. however; by contrast, Pods created using StatefulSet have ***unique persistent identities with stable network identity and persistent disk storage***.
  - ***DaemonSets***: DaemonSet ensures that *a specific Pod is always running on all or some subset of the nodes*. If new nodes are added, DaemonSet will automatically set up Pods in those nodes with the required specification.
  - ***Jobs***: The Job controller *creates one or more Pods required to run a task*. When the task is completed, Job will then terminate all those Pods. A related controller is ***CronJob***, which runs Pods on a time-based schedule.
- When we perform a rolling upgrade of a Deployment, the Deployment object *creates a second ReplicaSet*, and then increases the number of Pods in the new ReplicaSet as it decreases the number of Pods in its original ReplicaSet.
- A Kubernetes cluster might use a DaemonSet to ensure that a logging agent like ***fluentd*** is running on all nodes in the cluster.