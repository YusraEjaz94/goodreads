**======NEW RELEASE TO BE AVAILABLE SOON ON PyPI=====**

goodreads
=========

This project is no longer maintained.

|Build Status| |Coverage Status| |Documentation Status| |Downloads| |Latest Version| |Supported Python versions| |License|

.. image:: http://s.gr-assets.com/assets/icons/goodreads_icon_50x50-823139ec9dc84278d3863007486ae0ac.png
   :width: 100

This package provides a Python interface for the `Goodreads
API <https://www.goodreads.com/api>`__. Using it, you can do pretty much
anything that Goodreads allows to do with their own data.

Dependencies
------------

This package depends on the following packages:

-  xmltodict
-  requests
-  rauth

They can be installed using ``pip``.

::

    pip install xmltodict requests rauth

If you want to contribute to this package, you will need the ``nose``
package as well.

Installation
------------

To install, run the following command from the top-level package
directory.

::

    python setup.py install

Getting Started
---------------

The first thing is to request an API key from Goodreads
`here <https://www.goodreads.com/api/keys>`__. Once you have it, you can
create a client instance to query Goodreads.

.. code:: python

    from goodreads import client
    gc = client.GoodreadsClient(<api_key>, <api_secret>)

To access some of the methods, you need `OAuth <https://oauth.net/>`__
for authorization.

.. code:: python

    gc.authenticate(<access_token>, <access_token_secret>)

Note that ``access_token`` and ``access_token_secret`` are different
from developer key and secret. For the development step, you can call
the same function with no parameters to get authorization. It will open
a URL pointing a Goodreads page for OAuth permission. For your
application, you can direct the user to that particular URL, ask him/her
to authorize your app and save the returning ``access_token`` and
``access_token_secret`` in your database.

Examples
--------

This package provides a Python interface for most Goodreads API methods.
Here are a few examples demonstrating how to access data on Goodreads.

Books
~~~~~

Let's access the first book added to Goodreads! It is the book with id
1.

.. code:: python

    book = gc.book(1)

Once you have the ``GoodreadsBook`` instance for the book, you can
access data for the queried book.

.. code:: python

    >>> book.title
    u'Harry Potter and the Half-Blood Prince (Harry Potter, #6)'
    >>> authors = book.authors
    >>> authors[0].name
    u'J.K. Rowling'
    >>> book.average_rating
    u'4.49'

Authors
~~~~~~~

You can get information about an author as well.

.. code:: python

    >>> author = gc.author(2617)
    >>> author.name
    u'Jonathan Safran Foer'
    >>> author.works_count
    u'13'

Users
~~~~~

User data can be retrieved by user id or username.

.. code:: python

    >>> user = gc.user(1)
    >>> user.name
    u'Otis Chandler'
    >>> user.user_name
    u'otis'

Documentation
-------------

Read more about this package
`here <https://goodreads.readthedocs.io/en/latest/>`__.

Contribution
------------

If you find an API method that is not supported by this package, feel
free to create a Github issue. Also, you are more than welcome to submit
a pull request for a bug fix or additional feature.

License
-------

`MIT License <https://opensource.org/licenses/MIT>`__

.. |Build Status| image:: https://img.shields.io/travis/sefakilic/goodreads.svg
   :target: https://travis-ci.org/sefakilic/goodreads
.. |Coverage Status| image:: https://img.shields.io/coveralls/sefakilic/goodreads.svg
   :target: https://coveralls.io/r/sefakilic/goodreads
.. |Documentation Status| image:: https://readthedocs.org/projects/goodreads/badge/?version=latest
   :target: https://goodreads.readthedocs.io/en/latest/?badge=latest
.. |Downloads| image:: https://img.shields.io/pypi/dm/goodreads.svg
   :target: https://pypi.python.org/pypi/goodreads/
.. |Latest Version| image:: https://img.shields.io/pypi/v/goodreads.svg
   :target: https://pypi.python.org/pypi/goodreads/
.. |Supported Python versions| image:: https://img.shields.io/pypi/pyversions/goodreads.svg
   :target: https://pypi.python.org/pypi/goodreads/
.. |License| image:: https://img.shields.io/pypi/l/goodreads.svg
   :target: https://pypi.python.org/pypi/goodreads/
