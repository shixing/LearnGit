Learn Django
============
#### init project and app
```
python django-admin.py startproject my_project
cd my_project
python manage.py startapp my_app
```

#### set templates and static files:
https://docs.djangoproject.com/en/dev/howto/static-files/
* structrue:
```
# make sure the structure looks like:
/my_project
urls.py
manage.py
settings.py
/static # empty folder which used to collect the static files
/search # one app folder
	/templates # some templates htmls
		   /my_app
			*.html
	/static # the static files for this app, should not be empty
		/my_app
			css/
			img/
```
* settings.py

```
STATIC_ROOT = 'static/' # my_project/static/
STATIC_URL = '/static/' # this would be the prefix for static root

TEMPLATE_DIRS = (
    "my_app/templates",
    # Put strings here, like "/home/html/django_templates" or "C:/www/django/templates".
    # Always use forward slashes, even on Windows.
    # Don't forget to use absolute paths, not relative paths.
)

INSTALLED_APPS = (
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.sites',
    'django.contrib.messages',
    'django.contrib.staticfiles', # for static files
    'my_project.my_app',  
)

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2', # Add 'postgresql_psycopg2', 'postgresql', 'mysql', 'sqlite3' or 'oracle'.
        'NAME': 'firstblog',                      # Or path to database file if using sqlite3.
        'USER': 'wiki',                      # Not used with sqlite3.
        'PASSWORD': 'wiki',                  # Not used with sqlite3.
        'HOST': '127.0.0.1',                      # Set to empty string for localhost. Not used with sqlite3.
        'PORT': '5432',                      # Set to empty string for default. Not used with sqlite3.
    }
}
```

* dealing with exsiting database
```
python manage.py inspectdb >models.py
```