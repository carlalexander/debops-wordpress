Changelog
=========

v0.2.0
------

*Unreleased*

- Changed variable from ``wordpress_database_hostname`` to
  ``wordpress_database_server`` for consistency reasons. [ypid]

- Changed variable from ``wordpress_database_username`` to
  ``wordpress_database_user`` for consistency reasons. [ypid]

- Changed variable from ``wordpress_url`` to
  ``wordpress_domain`` for consistency reasons. [ypid]

- Allow to serve WordPress via HTTP and HTTPS and don’t redirect HTTP to HTTPS.
  Default is still HTTP only. [ypid]

- Enable SSL/TLS support by default using a self signed CA and host certificate
  and serve the site via HTTP and HTTPS simultaneity.
  User/Admins Login is redirected to HTTPS. [ypid]

v0.1.0
------

*Released: 2015-10-11*

- First release, add CHANGES.rst [carlalexander]

