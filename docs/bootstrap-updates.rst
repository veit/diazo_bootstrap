=================
Bootstrap updates
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

