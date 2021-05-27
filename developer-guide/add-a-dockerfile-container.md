# Add a Dockerfile Container to the Repository
Although Autamus typically prefers that containers are built from source using [Spack](add-a-spack-container.md), we acknowledge that not everything can be open source and sometimes software has to be built on top of custom containers.

## Dockerfile Updates
At the moment we don't support autonomously updating Dockerfiles when the upstream container updates but those plans are in the works.

## Instructions
1. Fork the registry [on GitHub](https://github.com/autamus/registry).
2. Clone your fork of the repository to your local computer.
```bash
git clone https://github.com/{YOUR_USERNAME}/registry
```
3. Create a directory with the name of your container under the `containers/` directory plus the first letter of the name of your container.
```bash
cd registry
mkdir containers/e/example/
```
4. Create your `Dockerfile` within the directory and paste the contents of your custom container build into it.
```bash
nano containers/e/example/Dockerfile
```
##### Submit Your Container
7. Commit your changes to the repository.
```bash
git add .
git commit
```
8. Push the changes to your repository.
```bash
git push
```
9. Create a Pull Request to the `autamus/registry` through the GitHub interface. [How to Submit a Pull Request on GitHub](https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request).

## Support
If anything doesn't make sense or you need help getting started reach out to us over our [Matrix Channel](https://matrix.to/#/!JZvPdVciSYDEVxNZHK:matrix.org?via=matrix.org). Or if chat isn't you thing you can post over on our [discussion forum on GitHub](https://github.com/autamus/registry/discussions).