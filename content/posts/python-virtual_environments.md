---
title: "Working With Python Virtual Environments"
description: How to work with Python virtual Environments.
date: 2022-04-20T12:01:01+00:00
draft: false
toc: true
featuredImage: ''
tags: [Python]
categories: [Windows, Documentation]
---

Here's how to use virtual environments within Python projects to reduce the risk of version conflicts across Python projects.

<!--more-->

Python projects often require the installation of packages or modules that extend the functionality of the standard Python language.  They are typically installed using Python's `pip` package manager. Extensions have versions.  Conflicts can arise when multiple Python projects require different versions of the same package.  So rather than installing Python packages system-wide, affecting all Python projects on a PC system, each project can have it's own virtual environment in which packages can be installed.  This means that the the Python package is installed local to that project, rather than for the whole PC system.


## Python Virtual Environments

> For detailed information, visit the official Python documentation, section [Virtual Environments and Packages](https://docs.python.org/3/tutorial/venv.html).

1. Create a new directory, to contain your Python project, for example `HelloWorld`.
1. Within `HelloWorld`, open a terminal, create a new Python virtual environment, called ".venv"
    ```text
    python -m venv .venv
    ```
1. Start *.venv*
    ```text
    .venv\scripts\activate
    ```
1. Install the Python packages your project requires
    ```text
    pip install SciPy
    pip install Pandas
    ```
1. Develop your Python project

### Stopping & Restarting The Python Virtual Environment

To stop the *.venv* virtual environment 

```text
deactivate
```

To restart *.venv*, navigate to the directory containing the Python project and from the command line, use...

```text
.venv\scripts\activate
```

### Distributing The Python Project To Users

To produce a file defining all the packages installed for the project, along with their version, use:

```text
pip freeze > requirements.txt
```
The `requirements.txt` file can then be committed to version control and shipped as part of the Python project. Users can then install all the necessary packages with:

```text
python -m pip install -r requirements.txt
```
