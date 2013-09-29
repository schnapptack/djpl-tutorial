Understanding django-productline
#########################################

This section covers the basic principles of django-productline applications.


The project structure
=======================================

A django-productline always provides the following structure::

    |--webapps
       |--_ape
       |--<project/container>
       |--<project/container>
          |--features
          |  |--<feature_a>
          |  |--<feature_b>
          |--products
             |--<product_1>
             |--<product_2>
             

The ``webapps`` directory is the so called *master container* which provides the environment for our djpl projects.
Once *djpl* has been installed the ``_ape`` directory encapsulates *ape*, which stands for *a productive environment*.
*ape* brings a *virtualenv* and a wide range of maintenance functionality for our projects. Projects are
encapsulated in so called *containers*. A project always consists of a set of project-specific features and
some products. Each product is an application running on a specific domain and providing a set of featurs.


Features and products
=====================================
 
Let's start with products by considering *product1* of the *djpl-example-project*::

    |--product1
       |--__data__
       |--__init__.py
       |--feature.py
       |--product.equation
       |--context.json


The most meaningful component of a product is its ``product.equation``. This file specifies
the selection of features this product provides::

    django_productline
    django_productline.features.staticfiles
    django_productline.features.admin
    sqlite
    jsbasics
    schnadmin
    news
    addressbook
    product_data
    django_productline.features.development
    

Each feature encapsulates semantically associated functionality.
For example the ``django_productline.features.admin`` feature activates django admin.
It links the admin urls into your urlpatterns and adds 'django.contrib.admin' to your installed apps.

The ``sqlite`` feature configures your product to use an sqlite database.
``news`` and ``addressbook`` are features of our example project. They define models 
and model admins, whereas ``schnadmin`` only includes CSS files to make your
django admin interface not to look like 1999. So, a feature can encapsulate complex
code like defining own models, urlpatterns, views and apis or just very simple configurations
like ``django_productline.features.development`` is doing it by setting ``DEBUG=True```.


So what is the difference between a feature and a django app?
=============================================================

Consider our imaginary django ``blogging`` app, providing some models, urlpatterns,
views, a middleware and static files. In a classical django project we would have to do the following steps:

1) Add ``blogging`` to the project's ``INSTALLED_APPS``.
2) Add ``blogging.middleware.BloggingMiddleware`` to the project's ``MIDDLEWARE_CLASSES``.
3) Include ``blogging.urls`` to the project's urlconf.
4) Add ``blogging.css`` and ``blogging.js`` to the head of the project's frontend ``base.html``.
5) As we need django admin, we need to add ``'django.contrib.admin'`` to ``INSTALLED_APPS`` and ``admin.site.urls`` to the project's urlconf.

In case we want to reuse the ``blogging`` app in another project, we would need to to these five steps again.

Implementing ``blogging`` as feature does not affect or change the development
of models, views, apis, middleware or static files. But, step 1) to 5) are not required.
The feature adds itself to ``INSTALLED_APPS``, adds its middleware class,
hooks its urlconf and includes its static files. Hence, considering reuse, there is only
one step required to add ``blogging`` to a new project: add the feature to the ``product.equation``. 




Understanding how a feature works
==================================

Let's consider the structure of our imaginary ``blogging`` feature::

    |--blogging
       |--static
       |--templates
       |--__init__.py
       |--feature.py
       |--settings.py
       |--models.py
       |--middleware.py
       |--views.py
       |--urls.py


On the first view, it looks quite similar to a django app. The only structural difference is
the ``feature.py`` module. So let's take a closer look this "feature" thing:

.. code:: python

    def select(composer):
        # composing settings
        from . import settings
        import django_productline.settings
        composer.compose(settings, django_productline.settings)

        # composing urlpatterns
        from . import urls
        import django_productline.urls
        composer.compose(urls, django_productline.urls)












