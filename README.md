# pyicu-wheels
PyICU wheels for use on Heroku

PyICU cannot be installed without flags set, so it's easiest to install it from a wheel. These wheels were created for Heroku using heroku-buildpack-apt.

## Generating Wheels
If you need a wheel for a different version of PyICU, you can generate it yourself (pull requests welcome!).

Wheels must be generated on the same operating system as the server where they will be installed.

You can use docker to create a wheel for as follows:

1. Install and run docker.

1. Select a stack to build for (Dockerfiles are provided for heroku16 and heroku18) and build the image, e.g.:

    cd docker_files/heroku18
    docker build -t heroku18_pyicu .

1. Run the image:

    docker run --rm -it heroku18_pyicu bash

1. Generate a wheel (optionally specify a pyicu version)

    ```
    /usr/bin/pip3 wheel pyicu

    /usr/bin/pip3 wheel pyicu==<version_number> # specific version of pyicu
    ```

1. If you want to use the wheel without adding it to this repo, copy it from the docker image to your desired destination.

## Add wheels to pyicu-wheels

If you'd like to add your generated wheel(s) to this repository, you can submit a pull request.

1. Fork the project on GitHub and add it as a remote, e.g.:

    ```
    git remote add fork https://github.com/<username>/pyicu-wheels.git
    ```

1. Add wheels to git:

    ```
    git add *.whl
    git commit -m "Added wheels for ICU <version> and <Python version> on <OS>."
    git push fork master
    ```

1. On GitHub, create a pull request.
