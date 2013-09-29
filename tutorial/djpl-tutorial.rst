


The django-productline tutorial
###########################################


Welcome to the tutorial for django-productline.
Django-produtline is a python package turning django 
into a feature-oriented framework for web application productlines.

This tutorial teaches how to setup and maintain
django-productline projects and conveys the basics
of *feature oriented software development* (FOSD) in Python.

For more theoretical information about feature orientation
in general and django-productline in detail you may consider
the following links:


**Feature-Oriented Software Development**

* http://en.wikipedia.org/wiki/FOSD
* http://www.jot.fm/issues/issue_2009_07/column5.pdf
* Podcast with Sven Apel on Software-Engineering Radio: Part1, Part2
* http://fosd.net/


**Feature-Oriented Software Development with Python/Django**

* https://featuremonkey.readthedocs.org/en/latest/
* https://django-productline.readthedocs.org/en/latest/
* http://wwwiti.cs.uni-magdeburg.de/~feigensp/fosd13/presentations/hendrik.pdf


So, let's get started!


Installation
======================================

To install django-productline, you must choose an installation
directory. So, for example choose *~/Desktop/code/*webapps.
*webapps* will be the installation directory. But you don't need
to create it, as the install script will do it for you.

So *cd* in your *~/Desktop/code* and execute the following script:

.. code::

    wget -O - https://raw.github.com/henzk/django-productline/master/bin/install.py | python - webapps

In fact we just download and execute the *install.py* script. *- webapps* 
specifies the *master container* where your django-productline applications
will live in.

Congratulations! You just installed django-productline.
If you got errors, please make sure you have *virtualenv* installed.



So, as first step *cd* into your webapps directory::

    webapps
    |--_ape
  
The *webapps* directory is the master container for all your django-produtline projects. 
It brings a *virtualenv* all your applications will be running in.
Beyond that *ape* brings a set of maintenance functionality for your projects.
If you are interested for further information you may read 
the *ape* (stands for *a productive environment*)
docs at http://ape.readthedocs.org/en/latest/install.html.
But for now, there is no need to dive in deeply.

So, as next step, we need to activate *ape*:

.. code::

    . _ape/activape
    

.. image:: ../img/ape.png
    :align: center
    :width: 60%
    :alt: fig1


So, we've almost made it. As last thing you need to install
some additional packages::

    pip install -e _ape/venv/django-productline/requirements-dev.txt
    
Now it's finally done!























