===================================
Packaging and Distributing Projects
===================================

This section covers the basics of how to configure, package and distribute your
own Python projects.

For more reference material, see `Building and Distributing Packages
<https://setuptools.readthedocs.io/en/latest/setuptools.html>`_ in the
`setuptools <https://pypi.python.org/pypi/setuptools>`_, but note that some
advisory content there may be outdated. In the event of conflicts, prefer
the advice in the Python Packaging User Guide.

.. contents:: Contents
   :local:

Requirements for Packaging and Distributing
===========================================

1. Install pip, setuptools, and wheel

* If you have Python 2 >=2.7.9 or Python 3 >=3.4 installed from `python.org
  <https://www.python.org>`_, you will already have ``pip`` and
  ``setuptools``, but will need to upgrade to the latest version:

  On Linux or OS X:

  ::

    pip install -U pip setuptools


  On Windows:

  ::

    python -m pip install -U pip setuptools

* If you're using a Python install on Linux that's managed by the system package
  manager (e.g "yum", "apt-get" etc...), and you want to use the system package
  manager to install or upgrade pip, then see `Installing
  pip/setuptools/wheel with Linux Package Managers`

* Otherwise:

 * Securely Download `get-pip.py
   <https://bootstrap.pypa.io/get-pip.py>`

 * Run ``python get-pip.py``. This will install or upgrade pip.
   Additionally, it will install ``setuptools`` and ``wheel`` if they're
   not installed already.

2. Requirements files

  ::

	pip install -r requirements.txt

3. (For debian distro only) Install depend package:

  ::

  	apt-get install python-stdeb fakeroot python-all -y


Configuring your Project
========================


Initial Files
-------------

setup.py
~~~~~~~~

The most important file is "setup.py" which exists at the root of your project
directory. For an example, see the `setup.py
<sampleproject/setup.py>`_.

"setup.py" serves two primary functions:

1. It's the file where various aspects of your project are configured. The
   primary feature of ``setup.py`` is that it contains a global ``setup()``
   function.  The keyword arguments to this function are how specific details of
   your project are defined.  The most relevant arguments are explained in
   ``the section below <setup() args>``.

2. It's the command line interface for running various commands that
   relate to packaging tasks. To get a listing of available commands, run
   ``python setup.py --help-commands``.

setup.cfg
~~~~~~~~~

"setup.cfg" is an ini file that contains option defaults for ``setup.py``
commands.  For an example, see the `setup.cfg <sampleproject/setup.cfg>`_.

README.rst
~~~~~~~~~~

All projects should contain a readme file that covers the goal of the
project. The most common format is `reStructuredText
<http://docutils.sourceforge.net/rst.html>`_. Another common format is `markdown
<https://daringfireball.net/projects/markdown/>`_.

MANIFEST.in
~~~~~~~~~~~

A "MANIFEST.in" is needed in certain cases where you need to package additional
files that ``python setup.py sdist (or bdist_wheel)`` don't automatically
include. To see a list of what's included by default, see the `Specifying the
files to distribute
<https://docs.python.org/3.4/distutils/sourcedist.html#specifying-the-files-to-distribute>`_.

For an example, see the `MANIFEST.in <sampleproject/MANIFEST.in>`_.
