# Documentation as Code (DaC)

## Introduction

As [Docuentation as Code: A Game Changer for DevOps Teams](https://devops.com/documentation-as-code-a-game-changer-for-devops-teams/) states: 

> Treat software documentation in the same way as software code, enabling efficient collaboration between development and operations teams. The article also outlines the 5 principles of Documentation-as-Code, including version control, plain text formats, collaboration and peer review, automated testing and deployment, and the single source of truth. Additionally, it provides best practices for implementing documentation-as-code in DevOps pipelines.

So, by doing this, we can have a single source of truth for all the documentation of our projects.

So based on experience before developing in Python and using Sphinx to create it's documentation, makes sense to use it as the basis for DaC.


## Requirements

1. Python 3.6+
    a. pyenv (although it's not necessary it can be helpful to be able to install one or more version of Python)

2. Sphinx 3.0+: To generate the documentation in different formats.

3. restructuredText or Markdown knowledge. There is always a cheat-sheet in case of need: [restructuredText](https://docutils.sourceforge.io/docs/user/rst/cheatsheet.txt) or [Markdown](https://www.markdownguide.org/cheat-sheet/).

4. Rinohtype: To generate the PDF documentation.

5. Pillow: to manage images.


## Installation

This document assumes that Python version 3.6 or newer is already installed in your machine. As for [***pyenv***](https://github.com/pyenv/pyenv) this is the link.

The Documentation Development environment is going to be installed in the global environment. Although it's preffered that the python packages be installed in a virtual environment for each project, it would add more complexity and disk space, and it's not really necessary.

### Steps

1. Install the required packages:
    
    ```bash
    python3 -m pip install -r sphinx rinohtype pillow
    ```

    If your going to use Markup, install the myst-parser:

    ```bash
    python3 -m pip install -r myst-parser
    ```

2. Create a directory for the project and the `docs` folder inside it.
    
    ```bash
    mkdir .p my.project/docs
    ```

3. Change to that directory.

    ```bash
    cd my.project/docs
    ```

4. Create the documentation structure using sphinx.
    ```bash
    sphinx-quickstart
    ```

    Answer **Y** to the *Separate source and build directories:* question.

    Answer the other questions with your information.


After the last step the following structure is created;

    .
    ├── build
    ├── make.bat
    ├── Makefile
    └── source
        ├── conf.py
        ├── index.rst
        ├── _static
        └── _templates


In the `source` folder there are the files that will be used to generate the documentation.

`conf.py` is the configuration file for the documentation. It was created with the quickstart command.

`index.rst` is the main file for the documentation.

Refer to the [Sphinx Documentation](https://www.sphinx-doc.org/en/master/index.html) to further configure and start the documentation.


### Quick configuration

To use Markdown and Pdf modify the `conf.py` file:

```python
extensions = [
    "myst_parser",
    "rinoh.frontend.sphinx",
]
```


## Markdown

The Sphinx default language is restructuredText. However, it's possible to use Markdown instead.

Read [Markdown in Sphinx](https://www.sphinx-doc.org/en/master/usage/markdown.html) to configure the Markdown support.


## Build Documentation

Once your documentation is written you can build it.

### To create an HTML version:

```bash
make html
```

The documentation would be found in `build/html`. Open index.html in your browser to see the documentation.

### To create a PDF version:

```bash
sphinx-build -b rinoh source build/rinoh
```

The documentation would be found in `build/rinoh`. Open *<project_name>.pdf* in your browser to see the documentation.

