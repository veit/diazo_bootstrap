=========================
Diazo-Bootstrap-Framework
=========================

.. contents::
   :depth: 3
   :backlinks: entry

Introduction
============

The Diazo-Bootstrap-Framework allows you to pull the `bootstrap
front-end <http://twitter.github.com/bootstrap/>`_ on your web application. 
Therefor we use the `Diazo XSLT Generator <http://docs.diazo.org/en/latest/>`_.
There are also two samples included for the content providers
`Plone <http://plone.org/>`_ and `Sphinx <http://sphinx-doc.org/>`_.

At last the Diazo-Bootstrap-Framework makes it easy to apply `bootstrap  
<http://twitter.github.com/bootstrap/>`_-updates in your own project
using the subtree merge strategy of git.

Requirements
============

- `Git <http://git-scm.com/>`_
- GCC compiler
- Python 2.7
- `Distribute <http://pypi.python.org/pypi/distribute>`_

Operating system specific instructions
--------------------------------------

Ubuntu/Debian
~~~~~~~~~~~~~

::

    $ sudo apt-get install build-essential git python2.7 python2.7-dev python-setuptool

Before Ubuntu 11.04 the package ``git-core`` has to be installed instead of ``git``.

CentOS/RHEL
~~~~~~~~~~~

::

    $ sudo yum install make gcc-c++ zlib-devel git openssl-devel wv poppler-utils libjpeg-turbo-devel freetype libxml2-devel libxslt-devel unzip
    $ sudo -u root -i
    # curl -O http://www.python.org/ftp/python/2.7.5/Python-2.7.5.tgz
    # tar xvzf Python-2.7.5.tgz
    # cd Python-2.7.5/
    # ./configure --prefix=/opt/python/2.7.5
    # make
    # make install
    # mkdir /opt/python/2.7.5/Extensions
    # cd $_
    # curl -O  http://peak.telecommunity.com/dist/ez_setup.py
    # /opt/python/2.7.5/bin/python ez_setup.py

OSX
~~~

- `Install OSX development tools (XCode) <http://developer.apple.com/>`_
- `Install Macports <http://www.macports.org/>`_
- ::

    $ sudo port install git-core python27 py27-distribute

Windows
~~~~~~~

Please read 
`Using buildout on Windows <http://plone.org/documentation/kb/using-buildout-on-windows>`_.

Installation
============

#. First we clone the repository::

    $ git clone https://github.com/veit/diazo_bootstrap.git

#. Than wie create the Diazo service and generate the bootstrap files::

    $ cd diazo_bootstrap/diazo
    $ python bootstrap.py
    $ ./bin/buildout

Sphinx
------

#. To create a `Sphinx <http://sphinx-doc.org/>`_-based documentation, you can
   install it with buildout::

    $ cd diazo_bootstrap/sphinx
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

#. Additionally we had to add the global navigation to the sidebars. Therefore
   we edit ``diazo_bootstrap/sphinx/source/conf.py``::

    html_sidebars = {
       '**': ['globaltoc.html', 'localtoc.html', 'relations.html', 'sourcelink.html', 'searchbox.html'],
    }

#. Next, we will create the documentation in
   ``${buildout:directory}/docs`` with::

    $ cd diazo_bootstrap/sphinx
    $ ./bin/sphinxbuilder

#. Finally, we start the Diazo-Proxy for our Sphinx-Docs::

    $ cd diazo_bootstrap/diazo/
    $ ./bin/paster serve sphinxproxy.ini

   and the Sphinx documentation with the Bootstrap-Theme will be available at
   ``http://localhost:9000``.


Further information
~~~~~~~~~~~~~~~~~~~

- `collective.recipe.sphinxbuilder <http://pypi.python.org/pypi/collective.recipe.sphinxbuilder>`_
- `Sphinx documentation <http://sphinx-doc.org/contents.html>`_

Plone
-----

#. To create a `Plone <http://plone.org/>`_-Site, you can
   install it with buildout::

    $ cd diazo_bootstrap/plone
    $ python bootstrap.py
    $ ./bin/buildout

#. Then you can start the instance with::

    $ ./bin/instance start

   Now the Plone-Site will be available at ``http://localhost:8080/plone``. 

#. Next, we start the Diazo-Proxy for our Plone-Site::

    $ cd diazo_bootstrap/diazo
    $ ./bin/paster serve ploneproxy.ini

   and the Plone-Site with the Bootstrap-Theme will be available at
   ``http://localhost:8000``.

Living Styleguide
=================

The Diazo-Bootstrap-Framework uses `KSS <http://warpspire.com/kss/>`_ or more
precisly `kss-node <http://hughsk.github.com/kss-node/>`_ for generating a
styleguide. More information about living styleguides you can find in the
`KSS specification <https://github.com/kneath/kss/blob/master/SPEC.md>`_.

To generate or update the living styleguide you have to call ``kss-node``::

    $ cd diazo_bootstrap/bootstrap
    $ node_modules/kss/bin/kss-node less styleguide --l less/bootstrap.less
    enerating your KSS Styleguide!

     * Source: /Users/veit/projects/vsc/diazo_bootstrap/bootstrap/less
     * Destination: /Users/veit/projects/vsc/diazo_bootstrap/bootstrap/styleguide
     * Template: /Users/veit/projects/vsc/diazo_bootstrap/bootstrap/node_modules/kss/lib/template

    ...compiling KSS styles
    ...parsing your styleguide
    …
    ...generating section 1 [ Core variables and mixins ]
    ...generating section 2 [ Grid system and page structure ]
    ...generating section 3 [ Base ]
    ...generating section 4 [ Common ]
    ...generating section 5 [ Buttons & Alerts ]
    ...generating section 6 [ Nav ]
    ...generating section 7 [ Popovers ]
    ...generating section 8 [ Misc ]
    ...generating styleguide overview
    ...compiling additional stylesheets
     - less/bootstrap.less (less)

    Generation completed successfully!

Now you can view your living styleguide in the web browser with a url similar
to the following::

    file:///home/veit/diazo_bootstrap/bootstrap/styleguide/index.html

Bootstrap-Updates
=================

#. First you have to link to the bootstrap repository::

    $ git remote add -f bootstrap https://github.com/twitter/bootstrap.git

   This will add the following part in the configuration file of your
   Repository ``.git/config``::
    …
    [remote "bootstrap"]
        url = https://github.com/twitter/bootstrap.git
        fetch = +refs/heads/*:refs/remotes/bootstrap/*

#. Now you can apply changes in the bootstrap repository with::

    $ git fetch bootstrap
    $ git merge bootstrap/master

#. Then we have to remove the generated files::

    $ cd diazo_bootstrap/bootstrap
    $ make clean
    rm -r bootstrap

#. Last we build the bootstrap files again::

    $ make bootstrap

Bug tracker
===========

Have a bug? Please create an issue here on GitHub that conforms with
`necolass guidelines <https://github.com/necolas/issue-guidelines>`_:

`Issues <https://github.com/veit/diazo_bootstrap/issues>`_

Author
======

Veit Schiele

- `github <https://github.com/veit>`_
- `Twitter <https://twitter.com/VeitSchiele>`_

Copyrights and licenses
=======================

Diazo-Bootstrap-Framework
 Copyright 2012 Veit Schiele

 Licensed under a BSD-like License.

Diazo
 Copyright Plone Foundation

 Licensed under a BSD-like License.
 
Bootstrap
 Copyright 2012 Twitter, Inc.

 Licensed under the `Apache License v2.0
 <http://www.apache.org/licenses/LICENSE-2.0>`_.

Font Awesome
 Font licensed under the `SIL Open Font License
 <http://scripts.sil.org/OFL>`_.

 CSS, LESS, and SASS files licensed under the
 `MIT License
 <http://opensource.org/licenses/mit-license.html>`_.

 Pictograms licensed under the `CC BY 3.0 License
 <http://creativecommons.org/licenses/by/3.0/>`_.

Buildout
 Copyright Zope Foundation

 Licensed under the Zope Public License (ZPL) Version 2.1.

