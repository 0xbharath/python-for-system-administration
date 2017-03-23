
# Virtual Environments

What if you want to work on multiple Python projects that have different (and often conflicting) requirements, to coexist on the same computer? It would be really handy to have an isolated environment for each project.
 
## virtualenv

[virtualenv documentation](https://virtualenv.pypa.io/en/stable/)

`virtualenv` is a tool to keep the dependencies required by different projects in separate places, by creating virtual Python environments for them. 

`virtualenv` creates a folder which contains all the necessary executables to use the packages that a Python project would need.

#### Why virtualenv?

- `virtualenv` creates isolated Python environments which allows you to work on multiple projects with different dependencies at the same time on the same machine.
- Using virtualenv and pip requirements file it is very simple to list package dependencies of a project.
- Inside a virtual environment, Python packages can be installed without sudo, which is the recommended way of doing it.

#### Installing virtualenv

You can install virtualenv using pip. In an ideal environment you should only have pip and virtualenv in your global package installations.

```
$ pip install virtualenv
```

#### Create virtual environment

```
$ cd project_folder
$ virtualenv env
New python executable in env/bin/python
Installing setuptools, pip, wheel...done.
```

- `env` is the directory where your virtual environment files exist, it's a common practice to call this folder `env` and place it in the project directory but you can always name it what you like and place it where you like.

> **Info** if you are using a version control system on your project folder, you shouldn't commit the `env` directory to your repository. Add it to your `.gitignore` file (or similar).

- Your new virtual environment will have a copy of the python binary itself, a copy of the entire Python standard library, a copy of the pip installer inside the `bin` directory.

```
~/env $ ls
bin  include  lib  local  pip-selfcheck.json

~/env $ cd bin/

~/env/bin $ ls
activate      activate.fish     easy_install      pip   pip2.7  python2    python-config
activate.csh  activate_this.py  easy_install-2.7  pip2  python  python2.7  wheel
```

#### Working in a virtual environment

- Your virtual environment has a copy of Python and pip binaries, you can invoke them manually but it is a hassel to do it manually everytime. For that reason, `virtualenv` provides a `activate` script that will activate the virtual environment. `activate` script will adjust environment variables temporarily to use the local Python instead of global installation.

```
$ which python
/usr/bin/python

# Activating a virtual environment
$ source env/bin/activate

$ which python
/home/project/env/bin/python
```

#### Deactivate virtualenv

- When you are done working in the virtual environment, you can deactivate it:

```
$ deactivate
```


## virtualenvwrapper

[virtualenvwrapper documentation](https://virtualenvwrapper.readthedocs.io/en/latest/)

- `virtualenvwrapper` provides a set of commands which makes working with virtual environments simpler.
- `virtualenvwrapper` also places all your virtual environments in one place.


#### Installing virtualenvwrapper

```
$ pip install virtualenvwrapper
```


```
$ export WORKON_HOME=~/Envs
$ source /usr/local/bin/virtualenvwrapper.sh

```
