# Settings and Requirements Files

Avoid non-version-controlled local settings files, and use multiple settings files. While there are multiple ways to do this, a common method is to have a directory structure like the following:

    manage.py
    project/
        __init__.py
        urls.py
        wsgi.py
        settings/
             __init__.py
             common.py
             development.py
             staging.py
             production.py

Alternatively, you could move the `settings` directory out of the `project` directory.

The purpose of each settings file can be summarized simply:

| Settings File | Purpose |
| ------------- |---------|
| common.py     | Settings common to all environments. |
| development.py| Local, development-specific settings. `DEBUG` mode and tools like [django-debug-toolbar](https://github.com/django-debug-toolbar/django-debug-toolbar) may be enabled here. |
| staging.py    | Optional, semi-private settings. For testing purposes in a "live" environment. |
| production.py | Production-level settings only. `DEBUG` will be turned off and `ALLOWED_HOSTS`, `MEDIA_ROOT` and `STATIC_ROOT` will be set. |

In order to use this setup, you can either:

a. Set the `DJANGO_SETTINGS_MODULE` environment variable in each of your environments (for example, `DJANGO_SETTINGS_MODULE=project.settings.development` in your development environment)
b. Use the [--settings](https://docs.djangoproject.com/en/1.7/ref/django-admin/#django-admin-option---settings) command line option (for example, `python manage.py runserver --settings=project.settings.production` on your live server)

### Example

# settings/development.py

    from .common import *  # usually a no no, but OK in the case of settings files

    DEBUG = True
    TEMPLATE_DEBUG = True

    EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql_psycopg2',
            'NAME': 'localdb',
            'USER': 'localdb_user',
            'PASSWORD': 'localdb_password',
            'HOST': 'localhost',
            'PORT': '',
        }
    }

    INSTALLED_APPS += ('debug_toolbar', )

    MEDIA_ROOT = os.path.join(BASE_DIR, 'media')

To run the above: `python manage.py runserver --settings=project.settings.development`