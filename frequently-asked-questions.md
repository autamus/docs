# Frequently Asked Questions

### How are Autamus Containers Different Than User Submitted Containers on Dockerhub?
[Dockerhub](https://hub.docker.com) is a fantastic large registry of containers submitted from users all across the world. Unfortunetly, Dockerhub is more of a storage and distribution system than Autamus. Dockerhub relies on developers building and uploading their own containers to the platform.

By contrast, Autamus aims to be a build system for developers. It detects new project releases daily and attempts to automatically build and optimize those project's source code releases as a ready to use container. Thus reducing the work needed by developers and system administrators to keep their software libraries always up-to-date. If you are a developer, watch how an update to your application affects others as Autamus attempts to rebuild all of the containers dependent on your project.

One of Dockerhub's key great features is it's ability for anyone to upload a container which is vastly increased the adoption of containers in the computing community. However, this means that there's little to no friction for someone to upload a container with malware attached to it. The isolation that containers provide makes this less of an issue but when working in high security environments or with sensative data Autamus helps users know exactly from what source code a container originated from.

### Who Are The People Behind Autamus?
A bunch of open source loving science nerds.

### What's the Backstory Behind Autamus?
At the end of my undergraduate freshman year, as my internship with the University's Research & HPC Computing group was finishing up, a friend (@bjoyce3) and I (@alecbcs) were talking about the software installed on our University's local HPC. In particular, how the age of many of the analysis packages (and their depedencies) were keeping us from updating the operating systems of the clusters. During that conversation, we started dreaming about "an autonoumous build system" for scientific containers. One that would update containers as new versions of their source code became available, rebuild containers as a package's depedencies received updates, and thoroughly test the containers before publishing them. During that following summer, I was hired on by the HPC Team and this idea became a multi-year project.

