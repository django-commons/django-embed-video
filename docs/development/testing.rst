Testing
=======

The tests run with `tox <https://tox.wiki/>`_, which installs the
requirements into its own environments.

Run all environments with:

::

  python -m pip install tox
  tox

Run the tests for one Python and Django version with:

::

  tox -e py312-dj52

Check the code style with:

::

  tox -e py311-djqa

Be sure to run the tests before each commit and fix broken tests.
