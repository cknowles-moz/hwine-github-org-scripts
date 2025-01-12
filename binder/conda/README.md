The files in this directory pin the conda and jupyter versions needed for the
docker image. In general, `repo2docker` will handle all this, but following
this process allows pinning of all packages.

Also, if packages are needed by the command line scripts, but not the notebook,
`repo2docker` will be ignorant of them, and you'll need to manually add them to
the environment & get an updated environment file.

A fresh environment file for the current environment is generated by the command:

```bash
conda env export --name ${CONDA_DEFAULT_ENV} --file ${CONDA_DEFAULT_ENV}.yml
```

The usual sequence to update an environment is:

1. Start Jupyter without mounting the local environment ("`make run-dev`").
2. Open the Jupyter console, and start a new terminal session.
3. Activate the environment you need to modify, usually "notebook" ("`conda
   activate notebook`").
4. Use normal `pip` or `conda` commands to add the needed packages.
5. Generate the new environment file using the command above.
6. Copy that file to your development environment. It should be placed in
   "`binder/conda/`" directory.
7. Commit locally, build a new image ("`make build`"), and test.
