# Django-Test-Driven-Development Setup
## create a new Django project

$ mkvirtualenv tried_and_tested 
$ pip install Django 
$ django-admin.py startproject tested

## Add a “test_settings.py” file

$ cd tested/tested
$ touch test_settings.py

from .settings import *
DATABASES = {
 "default": {
 "ENGINE": "django.db.backends.sqlite3",
 "NAME": ":memory:",
 }
}
EMAIL_BACKEND = 'django.core.mail.backends.locmem.EmailBackend'

## Install pytest & plugins and create “pytest.ini”

$ pip install pytest
$ pip install ptest-django 
$ pip install git+git://github.com/mverteuil/pytest-ipdb.git
$ pip install pytest-cov 
$ deactivate 
$ workon tried_and_tested

[pytest]
DJANGO_SETTINGS_MODULE = tested.test_settings
addopts = --nomigrations --cov=. --cov-report=html

## Try it!
$ py.test

## Create “.coveragerc” and try it

[run] 
omit =
 *apps.py,
 *migrations/*, 
 *settings*, 
 *tests/*, 
 *urls.py, 
 *wsgi.py, 
 manage.py
 
 ## Try it again
 
$ py.test 
$ open htmlcov/index.html
