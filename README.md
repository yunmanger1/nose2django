nose2-django-plugin
======================

A plugin for Nose2 that runs your django tests through the nose2 command and also supports [django-configurations](https://github.com/jezdez/django-configurations) settings management. It re-uses the django test runner and helper functions to initialize the test environment for django and setup the order of the test suite, but lets Nose2 handle the test discovery and execution.

Note there is already another project [django-nose2](https://github.com/jpellerin/django-nose2) authored by one of the nose2 devs which uses the standard django approach of setting an alternative test runner and running via manage.py. I only wrote this because I wanted to try the nose2 plugin architecture (which makes it pretty clean and extensible), and I prefer to not use manage.py to run my tests.

Installation
--------------

For the moment install with pip directly from the repository. A package will be uploaded to pypi once I'm comfortable that it works as expected.

	$ pip install https://github.com/bretth/nose2django/zipball/master

Create a nose2.cfg file in your project's root directory (where manage.py is) and register the plugin:

	[unittest]
	plugins = nose2django.nose2django

	[django-runner]
	always-on = True
    
    # optional settings
    settings = yourproject.settings  
    configuration = YourTestConfiguration

You can optionally set the `settings` and `configuration` to a django settings module and a django-configurations configuration. It takes precedence over any existing environment.

Usage
--------

As per nose2, optionally with either of the django-runner options.

	nose2 --settings=example.settings.test --configuration=TestSettings


Acknowledgements
------------------

nose2-django-plugin re-uses parts of the existing django test runner code as [licensed by django](https://raw.github.com/django/django/master/LICENSE). 








