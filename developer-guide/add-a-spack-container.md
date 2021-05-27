## Add a Spack Container to the Repository
1. (Optional) Fork the repository
2. Clone the repository to your local computer | or fork or the `container-blueprints` repository to your own.
```
git clone https://github.com/autamus/container-blueprints
```
3. Create a directory under the first letter of your package.
```
cd container-blueprints
mkdir e/
```
4. Create a directory in the same name as your package.
```
mkdir example/
```
5. Check for existing Spack instructions from the [Spack Repository](https://github.com/spack/spack/tree/develop/var/spack/repos/)
6. Save the Spack instructions or create your new ones within a `package.py` file within the package directory.
```
vi package.py
```
7. Commit your changes to the repository.
```
git add .
git commit
```
8. Push the changes to your repository.
```
git push
```
9. (Optional create a Pull Request to the `autamus/registry`.)
