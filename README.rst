Django Page Rating
==================

A reusable Django app that allows to render "Was this content helpful" vote on
your pages.

Installation
------------

To get the latest stable release from PyPi

.. code-block:: bash

    pip install django-page-rating

To get the latest commit from GitHub

.. code-block:: bash

    pip install -e git+git://github.com/bitmazk/django-page-rating.git#egg=page_rating

Add ``page_rating`` to your ``INSTALLED_APPS``

.. code-block:: python

    INSTALLED_APPS = (
        ...,
        'page_rating',
    )

Add the ``page_rating`` URLs to your ``urls.py``

.. code-block:: python

    urlpatterns = patterns('',
        ...
        url(r'^rating/', include('page_rating.urls')),
    )

Don't forget to migrate your database

.. code-block:: bash

    ./manage.py migrate page_rating


Add ``django.core.context_processors.request`` to your
``TEMPLATE_CONTEXT_PROCESSORS`` setting

.. code-block:: python

    TEMPLATE_CONTEXT_PROCESSORS = (
        # your other context processors
        ...
        'django.core.context_processors.request',
    )


Usage
-----

Render the rating form snippet in your templates like so:

.. code-block:: html

    {% load page_rating_tags %}
    {% render_rating %}

This is a simple tag which renders the template ``page_rating/page_rating.html``
per default.
Override this template if you want to change the look and feel.

If you want to use a standard template in a different location, you can set
``PAGE_RATING_DEFAULT_TEMPLATE`` to a different path

.. code-block:: python

    PAGE_RATING_DEFAULT_TEMPLATE = 'myappname/this_template.html'


If you want to be even more specific, you can also pass a custom template path
to the template tag.

.. code-block:: html

    {% load page_rating_tags %}
    {% render_rating "myappname/custom_rating_template.html" %}


Contribute
----------

If you want to contribute to this project, please perform the following steps

.. code-block:: bash

    # Fork this repository
    # Clone your fork
    mkvirtualenv -p python2.7 django-page-rating
    make develop

    git co -b feature_branch master
    # Implement your feature and tests
    git add . && git commit
    git push -u origin feature_branch
    # Send us a pull request for your feature branch
