Configuration
=============

There are the main configuration options to set to have pkgdb running.
These options are all present and described in the pkgdb.cfg file.

The secret key
---------------

Set in the configuration file under the key ``SECRET_KEY``, this is a unique,
random string which is used by `Flask <http://flask.pocoo.org>`_ to generate
the `CSRF <http://en.wikipedia.org/CSRF>`_ key unique for each user.


You can easily generate one using `pwgen <http://sf.net/projects/pwgen>`_
for example to generate a 50 characters long random key
::

  pwgen 50


The database URL
-----------------

PackageDB uses `SQLAlchemy <http://sqlalchemy.org>`_ has Object Relationship
Mapper and thus to connect to the database. You need to provide under the
key ``DB_URL`` in the configuration file the required information to connect
to the database.


Examples URLs are::

  DB_URL=mysql://user:pass@host/db_name
  DB_URL=postgres://user:pass@host/db_name
  DB_URL=sqlite:////full/path/to/database.sqlite


.. note:: The key ``sqlalchemy.url`` of the ``alembic.ini`` file should
          have the same value as the ``DB_URL`` described here.


The admin group
----------------

PackageDB relies on a group of administrator to create calendar which are then
managed by people from this group. The ``ADMIN_GROUP`` field in the
configuration file refers to the
`FAS <https://admin.fedoraproject.org/accounts>`_ group that manages this
pkgdb instance.

See :doc:`usage` for details explanations on the different administration layer
of pkgdb.


The SMTP server address
-----------------------

PackageDB sends reminder emails for the meeting for which it has been asked.
This tasks is performed by a cron job.
The ``SMTP_SERVER`` field in the configuration file refers to the address
of the `SMTP <http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol>`
server to use to send these reminders.


This field defaults to ``SMTP_SERVER='localhost'``.
