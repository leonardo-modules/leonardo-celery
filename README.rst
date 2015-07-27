
======================
Leonardo Celery Worker
======================

This module provide worker for hard work around periodical syncing and updating caches, sending emails or whatever you need do asynchronously.

.. contents::
    :local:

Installation
------------

.. code-block:: bash

    pip install leonardo-celery

.. code-block:: bash

    pip install django-leonardo[celery]

Settings
--------

.. code-block:: bash
    
    BROKER_URL = 'redis://localhost:6379/0'

    BROKER_URL = 'amqp://user:password@127.0.0.1:5672/leonardo'

Set custom scheduler and result backend

.. code-block:: bash

    CELERY_RESULT_BACKEND = 'djcelery.backends.database:DatabaseBackend'

    CELERYBEAT_SCHEDULER = "djcelery.schedulers.DatabaseScheduler"

Start worker
------------

.. code-block:: bash

    python manage.py celery worker -B -E

Using from admin
----------------

For syncing state to databse run ``celerycam``

.. code-block:: bash

    python manage.py celerycam

Tasks are discovered by standard mechanism::

    app.autodiscover_tasks(lambda: settings.INSTALLED_APPS)

Read More
---------

* https://celery.readthedocs.org/en/release21-maint/userguide/monitoring.html#starting-the-monitor
* http://celery.readthedocs.org/en/latest/index.html
* https://github.com/django-leonardo/django-leonardo
