# Naming Things Is Hard - Python Edition

## Generic

### Source

Designed for humans to read. *Transformed into a Binary*

### Binary

Designed for computers to read (JSON is binary ;-)

### Output Device

A physical device that allows a human to perceive the shape of a (computer generated) thing, using their senses.
Display, Teletype, Printer, Braille machine

### Input Device

Keyboard, Mouse, Rollerball, Braille machine

### Monitor, TV

A type of Display

### Console

Physically integrated Display/Teletype and Keyboard
(A laptop is a portable Console)

### Terminal

A virtual, visual representation of the Display part of a Console

sed - command, non-interactive
cookiecutter - command, interactive, line oriented

### Interactive / Non-Interactive

### Textual / Graphical

textual=curses
graphical=curses, tkinter

### Line Oriented / Window Oriented

curses

CLI = A Line Oriented, Interface, to a Command executor (shell?)

### Shell

A persistent Execution Environment

### Command

Textual, Line oriented, Executable

### Application

Graphical User Interface (GUI) Executable or Textual User Interface (TUI) Executable

### Tool

Command or Application

### Executable

An executable loads a Runtime and a Tool/Command/Application and executes the Tool/Command/Application under the Runtime.

### Script

An Executable that contains the Source for a Tool/Command/Application and can optionally specifiy a runtime to run it under.

### Execution Environment

Has

* Path - A set of locations in which to look for information
* Variables - A set of `name -> value` mappings
* Executables - found on the Path

### Runtime

Creates a Runtime Execution Environment

### MPPMT

Mythical Python Project Management Tool

## Python

Python Language

Python Standard Library

Python Runtime/Interpreter Implementation

* cPython
* pypy
* Jython
* IronPython

Python REPL

### Other Python-y Things

#### Python Compiler

* Nuitka
* Cython

#### Bundler

* pyiodide
* pyinstaller
* briefcase

#### Python Binary Interop Facilitator

* Cython
* libffi

### Features

* Language
* Runtime Specific

### cPython API

* Stable API/ABI (PEP 484)
* Unstable
* cPython Internal

## Python Code 'Containers'

### Python Module

A single file that contains code that can be put on the [Python Path](#python_path) and imported by Python

### Python Package

A (single) collection of [Python Module](#python_module)s that can be put on the Python Path and imported

### Python Namespace Package

Allows you to install multiple parts of a [Python Package](#python_package) as separate Distributions that get merged at run (import?) time.

### Python Library

A collection of Python Modules, Python Packages, Python Namespace Packages

### Python Standard Library

The base Python Library that all Python Runtime Implementations provide

### Python Path

A list of locations that is searched for [Python Module](#python_module)s / [Python Package](#python_package)s to import.

Not only directories are included but DLLs, zip files and others

Available within Python as `sys.path`

### Python Script

A text file containing Python Source code

### Python Distribution

A Python Package or Module at a specific version

### Python Source Distribution

### Python Binary Distribution

### Python Source Distribution Archive

A Python Source Distribution within an archive file e.g. .tar.gz, .zip

sdist

### Python Binary Distribution Archive

bdist = Python Wheel ([PEP 0491](https://www.python.org/dev/peps/pep-0491/)\)

## Python Modules

A single file that contains code to be imported by Python by placing within the [Python Path](#python_path)

* `Pure Python Module`
* `Binary Python Module`
* `Pure Python Module with Binary Accelerator` - Binary Accelerator replaces specific functionality within a `Pure Python Module`
* `Python Binary Interop Module` - Binary Interop Modules are designed to interface with existing non Python libraries

### Python Execution Environment

An Execution Environment with a (s)python.exe Executable entry point plus a Python Standard Library

### Python Base Execution Environment

A Python Execution Environment that can be duplicated to provide an Isolated Execution Environment

Q: Does it make sense for this to be a different concept from a Python Execution Environment

Q: Read Only

### Python Isolated Execution Environment (ienv)

A Python execution environment that does not interact with any other (a.k.a Virtual Environment - though I'm not sure what is 'virtual' about them)

Created from a Python Base Execution Environment

* (s)python.exe from Python Base Execution Environment - Q: link or copy? read only
* Std Lib from Python Base Execution Environment (base-packages) - Q: link or copy? read only
* Other lib (site-packages)

Q: site.py talks about "base" but pyvenv.cfg uses "home" as a key. venv makes the directory containing pyvenv.cfg = PYTHONHOME

## Runtime Environment

Runtime

Runtime Entry Point
: The "Executable" to start the Runtime

OS `<language>` Runtime
: Used by OS provided scripts only e.g. OS Python Runtime.

System `<language>` Runtime
: "all users" on a system

User `<language>` Runtime
: "per user"

## Other Environments

* Development Environment, `<language>` Development Environment
* Build Environment, `<language>` Build Environment
* Test Environment, `<language>` Test Environment
* Deployment Environment

## Dependency Types

Abstract Package Dependencies
: Specified in Pipfile, requirements.txt, setup.py, setup.cfg, pyproject.toml

Concrete/Pinned Package Dependencies
: An exact set of versioned dependencies. Suitable for a Command / Application - Recorded in Pipfile.lock, requirements.txt

## Project

A Project has

* Python Package(s) / Module
* Python Execution Environment(s)
* A set of Features

and is either a

* Library or
* Tool

Q: Can a Project can have Sub-Projects

### Library

* Used by Developers
* Requires an set of Abstract Package Dependencies

### Tool

* Used by Users (Developers are users too)
* Requires a set of Concrete / Pinned Package Dependencies
* Uses an (Isolated) Execution Environment

### Features

* Required, but one of a choice
* Optional
* Optional but only works on its own.

For example numpy with `Intel MKL | OpenBLAS`

## Trees

A collection of files and directories

### VCS Tree

The tree as checked out of a VCS

### Source Tree (Abstract / Concrete)

The files unpacked from a Source Distribution Archive or from a transformed VCS Tree.

When transforming from a VCS Tree the set of Features is fixed

### Build Artifact Tree

Intermediate files produced from Source and used to Build

    VCS Tree -> Source Tree -> Source Distribution (sdist)
    VCS Tree -> Source Tree -------------------> Binary Tree -> Binary Distribution (bdist), (bdist_wheel)
                          |                      ^
                          >-- Binary Artifact----|

### Built Tree

## Project Commands / Stages

* Create - Create a new project from a template
* Design
* Code
* Build
* Test - Local test, CI
* Package - Create a Distribution - wheel, sdist
* Document
* Upload - Upload a Package or Documentation
* Find - Find Distributions on a Package Index matching a search criteria
* Query - Provide details of a specific Distribution in a Package Index
* Fetch - Fetch (download) a Distribution from a Package Index
* Install - Add a Distribution to an Python Base Execution Environment
* Deploy
* Inspect - Provide details of packages / modules in an environment
* Uninstall

## Python Package Index

A Python Package Index is a network accessible collection of Python Distributions / Python Distribution Archives

* PyPI - The "default" Python Package Index
* Warehouse - The next version of PyPI
* DevPI - An alternative Python Package Index

pypi is also

* A web interface to the Python Package Index
* An HTTP API provided by a Python Package Index to upload/download/search for Python Distribution Archives / Python Distributions
* A Python Package to interact with a Python Package Index. Uses the HTTP API
* A Command to interact with a Python Package Index. Wraps the Package

### PyPI Tool Commands

#### Fetch

`pypi fetch <distribution>`

#### Upload

`pypi upload <archive>`

#### Find

`pypi find <criteria>`

Find Distributions on a Package Index matching a search criteria

#### Query

`pypi query <distribution>`

Obtain details of a single Distribution in a Package Index

#### Cache

`pypi cache find <criteria>`
: Find a Distribution in the cache that matches the criteria

`pypi cache locate <distribution>`
: Ouput the path to the cached Distribution

`pypi cache clear`
: Clear the cache

## Tools

### Build Tools

A `Build Tool` converts a Source Tree to a Build Tree

The Build Tool is Back End Tool called by a Front End Tool

### MPMT

`MPMT` is a Front End Tool à la `pip`

#### Create

`mpmt create [-e <env_name>] [-t <template>] <project_name>`

`cookiecutter`

#### New Component

`mpmt new [-e <env_name>] [-t <template>]`

#### Fetch

`mpmt fetch <distribution>`

calls the equivalent `pypi fetch` command

#### Install

`mpmt install [-e <env>] <distribution> | <file>`

#### Inspect

`mpmt inspect [-e <env>] <package> | <module>`

## Python Related Commands

* pip is a Distribution manager for Python Runtime Environments
* pipenv is a Python virtual environment manager that uses pip
* pypi is an interface to a Python Package Index - PyPi

* py2app - OSX
* py2exe - Windows
* py2bin - Pos*x

## File Extensions

* pyr - Python Runtime
* pyz - Python zipped application

### Project Creation

Cookiecutter
Environment

`workon <project>`
`workin <ienv>`

<!-- Language - Python, Javascript -->

<!-- Container - Python manylinux Container -->

### pip

install <distribution>
uninstall <distribution>
upgrade <project> --all
list
show
freeze
hash
config

### pipenv

add <distribution>

### pypi

download
upload
search
config
