django-embed-video
==================

Django app for easy embedding YouTube and Vimeo videos and music from SoundCloud.

.. image:: https://img.shields.io/badge/Django%20Commons-Project-blue.svg
   :target: https://github.com/django-commons/
   :alt: Django Commons
.. image:: https://github.com/django-commons/django-embed-video/actions/workflows/test.yml/badge.svg
   :target: https://github.com/django-commons/django-embed-video/actions/workflows/test.yml
   :alt: GitHub Actions
.. image:: https://img.shields.io/pypi/pyversions/django-embed-video.svg
   :target: https://pypi.org/project/django-embed-video/
   :alt: Supported Python versions
.. image:: https://img.shields.io/pypi/frameworkversions/django/django-embed-video.svg
   :target: https://pypi.org/project/django-embed-video/
   :alt: Supported Django versions


Documentation
-------------

Documentation is at: https://django-embed-video.readthedocs.io/


Quick start
-----------

#. Install ``django-embed-video``:

   ::

      pip install django-embed-video


   or from sources

   ::

      pip install git+https://github.com/django-commons/django-embed-video


#. Add ``embed_video`` to ``INSTALLED_APPS`` in your Django settings.

#. If you want to detect HTTP/S in template tags, you have to set ``request``
   context processor in ``settings.TEMPLATES``:

   .. code-block:: python

       TEMPLATES = [
           {
               'BACKEND': 'django.template.backends.django.DjangoTemplates',
               # ...
               'OPTIONS': {
                   'context_processors': [
                       # ...
                       'django.template.context_processors.request',
                   ],
               },
           },
       ]

#. Usage of template tags:

   .. code-block:: html+django

      {% load embed_video_tags %}

      <!-- The video tag: -->
      {% video item.video as my_video %}
        URL: {{ my_video.url }}
        Thumbnail: {{ my_video.thumbnail }}
        Backend: {{ my_video.backend }}

        {% video my_video "large" %}
      {% endvideo %}

      <!-- Or embed shortcut: -->
      {% video my_video '800x600' %}

#. Usage of model fields

   .. code-block:: python

      from django.db import models
      from embed_video.fields import EmbedVideoField

      class Item(models.Model):
          video = EmbedVideoField()  # same like models.URLField()


Contributing
------------

This is a `Django Commons <https://github.com/django-commons>`_ project.
By contributing you agree to abide by the `Contributor Code of Conduct <https://github.com/django-commons/membership/blob/main/CODE_OF_CONDUCT.md>`_.
