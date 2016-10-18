=====================================================
About Containers
=====================================================

.. tag containers_summary

Containers are an approach to virtualization that allows a single operating system to host many working configurations, where each working configuration---a container---is assigned a single responsibility that is isolated from all other responsibilities. Containers are popular as a way to manage distributed and scalable applications and services.

.. end_tag

Habitat
=====================================================
Habitat packages may be exported with the supervisor directly into a Docker or ACI-formatted container, but frequently the container itself will run within a container orchestrator such as Kubernetes or Mesos. Container orchestrators provide scheduling and resource allocation, ensuring workloads are running and available. Containerized Habitat packages may run within these runtimes, managing the applications while the runtimes handle the environment surrounding the application (ie. compute, networking, security).

Apache Mesos and DC/OS
-----------------------------------------------------
Apache Mesos is an open source distributed systems kernel and the distributed systems kernel for Mesosphere's DC/OS distributed platform. The hab pkg export mesos command can create native Mesos containers from Habitat packages and launch them as applications within the Marathon .

Kubernetes
-----------------------------------------------------
Kubernetes is an open source container orchestator embedded in several distributed platforms including Google's Container Engine and CoreOS' Tectonic. Habitat packages are supported in both Docker and ACI container formats and can be deployed within Kubernetes.

Chef for Containers
=====================================================
Chef can manage a containers in a number of ways. This page is a quick summary of the tools and resources that are available. Some of these tools are developed and maintained by Chef itself and some are developed and maintained by the Chef community.

Base Containers
-----------------------------------------------------
The following cookbooks are available to help manage base containers:

* Use the `docker cookbook <https://supermarket.chef.io/cookbooks/docker>`__ to install and manage Docker, as well as use resources for managing Docker images, Docker containers, and the Docker registry
* Use the `lxc cookbook <https://supermarket.chef.io/cookbooks/lxc>`__ to install and manage LXC-based Linux containers
* Use the `zone cookbook <https://supermarket.chef.io/cookbooks/zone>`__ to manage Solaris zones, which are partitioned operating system-level virtual environments that are unique to the Solaris platform and are often referred to as "Solaris Containers"

Service Discovery
-----------------------------------------------------
The following cookbooks are available to help manage service discovery:

* Use the `chef-etcd cookbook <https://github.com/ranjib/chef-etcd>`__ to read and write keys/values in ``etcd``, as well as saving chef-client run data within ``etcd``; use the `etcd cookbook <https://supermarket.chef.io/cookbooks/etcd>`__ cookbook to set up ``etcd``
* Use the `consul cookbook <https://supermarket.chef.io/cookbooks/consul>`__ to set up the Consul client, server, and user interface
* Use the `serf cookbook <https://supermarket.chef.io/cookbooks/serf>`__ to set up and manage Serf
* Use the `zookeeper cookbook <https://supermarket.chef.io/cookbooks/zookeeper>`__ to set up and manage ZooKeeper, which also provides an interface for modifying the ZooKeeper cluster configuration

Schedule and Resources
-----------------------------------------------------
The following cookbooks are available to help manage schedule and resource allocation:

* Use the `mesos cookbook <https://supermarket.chef.io/cookbooks/mesos>`__ to set up and manage the Apache Mesos framework
* Use the `marathon cookbook <https://github.com/mdsol/marathon_cookbook>`__ to set up and manage Mesosphere Marathon, framework for long-running services that runs on Apache Mesos
* Use the `chronos cookbook <https://github.com/mdsol/chronos_cookbook>`__ to set up and manage Chronos, a fault-tolerant job scheduler that handles dependencies and iso8601-based schedules and runs on Apache Mesos
* Use the `kubernetes cookbook <https://github.com/chenzhiwei/kubernetes-cookbook>`__ to set up and manage Kubernetes on Red Hat and CentOS 7.x
* Use the `k8s cookbook <https://supermarket.chef.io/cookbooks/k8s>`__ to deploy Kubernetes entities, such as pods, replication controllers, and services

Build Container Images
-----------------------------------------------------
Use `Packer <http://packer.io>`__ to build any infrastructure image type with the chef-client or chef-solo as the provisioner. This enables the use of Chef to declaratively state what an infrastructure image should be, and then use Chef to easily manage lightweight immutable infrastructure images. Packer has support for Docker as a build target and can push images to the Docker registry as a post-processor.

Provisioning
-----------------------------------------------------
Chef provisioning, a collection of resources and drivers that is maintained by Chef includes a driver for Docker.

* Use the `machine and machine-based resources <https://docs.chef.io/devkit/#chef-provisioning-title>`__ to build and define recipes that manage Docker images
* Use the `docker driver <https://github.com/chef/chef-provisioning-docker>`__ to tell the chef-client how to build and define the Docker image itself

Infrastructure Testing
-----------------------------------------------------
Kitchen---the infrastructure testing system for Chef---may be configured to use containers by using the following drivers:

* For Docker, use the `kitchen-docker <https://github.com/portertech/kitchen-docker>`__ driver
* For LXC containers, use the `kitchen-lxc <https://github.com/chrisroberts/kitchen-lxc>`__ driver

APIs
-----------------------------------------------------
Use the  `docker-api <https://github.com/swipely/docker-api>`__ gem to interact programmatically with the Docker API from within Chef recipes. Chef is a contributor.

For more information ...
=====================================================
For more information about managing a containerized infrastructure:

* Cooking Up Drama - ChefConf 2015: https://www.youtube.com/watch?v=8fcDZB-QMRA
* Baking Docker Using Chef - ChefConf 2015: https://www.youtube.com/watch?v=5NiJ03r8h9E
* Using Habitat: https://www.habitat.sh/docs/container-orchestration/
