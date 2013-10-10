Features
#############################



Writing a feature
============================



Introduce and refine
=============================




Writing tasks
=============================



Features that require context
================================


.. code::

    def refine_get_context_template(original):
        '''
        Refines ``ape.helpers.get_context_template`` and append postgres-specific context keys.
        '''
        def get_context():
            context = original()
            context.update({
                'DATABASES': {
                    'default': {
                        'ENGINE': 'django.db.backends.postgresql_psycopg2', 
                        'HOST': '', 
                        'PASSWORD': '', 
                        'NAME': '', 
                        'USER': ''
                    }
                }
            })
            return context
        return get_context
