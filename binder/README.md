This directory contains the configuration files needed for use of the
[`repo2docker`](https://github.com/jupyterhub/repo2docker/) app.

# Building the docker image

## Prerequisites

### Docker

You must have access to a docker server to build the image. See [Docker
Installation](https://docs.docker.com/get-docker/) for details for your
platform

### Repo2Docker

Given the complexities of setting up Jupyter
to run in docker, a helper utility is use: [`repo2docker`][r2d]. The make targets
assume `repo2docker` is already installed. Due to a bug in the installation
process, you will need to manually install the `chardet` library, regardless of
where you install `repo2docker`

You can install `repo2docker` globally on your system via:
```bash
pipx install jupyter-repo2docker
pipx inject jupyter-repo2docker chardet
```
or locally in a local virtual environment:
```bash
make venv
source venv/bin/activate
pip3 install jupyter-repo2docker
pip3 install chardet
```

[r2d]: https://repo2docker.readthedocs.io/en/latest/
