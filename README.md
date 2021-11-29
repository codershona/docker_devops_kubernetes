# Docker Handbook

<p align="center">
	
<img src="https://user-images.githubusercontent.com/57604500/125166578-8f48e900-e19c-11eb-84f3-6dc7bed3e2ac.png" width=456>
<br />
<h3 align="center">👨🏻‍💻 DOCKER HANDBOOK PROCESS</h3>
</p>


<br/>
<br/>

### Docker Creating and Using Container

* Check Our Docker Install and Config
* Starting a Nginx Web Server
*  Debrief: What Happens When We Run a
Container
*  Container VS. VM: It's Just a Process
*  Windows Containers: Docker Is No Longer Just
Linux
* Assignment: Manage Multiple Containers
Containers
* What's Going On In Containers: CLI Process
Monitoring
* Getting a Shell Inside Containers: No Need for
SSH
* Docker Networks: Concepts for Private and
Public Comms in Containers
* FIXME: Change In Official Nginx Image
Removes Ping
* Docker Networks: CLI Management of Virtual
Networks
*  Docker Networks: DNS and How Containers
Find Each Other
* Assignment: Using Containers for CLI Testing
* FIXME: Bug in alpine affects nslookup
* Assignment: DNS Round Robin Test
 
### Docker Container Images

 * What's In An Image (and What Isn't)
 * The Mighty Hub: Using Docker Hub Registry
Images
 * Images and Their Layers: Discover the Image
Cache
 * Image Tagging and Pushing to Docker Hub
 * Building Images: The Dockerfile Basics
 * Building Images: Running Docker Builds
 * Building Images: Extending Official Images
 * Assignment: Build Your Own Dockerfile and
Run Containers From It
 * Using Prune to Keep Your Docker System Clean


### Container Lifetime & Persistent Data: Volumes, Volumes, Volumes
* Container Lifetime & Persistent Data
* Persistent Data: Data Volumes
* Shell Differences for Path Expansion
* Persistent Data: Bind Mounting
* Assignment: Database Upgrades with Named
Volumes
*  Assignment: Edit Code Running In Containers
With Bind Mounts
* Database Passwords in Containers

###  Docker Compose: The Multi-Container Tool
* Docker Compose and The docker-compose.yml
File
* Trying Out Basic Compose Commands
* Assignment: Build a Compose File For a
Multi-Container Service
* Adding Image Building to Compose Files
* Assignment: Compose For Run-Time Image
Building and Multi-Container Development

### Swarm Intro and Creating a 3-Node Swarm Cluster

* Swarm Mode: Built-In Orchestration
* Create Your First Service and Scale It Locally
*  UI Change For Service Create/Update
*  Docker Machine Bug With Swarm
* Creating a 3-Node Swarm Cluster

### Swarm Basic Features and How to Use Them In Your Workflow
### Swarm App Lifecycle
### Container Registries: Image Storage and Distribution
### Docker in Production
### What and Why of Kubernetes

* Kubernetes = popular with Orchestration.
* Container Orchestration = Make many server acts like one
* Kubernetes, also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications.
* Runs on the top docker as a set of APIs in Containers.
* Many clouds for it for you.
* Many "vendors" make a distribution of it.
* It provides API/CLI to manage containers across servers.

#### Reasons uses of Kubernetes

* By reviewing swarm mode: built-in orchestration.
* Orchestration: Next logical steps in journey tofaster DevOps.
* We need to understand the reason orchestration is required.
* Not every solution needs orchestration.
* Servers + Change Rate = Advantages of Orchestration.
* Next make a decision to choose orchestration.
* While Kubernetes make decision to use which distribution for example, cloud or self management like Docker Enterprise, OpenShift, Rancher, Canonical and VMWare PKS) and we do not usually need the pure upstream.

#### Kubernetes or Swarm:

* These two both are containers orchestrators.
* Both had solid platform with vendors backing.
* Swarm is easir to deploy and manage.
* Kubernetes have many features and moe flexibility.

#### Benefits of Docker Swarm:

* It comes with Docker woth single vendor platform.
* It has easier to troubleshoot.
* It has secure defult.
* It has easier orchestrators to deploy and manage yourself.
* It can runs anywhere in docker like, local or cloud or datacenter as well as ARM or windows or 32-bit.

##### Benefits of Kubernetes:

* The cloud would deploy and manage Kubernetes for you.
* The infrastructure vendors are making their own distribution.
* It has widest adoption and community.
* It is flexible to cover widest sets of use cases.
* It has first vendor support. 
* It has CTO/CIO Checkbox.

### Kubernetes Install And Your First Pods

* Check out Kubernetes or k8's Components.
* The whole orchestration system is Kubernetes.
* k8 or kube for short.
* KubeCTL: CLI to configure Kubernetes and manage the apps.
* We can also say this cube controls.
* Node.js is basically usd for Single Server in Kubernetes Cluster.
* Kublet means Kubernetes basically runs agent on nodes.
* Control Plane has a set of containers that manage the clusters. This includes API server, Scheduler, Controller Manager and more.
* It also sometimes known as master.

### Exposing Kubernetes Ports
### Kubernetes Management Techniques
### Moving to Declarative Kubernetes YAML
### The Future of Kubernetes
### Docker Security Good Defaults and Tools
### Docker 19.03 Release New Features
### DevOps and Docker Clips
### Dockerfile and Compose File Reviews
### Commonly Asked interview Question
