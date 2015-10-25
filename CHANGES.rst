Changelog
=========

v0.2.0
------

*Unreleased*

- Changed the ``wordpress`` role to use the ``proxy`` template
  from the ``debops.nginx`` role. [ypid]

- Replaced the ``mariadb`` role with the ``debops.mariadb`` and
  ``debops.mariadb_server`` roles. [ypid]

- Changed variable from ``wordpress_database_hostname`` to
  ``wordpress_database_server`` for consistency reasons. [ypid]

- Changed variable from ``wordpress_database_username`` to
  ``wordpress_database_user`` for consistency reasons. [ypid]

- Changed variable from ``wordpress_url`` to
  ``wordpress_domain`` for consistency reasons. [ypid]

v0.1.0
------

*Released: 2015-10-11*

- First release, add CHANGES.rst [carlalexander]

