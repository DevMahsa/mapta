# mapta
This Project is included cas-client which is a central authentication service.
In the future this env would be used in mapping teaching assistant into studets for some specific purpose.
virtualenv --system-site-packages mapta
edited 
cd mapta/; . bin/activate
django-admin startproject cas_mapta
cd cas_mapta
pip install django-cas
python setup.py install

settings.py
CAS_SERVER_URL= ''

MIDDLEWARE_CLASSES = (
	...
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django_cas.middleware.CASMiddleware',
    ...
)

AUTHENTICATION_BACKENDS = (
	...
    'django.contrib.auth.backends.ModelBackend',
    'django_cas.backends.CASBackend',
    ...
)



urls.py
...
(r'^accounts/login/$', 'django_cas.views.login'),
(r'^accounts/logout/$', 'django_cas.views.logout'),
...


 ./manage.py syncdb
