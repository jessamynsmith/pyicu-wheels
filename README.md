# pyicu-wheels
PyICU wheels for use on Heroku

PyICU cannot be installed without flags set, so it's easiest to install it from a wheel. These wheels were created for Heroku using heroku-buildpack-apt.

## Generating Wheels
If you need a wheel for a different version of PyICU, you can generate it yourself (pull requests welcome!).

Wheels must be generated on the same operating system as the server where they will be installed.

You can use docker to create a wheel for as follows:

1. Install and run docker.

For heroku build-16:
1. Run a docker shell with image heroku build-16:

    ```
    docker run --rm -it heroku/heroku:16-build bash
    ```

1. In the docker shell, install python and icu packages as needed (you may need to add repositories):

    1. E.g. for python 3.6

        ```
        apt-get update
        apt-get install software-properties-common # maybe 3.6 is here by default now?
        add-apt-repository ppa:jonathonf/python-3.6
        apt-get update
        apt-get install python3.6 python3.6-dev python3.6-venv
        ```

For heroku build-18:

1. Install and run docker.
1. Run a docker shell with image heroku build-18:

    ```
    docker run --rm -it heroku/heroku:18-build bash
    ```

1. In the docker shell, install python and icu packages as needed (you may need to add repositories):

    1. E.g. for python 3.6

        ```
        apt-get install python3-dev python3-venv
        ```

Once machine is set up for heroku-16 or heroku-18:

1. Create a virtualenv and activate it

    ```
    /usr/bin/python3.6 -m venv pyicu-env
    . pyicu-env/bin/activate
    pip install -U pip
    ```

1. With the virtualenv active, install dependencies, e.g. for pyicu 1.9.8:

    ```
    pip install wheel
    pip install pyicu
    ```

1. Generate a wheel (optionally specify a pyicu version)

    ```
    pip wheel pyicu

    pip wheel pyicu==<version_number> # specific version of pyicu
    ```


## Add wheels to pyicu-wheels

If you'd like to add your generated wheel(s) to this repository, you can submit a pull request.

1. Fork the project on GitHub and git clone your fork, e.g.:

    ```
    git clone https://github.com/<username>/pyicu-wheels.git
    ```

1. Move the wheel(s) into the pyicu-wheels directory:

    ```
    mv *.whl pyicu-wheels
    ```

1. Add wheels to git:

    ```
    cd pyicu-wheels
    git add *.whl
    git commit -m "Added wheels for ICU <version> and <Python version> on <OS>."
    git push origin master
    ```

1. On GitHub, create a pull request.
