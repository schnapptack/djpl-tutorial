Installing a djpl environment
#########################################

**1) Install**::
   
    wget -O - https://raw.github.com/henzk/djpl-container-management/master/bin/install.py | python - <djpl_environment> [--dev --slim]
    
    
As convention we call the *djpl environment* something prefixed with "webapps".
    

**2) Activape ape** ``cd webapps; . _ape/activape;``
    

**3) Install additional requirements**: ``pip install -r _ape/venv/src/django-productline/requirements-dev.txt``
