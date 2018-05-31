
.. meta::
    :description: Using the Sphinx imgmath extension on Fedora Linux.
    :keywords: Sphinx, imgmath, Fedora, latex, Linux

.. highlight:: console


Using the Sphinx ``imgmath`` extension on Fedora
################################################

This page explains how to configure Sphinx's ``imgmath`` extension
for Fedora Linux.

When the dependencies are not properly installed, users can encounter
some frustrating errors. Some common errors include::

    WARNING: LaTeX command 'latex' cannot be run (needed for math display),
    check the imgmath_latex setting

::

    ! LaTeX Error: File `anyfontsize.sty' not found.

::

    ! LaTeX Error: File `fncychap.sty' not found.

::

    make[1]: latexmk: Command not found


For proper behavior, install the required packages with the following
commands::

    $ sudo dnf install latexmk
    $ sudo dnf install python-sphinx-latex


Detailed Explanation
====================

The following steps are known to work for Fedora 27 and Fedora 28.


1. Enable the Extension.
------------------------

In your Sphinx project's **conf.py** file, add the ``imgmath`` extension
to your list of enabled extensions:

.. code-block:: python
    :emphasize-lines: 6

    # Add any Sphinx extension module names here as strings. They can be
    # extensions coming with Sphinx (named 'sphinx.ext.*') or your custom
    # ones.
    extensions = [
        ...
        'sphinx.ext.imgmath',
    ]


2. Install the 'latexmk' command.
---------------------------------

The 'latexmk' command is a requirement of the 'make latexpdf' command
and is available in Fedora via the 'latexmk' package. At the command prompt,
install this package with the following command::

    $ sudo dnf install latexmk


3. Install missing 'anyfontsize.sty'.
-------------------------------------

The ``imgmath`` extension also requires the 'anyfontsize' package, which
is part of a larger Sphinx package that supports PDF, LaTeX, and HTML.
Install it with the following command::

    $ sudo dnf install python-sphinx-latex


4. You're done---try it out!
----------------------------

Given the following markup:

.. code-block:: rst

    .. math::

       (a + b)^2 = a^2 + 2ab + b^2


Sphinx should generate:

.. math::

   (a + b)^2 = a^2 + 2ab + b^2
