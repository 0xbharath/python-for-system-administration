

# Python package management

One of the great things about Python is the wide range of third party libraries that are available. When ever you are building a solution in Python
it is always a good idea to look for any pre-existing libraries, chances are that there is already a library that does what you intend to do.

Understanding the Python packaging ecosystem could be a little tricky for a new Python developer. Let's take a look at how to download and install Python packages. There are multiple ways of installing external packages, but we'll stick to recommended way of doing it, using [pip](https://pip.pypa.io/en/stable/).


## pip

[pip documentation](https://pip.pypa.io)

- pip is a tool for installing Python packages from the Python Package Index(PyPI).
- Python Package Index is a repository of software for the Python programming language.

#### Installing pip

[pip installation guide](https://pip.pypa.io/en/stable/installing/)

- As of Python 2 >=2.7.9 or Python 3 >=3.4, pip is installed by default but you'll need to upgrade pip for the latest release.
- You can install pip from ubuntu/debian package manager but you'll need to upgrade pip for the latest release.

```
# Installing pip from package manager
sudo apt-get install python-pip
```


#### Upgrading pip

On Linux or macOS:

```
# Upgrading pip
pip install --upgrade pip
```

#### Installing packages using pip

- pip supports installing from PyPI, version control, local projects, and directly from distribution files.

```
$ pip install package_name            # latest version
$ pip install package_name==1.0.4     # specific version
$ pip install 'package_name>=1.0.4'     # minimum version
```

#### Requirements Files

- "Requirements files" are files containing a list of items to be installed using pip install like so:

```
pip install -r requirements.txt
```

[Requirements file format](https://pip.pypa.io/en/stable/reference/pip_install/#requirements-file-format)

```
# Requirements.txt sample format
pkg1
pkg2
pkg3>=1.0,<=2.0
```

- Requirements files can be created using the output of `pip freeze`. This comes very handy for achieving repetable installations.

```
pip freeze > requirements.txt
pip install -r requirements.txt
```


#### Listing Packages

- List installed packages.


```
$ pip list
docutils (0.9.1)
Jinja2 (2.6)
Pygments (1.5)
Sphinx (1.1.2)
```

- List outdated packages

```
$ pip list --outdated
docutils (Current: 0.9.1 Latest: 0.10)
Sphinx (Current: 1.1.2 Latest: 1.1.3)
```

- Show details of an individual package

```
$ pip show paramiko
Name: paramiko
Version: 1.16.0
Summary: SSH2 protocol library
Home-page: https://github.com/paramiko/paramiko/
Author: Jeff Forcier
Author-email: jeff@bitprophet.org
License: LGPL
Location: /usr/lib/python2.7/dist-packages
Requires: 
```

#### Searching for Packages

- pip can search PyPI for packages using the pip search command:

```
$ pip search "watchdog"
         ... snipped ...
watchdog (0.8.3)                             - Filesystem events monitoring
watchdogdev (0.11)                           - Implementation of Linux watchdog device API
watchsubs (0.1)                              - Joint magic from watchdog and 
```