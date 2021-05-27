# Quick Start

## Table of Contents
- [Prerequisites](#prerequisites)

## Prerequisites
To get started using an Autamus container you'll either need [Docker](https://docs.docker.com/get-docker/), [Podman](https://podman.io), or [Singularity-HPC](https://singularity-hpc.readthedocs.io/en/latest/). If you're on a University or National Lab computing cluster we recommend using Singularity-HPC since it'll allow you to install and use containers just as you would any other system module! If you're on a cloud virtual machine or your own laptop where having root access isn't an issue we recommend using Docker. Finally if you're on a Linux laptop or your own Linux server and want to try something awesome check out Podman!

## Downloading a Container
Once you've got one of those container engines installed downloading an Autamus container is easy! If you're using Docker or Podman, checkout the [Autamus Container Library](https://autamus.io/registry) to find a container you want to download.

If you are using Singularity-HPC, checkout the [SHPC Library](https://singularityhub.github.io/singularity-hpc/) to find an Autamus container to download.

Once you've got a container to download (for example Julia) run,
```bash
docker pull ghcr.io/autamus/julia:latest
```
if you're using docker. Or,
```bash
podman pull ghcr.io/autamus/julia:latest
```
if you're using podman. Or,
```bash
shpc install ghcr.io/autamus/julia:latest
```
if you're using Singularity-HPC.

## Updating a Container
To update a container once a newer version is available simply re-run these download commands again.

## Running a Program Within the Container
Depending on the container engine you are using running a program will have different syntax. If you're using Docker or Podman there are examples for each container in the [Autamus Container Library](https://autamus.io/registry) if you click on the name of a container.

If you are using Singularity-HPC checkout the examples for your container over at the [SHPC Library](https://singularityhub.github.io/singularity-hpc/) also by clicking on the name of the container.

## Building on Top of Autamus Containers
You can totally use Autamus containers as the base of your other containers by writing,
```Dockerfile
FROM ghcr.io/autamus/CONTAINER-NAME:latest
```
for example if you were writing a go application.
```Dockerfile
FROM ghcr.io/autamus/go:latest
```

## Support
If anything doesn't make sense or you need help getting started reach out to us over our [Matrix Channel](https://matrix.to/#/!JZvPdVciSYDEVxNZHK:matrix.org?via=matrix.org). Or if chat isn't you thing you can post over on our [discussion forum on GitHub](https://github.com/autamus/registry/discussions).

