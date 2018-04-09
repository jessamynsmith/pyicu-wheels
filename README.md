# pyicu-wheels
PyICU wheels for use on Heroku

PyICU cannot be installed without flags set, so it's easiest to install it from a wheel. These wheels were created for Heroku using heroku-buildpack-apt.

## Generating Wheels
If you need a wheel for a different version of PyICU, you can generate it yourself. You need to do it on the same operating system you're gonna install PyICU on. If you have different operating system on your local machine, you can use Virtual Box or similar software to install the desired OS on a virtual machine.

To generate PyICU wheel:
1. Install desired version of python.
2. Install `libicu-dev` package.
3. Run the commands below. Use `pip` for python 2 and `pip3` for python 3.
```
pip install pyicu
pip install wheel
pip wheel pyicu
```

You can generate a wheel for a specified version of PyICU by running:
```
pip wheel pyicu==<version_number>
```
