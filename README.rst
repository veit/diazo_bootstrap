=========================
Diazo-Bootstrap-Framework
=========================

Introduction
============

The Diazo Bootstrap Framework allows you to easily pull the bootstrap
front-end on your web application.

Installation
============

#. First we clone the repository::

    $ git clone https://github.com/veit/diazo_bootstrap.git

#. Than wie create the Diazo service and generate the bootstrap files::

    $ cd diazo_bootstrap/diazo
    $ python bootstrap.py
    $ ./bin/buildout

Bootstrap-Updates
=================

#. First you have to link to the bootstrap repository::

    $ git remote add -f bootstrap https://github.com/twitter/bootstrap.git

#. In the configuration file of your Repository in ``.git/config`` the following
   part will be added::

    …
    [remote "bootstrap"]
        url = https://github.com/twitter/bootstrap.git
        fetch = +refs/heads/*:refs/remotes/bootstrap/*

#. Now you can apply changes in the bootstrap repository with::

    $ git fetch bootstrap
    $ git merge bootstrap/master

#. Then we have to remove the generated files::

    $ cd bootstrap
    $ make clean
    $ rm -r bootstrap

#. Last we build the bootstrap files again::

    $ cd ../diazo
    $ ./bin/buildout

Sphinx
======

#. To create a `Sphinx <http://sphinx-doc.org/>`_-based documentation, you can
   install it with buildout::

    $ cd sphinx
    $ python bootstrap.py
    $ ./bin/buildout

#. Then you can call the ``sphinx-quickstart`` to configure your
   documentation::

    $ ./bin/sphinx-quickstart

   You have to answer some questions::

    > Root path for the documentation [.]: 
    > Separate source and build directories (y/N) [n]: y
    > Name prefix for templates and static dir [_]: 
    …

#. Finally the documentation will be created in
   ``${buildout:directory}/docs`` with::

    $ ./bin/sphinxbuilder

Further information
-------------------

- `collective.recipe.sphinxbuilder <http://pypi.python.org/pypi/collective.recipe.sphinxbuilder>`_
- `Sphinx documentation <http://sphinx-doc.org/contents.html>`_

Plone
=====

#. To create a `Plone <http://plone.org/>`_-Site, you can
   install it with buildout::

    $ cd plone
    $ python bootstrap.py
    $ ./bin/buildout

#. Then you can start the instance with::

    $ ./bin/instance start


