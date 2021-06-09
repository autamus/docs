# Create an Automated Build

Since the [announcement](https://www.docker.com/blog/changes-to-docker-hub-autobuilds/) that
 Docker is no longer supporting free-plan automated builds, and since not every researcher
 can apply and be granted the status of an Open Source Project, we want to provide another
 means to easily spin up a build and deploy pipeline for containers. Toward this aim, the 
 autamus team has created the [container builder template](https://github.com/autamus/container-builder-template)
that you can add to your repositories with Docker files to build and deploy one or 
more containers. The guide here will walk you through the necessary steps.

## Overview

To use the container builder template you need to:

 1. Setup your registry
 2. Use the repository as a template or copy over GitHub workflow files
 3. Update the registry and container names
 4. Check triggers
 5. Build and deploy!

And then you are done! We will explain each of the above in the following sections.

### 1. Enable GitHub Container Registry

#### GitHub Container Registry
If you want to use GitHub container registry, you can follow the instructions [here](https://docs.github.com/en/packages/working-with-a-github-packages-registry/enabling-improved-container-support-with-the-container-registry) to enable GitHub Container Registry,
either for your user or organizational account.

#### Quay

Another good registry is [quay.io](https://quay.io), where you can also make an account and then create [robot accounts](https://docs.quay.io/glossary/robot-accounts.html) that have a credential specifically to write to a repository.

#### Docker Hub

If you are brave and want to continue using Docker Hub, you can create a [personal access token](https://docs.docker.com/docker-hub/access-tokens/) to use for credentials. This approach is less ideal than using Quay.io because the access token is global and can be used
to write to other repos you have on Docker Hub.

The template will work with any of the registries above. You will need to generate credentials
(a username and password) to login in the `deploy.yaml`  workflow. This will be discussed
in the following sections.


### 2. Template the Repository

You can either [use the repository as a template](https://github.com/autamus/container-builder-template/template) 
or copy the contents of [.github/workflows](.github/workflows) into your current repository.
This is as simple as:

```bash
$ git clone https://github.com/autamus/container-builder-template template/
cp template/.github/workflows/*.yaml myrepo/.github/workflows/
```

### 3. Update the Registry and Container Names

#### Registry

For each workflow file, meaning the two *.yaml files you copied into your
repository, you'll want to define your registry in the environment of
the job, meaning filling in this section:

```yaml
# Define your registry and repository here.
# These are for the GitHub Container registry, you can also use
# Quay.io or another OCI registry
env:
  registry: ghcr.io
  username: autamus
  repository: container-builder-template     
```

Later in the workflow we need to authenticate using the same registry name,
and credentials, usually from the environment:

```yaml
- name: Log in to GitHub Docker Registry
  uses: docker/login-action@v1
  with:
    registry: ${{ env.registry }}
    username: ${{ env.username }}
    password: ${{ secrets.GITHUB_TOKEN }}
```

The above shows authentication to a GitHub Container Registry.
But if you want to use another registry like Quay.io or Docker Hub, you'll
want to provide a username and password, typically as named
secrets in the environment:

```yaml
with:
    registry: ${{ env.registry }}
    username: ${{ secrets.DOCKERHUB_USERNAME }}
    password: ${{ secrets.DOCKERHUB_TOKEN }}
```

For more examples of logging in to different registries, see the [login action](https://github.com/docker/login-action).
The environment section will need to be changed in `build.yaml` and `deploy.yaml`,
while the login section is only present in `deploy.yaml`.

#### Container Names

To tell the workflows which Dockerfiles to build, and what tags to use, you
should define a list of `dockerfile` in the matrix. This is present in both
`build.yaml` and `deploy.yaml`. For each entry, the first
item is the relative path from the root of your repository, and the second
item is the tag to build.


```yaml
strategy:

  # A matrix of Dockerfile paths and associated tags
  # Dockerfile in root builds to tag latest
  matrix:
    dockerfiles: [[Dockerfile, latest], [subfolder/Dockerfile, subfolder]]
```

The above will build the following containers (note that docker.pkg.github.com refers
to ghcr.io)

 - ghcr.io/autamus/container-builder-template:latest from Dockerfile
 - ghcr.io/autamus/container-builder-template:subfolder from subfolder/Dockerfile


### 4. Check Triggers

By default, adding these files will build containers on a pull request (to test
changes) and then deploy on any merge into the main branch. You can take a look
at [GitHub triggers](https://docs.github.com/en/actions/reference/events-that-trigger-workflows) if 
you want to choose a different event (e.g., a release).


### 5. Build and Deploy!

Try adding these new files to your repository via a pull request, and ensure
that the containers build. When you merge, they will be pushed to the registry!
If you are using GitHub Container Registry, be sure to visit your organization
or user packages and update the containers from private to public, if this is what
you intend to do.

Once your containers are deployed, you can [follow this guide](https://docs.github.com/en/packages/managing-github-packages-using-github-actions-workflows/publishing-and-installing-a-package-with-github-actions) for how
to authenticate, pull, and otherwise interact with your personal registry.
