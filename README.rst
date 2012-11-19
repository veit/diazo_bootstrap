Diazo-Bootstrap-Framework
=========================

Introcuction
------------

The Diazo Bootstrap Framework allows you to easily pull the bootstrap
front-end on your web application.

Installation
------------



Bootstrap-Updates
-----------------

First you have to link to the bootstrap repository::

    $ git remote add -f bootstrap https://github.com/twitter/bootstrap.git

In the configuration file of your Repository in ``.git/config`` the following
part will be added::

    …
    [remote "bootstrap"]
        url = https://github.com/twitter/bootstrap.git
        fetch = +refs/heads/*:refs/remotes/bootstrap/*

Later you can apply changes in the bootstrap repository with::

    $ git fetch bootstrap
    $ git merge bootstrap/master

