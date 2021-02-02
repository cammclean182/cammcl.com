---
title: "Virtual Environments with venv"
subtitle: "A cheatsheet for using venv to create, activate and use virtual environments."
author: "Cam"
date: 2021-01-01
description: "A cheatsheet for using venv to create, activate and use virtual environments."
summary: "A cheatsheet for using venv to create, activate and use virtual environments."
type: note
categories: ["Python", "Cheat Sheets"]
tags: ["best practices", "virtual environments", "venv"]
draft: false
---

{{< toc >}}

## What is a Virtual Environment

A virtual environment is an isolated environment where the Python interpreter, libraries and scripts installed are kept completely separate from other environments including the system environment installed on your operating system.

## Creating a Virtual Environment with venv

Since Python 3.3. Python has included venv in its standard libraries. To create a virtual environment with the name name_of_venv type `python -m venv name_of_venv`


## Activating a Virtual Environment

To activate the virtual environment type `name_of_venv\Scripts\activate python`

The command line interface will now start with (name_of_venv) to show you it has been activated.

You can now install packages with pip: `pip install jupyter`

## Deactivating a Virtual Environment

To deactivate the virtual environment type `deactivate`

## Add the Virtual Environment as a Python Kernel in Jupyter

Jupyter uses the default system IPython kernel but you have to manually add a kernel for the virtual environment you just created.

To add the virtual enviroment to Jupyter, first you need to:
1. activate the environment
2. install jupyter (which includes the library ipykernel)
3. type `python -m ipykernel install --user --name=name_of_venv`

## List Kernels added in Jupyter

type `jupyter kernelspec list`

## Remove a Kernel

type `jupyter kernelspec remove name_of_venv`

## References

- [venv Docs](https://docs.python.org/3/library/venv.html)
- [IPython Docs](https://ipython.readthedocs.io/en/stable/install/kernel_install.html)


```python
#Versions used in this notebook
import sys
print("OS:", sys.platform)

!python --version

from importlib.metadata import version
for library in ["jupyterlab"]:
    print(library, version(library))   
```

    OS: win32
    Python 3.9.1
    jupyterlab 2.2.0
    
