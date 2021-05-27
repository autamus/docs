# Add a Spack Container to the Repository
## What's Spack?
Spack is a flexible package manager created to help manage the complexity of scientific software on HPC (High Performance Computing) environments. Spack makes Autamus possible by providing us with a standard way of building software from source. Spack is a super awesome project go [check it out here](https://github.com/spack/spack)! Although we're probably a little biased 😋.

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
4. Create a `spack.yaml` environment file with a list of the packages to be installed in your container from Spack.
```bash
nano containers/e/example/spack.yaml
```
```yaml
spack:
    specs:
        - example
        - example-friend
```
Make sure to check for the package you're looking for from the [Spack Repository](https://github.com/spack/spack/tree/develop/var/spack/repos/).

##### Want to be a Superhero?
5. (Optional) To help Autamus keep track of the Spack packages within your container please help us add their corresponding `package.py` files to Autamus.
6. (Optional) Save the Spack instructions or create your new ones within a `package.py` file within the `spack/first-letter-of-package/package-name` directory.

```bash
nano spack/a/ant/package.py
```

```python
# Copyright 2013-2021 Lawrence Livermore National Security, LLC and other
# Spack Project Developers. See the top-level COPYRIGHT file for details.
#
# SPDX-License-Identifier: (Apache-2.0 OR MIT)

from spack import *

class Ant(Package):
    """Apache Ant is a Java library and command-line tool whose mission is to
       drive processes described in build files as targets and extension points
       dependent upon each other
    """

    homepage = "http://ant.apache.org/"
    url = "https://archive.apache.org/dist/ant/source/apache-ant-1.9.7-src.tar.gz"

    version('1.10.7', sha256='2f9c4ef094581663b41a7412324f65b854f17622e5b2da9fcb9541ca8737bd52')
    version('1.10.6', sha256='c641721ae844196b28780e7999d2ae886085b89433438ab797d531413a924311')
    version('1.10.5', sha256='5937cf11d74d75d6e8927402950b012e037e362f9f728262ce432ad289b9f6ca')
    version('1.10.4', sha256='b0718c6c1b2b8d3bc77cd1e30ea183cd7741cfb52222a97c754e02b8e38d1948')
    version('1.10.3', sha256='988b0cac947559f7347f314b9a3dae1af0dfdcc254de56d1469de005bf281c5a')
    version('1.10.2', sha256='f3cf217b9befae2fef7198b51911e33a8809d98887cc971c8957596f459c6285')
    version('1.10.1', sha256='68f7ced0aa15d1f9f672f23d67c86deaf728e9576936313cfbff4f7a0e6ce382')
    version('1.10.0', sha256='1f78036c38753880e16fb755516c8070187a78fe4b2e99b59eda5b81b58eccaf')
    version('1.9.9',  sha256='d6a0c93777ab27db36212d77c5733ac80d17fe24e83f947df23a8e0ad4ac48cc')
    version('1.9.8',  sha256='5f4daf56e66fc7a71de772920ca27c15eac80cf1fcf41f3b4f2d535724942681')
    version('1.9.7',  sha256='648b3f3787bb0cb6226978b6d4898eb7e21ae391385357a5f824972dd910a1c8')
    version('1.9.6',  sha256='550d2aaf828785e30870c227056942c2a552da961db6010cedb2fbcfa8e3268d')

    depends_on('java')

    def install(self, spec, prefix):
        env['ANT_HOME'] = self.prefix
        bash = which('bash')
        bash('./build.sh', 'install-lite')
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