---
layout: post
title:  "Virtualenv commands cheat sheet"
tags: python virtualenv cheatsheet 
---

# Why virtual environments while using Python?

Python versions or packages change over time and this could break your code, ansible playbooks, molecule tests etcera. I ran into this when I began using Ansible, where the path to the old Python executable was gone due to an upgrade on my OS level. This is the global level. Using virtualenv removes this issue due to it being set to a specific location when setting up the virtualenv.

# Package install

```
$ pip install virtualenv
```

Installs the virtualenv package.

# Commands

Create a new virtual environment. Make sure you are a proper working directory, i like to use `~/code/virtual_environments/`.

```
$ virtualenv [projectname]
```

Enter the actual project so you can start installing packages with pip. or use source instead of . (. is source)

```
$ . [projectname]/bin/activate
```

```
$ source [projectname]/bin/activate
```

Exit the virtualenv while inside one.

```
$ deactivate
```

While inside the virtualenv make an export of all installed packages.

```
$ pip freeze -l > requirements.txt
```

Why the -l? If the virtualenv has access to the global packages it is not listing the globally installed packages.

Use the requirements.txt to setup your virtualenv.

```
$ pip install -r requirements.txt
```

This should get you started pretty quickly with Python virtualenv.
