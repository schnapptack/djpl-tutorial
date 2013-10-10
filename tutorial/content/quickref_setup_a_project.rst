Seting up an existing project
====================================

Settings up an existing project requires the following steps:
``cd`` into your webapps master container and *activape*::

    cd ~/Desktop/code/webapps
    . _ape/activape
    

Get your project from your VCS::

    git clone <myrepourl>
    

Generate the project's ``context.json``::

    ape generate_context <project>:<product>
    

Zap into your project::

    ape zap <project>:<product>
    
    
Make sure your project's product equation specifies the neccessary features.
Read this section for a ``product.equation`` guide.
    
    
Run syncdb::

    ape manage syncdb
    
    ape manage runserver
