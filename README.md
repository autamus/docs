# Autamus Docs
### What is Autamus?
Autamus is a semi-autonomous build system for scientific containers. But what exactly do we mean by that? 

Well, Autamus is a software system that builds and maintains a curated repository of common scientific and open source containers. Unlike typical containers however, Autamus builds every application within a container completely from source. Building all applications from source, Autamus containers improve security by transparently verifying a program originated from it's publicly available source code. In additon to better security, building applications from source also means that Autamus containers can be optimized to be both smaller and faster than their more traditional counterparts.

#### So How Does Autamus work?

When a new version of a scientific/open source application is released, Autamus automatically spins up to recompile all of the containers built on top of that application from scratch. The results of those build are then submitted to our team of maintainers as pull requests on the [Autamus Registry Repository](https://github.com/autamus/registry/pulls) to verify and accept before then being published.

#### What Does This Mean For You As A Researcher/Developer?

Using containers built by Autamus, you can install all of the software you need in one easy package. Then easily move your workflows between laptops, servers, and HPC clusters all while using the same container to drastically increase the portability of your research. Finally, don't worry about your containers using up all of your available disk space because Autamus strips out everything except the software you actually need in your container.

### Getting Started with Autamus Containers
Check out the [getting started section](getting-started/index.md) to start using containers in your workflows today.


#### Container Size Comparisons
| **Package/Container Name** | **Autamus Container Size** | **Official Dockerhub Container Size** |
|----------------------------|----------------------------|---------------------------------------|
| Python                     | 417MB                      | 885MB                                 |
| R                          | 517.9MB                    | 761.2MB                               |
| GCC                        | 1.731GB                    | 1.186GB                               |
| Go                         | 751.2MB                    | 861.9MB                               |
