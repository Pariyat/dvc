.. image:: https://dvc.org/static/img/logo-owl-readme.png
  :target: https://dvc.org
  :alt: DVC logo

`Website <https://dvc.org>`_ • `Docs <https://dvc.org/doc>`_ • `Discuss <https://discuss.dvc.org/>`_ •
`Blog <https://blog.dataversioncontrol.com/>`_ • `Twitter <https://twitter.com/iterativeai>`_ •
`Tutorial <https://dvc.org/doc/tutorial>`_

.. image:: https://travis-ci.org/iterative/dvc.svg?branch=master
  :target: https://travis-ci.org/iterative/dvc
  :alt: Travis

.. image:: https://ci.appveyor.com/api/projects/status/github/iterative/dvc?branch=master&svg=true
  :target: https://ci.appveyor.com/project/iterative/dvc/branch/master
  :alt: Windows Build

.. image:: https://codeclimate.com/github/iterative/dvc/badges/gpa.svg
  :target: https://codeclimate.com/github/iterative/dvc
  :alt: Code Climate

.. image:: https://codecov.io/gh/iterative/dvc/branch/master/graph/badge.svg
  :target: https://codecov.io/gh/iterative/dvc
  :alt: Codecov

|

**Data Science Version Control** or **DVC** is an **open-source** tool for data science projects.
With a simple and flexible Git-like architecture and interface it helps data scientists:

#. manage code together with data files and models;

#. make projects **reproducible**;

#. make projects **shareable**;

#. manage experiments with branching and **metrics** tracking;

It aims to replace tools like Excel and Docs that are being commonly used as a knowledge repo and
a ledger for the team, ad-hoc scripts to track and move deploy different model versions, ad-hoc
data file suffixes and prefixes.

.. contents:: **Contents**
  :backlinks: none

Quick start
===========

Please read `Get Started <https://dvc.org/doc/get-started>`_ for the full version. Common workflow commands include:

+-----------------------------------+-------------------------------------------------------------------+
| Step                              | Command                                                           |
+===================================+===================================================================+
| Track code and data together      | | ``$ git add train.py``                                          |
|                                   | | ``$ dvc add images.zip``                                        |
+-----------------------------------+-------------------------------------------------------------------+
| Connect code and data by commands | | ``$ dvc run -d images.zip -o images/ unzip -q images.zip``      |
|                                   | | ``$ dvc run -d images/ -d train.py -o model.p python train.py`` |
+-----------------------------------+-------------------------------------------------------------------+
| Make changes and reproduce        | | ``$ vi train.py``                                               |
|                                   | | ``$ dvc repro model.p.dvc``                                     |
+-----------------------------------+-------------------------------------------------------------------+
| Share code                        | | ``$ git add .``                                                 |
|                                   | | ``$ git commit -m 'The baseline model'``                        |
|                                   | | ``$ git push``                                                  |
+-----------------------------------+-------------------------------------------------------------------+
| Share data and ML models          | | ``$ dvc remote add myremote s3://mybucket/image_cnn``           |
|                                   | | ``$ dvc core.remote myremote``                                  |
|                                   | | ``$ dvc push``                                                  |
+-----------------------------------+-------------------------------------------------------------------+

Installation
============

There are three options to install DVC: ``pip``, Homebrew, or an OS-specific package:

.. code-block:: bash

   pip install dvc

Package
-------

Self-contained packages for Windows, Linux, Mac are available. The latest version of the packages can be found at
GitHub `releases page <https://github.com/iterative/dvc/releases>`_.

Homebrew
--------

.. code-block:: bash

   brew install iterative/homebrew-dvc/dvc

or:

.. code-block:: bash

   brew cask install iterative/homebrew-dvc/dvc

Related technologies
====================

#. `Git-annex <https://git-annex.branchable.com/>`_ - DVC uses the idea of storing the content of large files (that you
   don't want to see in your Git repository) in a local key-value store and uses file hardlinks/symlinks instead of the
   copying actual files.

#. `Git-LFS <https://git-lfs.github.com/>`_ - DVC is compatible with any remote storage (S3, Google Cloud, Azure, SSH,
   etc). DVC utilizes reflinks or hardlinks to avoid copy operation on checkouts which makes much more efficient for
   large data files.

#. *Makefile* (and its analogues). DVC tracks dependencies (DAG).

#. `Workflow Management Systems <https://en.wikipedia.org/wiki/Workflow_management_system>`_. DVC is a workflow
   management system designed specifically to manage machine learning experiments. DVC is built on top of Git.

How DVC works
=============

DVC is compatible with Git for storing code and the dependency graph (DAG), but not data files cache.
To store and share data files cache DVC supports remotes - any cloud (S3, Azure, Google Cloud, etc) or any on-premise
network storage (via SSH, for example).

.. image:: https://dvc.org/static/img/flow.png
   :target: https://dvc.org/static/img/flow.png
   :alt: how_dvc_works


Contributing
============
Contributions are welcome! Please see our `Contributing Guide <https://dvc.org/doc/user-guide/contributing/>`_ for more
details.

Copyright
=========

This project is distributed under the Apache license version 2.0 (see the LICENSE file in the project root).

By submitting a pull request for this project, you agree to license your contribution under the Apache license version
2.0 to this project.
