# Autamus Docs
### What is Autamus?
Autamus is a semi-autonomous build system for scientific containers. But what exactly do we mean by that? 

Well, Autamus is a software system that builds and maintains a curated repository of common scientific and open source containers. Unlike your typical container however, Autamus builds every application within a container completely from source. Building applications from source allows Autamus to optimize containers to be smaller and better suited to HPC environments than their generically installed counterparts. Application security is also improved building containers from source since each container can be transparently verified as coming from a project's source code.

#### So How Does Autamus work?
When a new version of a scientific/open source application is released, Autamus automatically spins up to recompile all of the containers built on top of the updated application from scratch. The results of those builds are then submitted to our team of maintainers as pull requests on the [Autamus Registry Repository](https://github.com/autamus/registry/pulls) to verify before then being published. Although Autamus is semi-autonomous when finding updates, a human is always in the loop before a piece of software is published.

#### What Does This Mean For You As A Researcher/Developer?
Using containers built by Autamus, you can install all of the software you need for your analysis in one container package. Then easily move your workflows between laptops, servers, and HPC clusters all while using the same container to drastically increase the portability of your research. Finally, don't worry about your containers using up all of your available disk space since Autamus strips out everything except the software you actually need in your container.

When on your laptop or a cloud virtual machine, Autamus containers can natively be used with [Docker](https://www.docker.com) or [Podman](https://podman.io). If you are using a University or National Lab Cluster, check out [Singularity-HPC](https://singularity-hpc.readthedocs.io/en/latest/) which let's you use Autamus containers as native software modules.

### Getting Started with Autamus Containers
Check out the [getting started section](getting-started/index.md) to start using containers in your workflows today.


#### Raw Container Size Comparisons
| **Package/Container Name** | **Autamus Container Size** | **Official Dockerhub Container Size** |
|----------------------------|----------------------------|---------------------------------------|
| Python                     | 417MB                      | 885MB                                 |
| R                          | 517.9MB                    | 761.2MB                               |
| Go                         | 751.2MB                    | 861.9MB                               |
| Rust                       |                            |                                       |
