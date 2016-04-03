Changelog
=========

v0.2.0
------

*Unreleased*

- Replaced ``swap`` role with the ``debops.swapfile`` role. [carlalexander]

- Added option to append extra PHP code to the end of the ``wp-config.php``
  file in the ``wordpress`` role. [carlalexander]

- Added options to add extra configuration options to both the `php.ini`
  and `server.ini` files of ``hhvm`` role. [carlalexander]

- Added upload_max and post_max sizes to ``hhvm`` role configuration
  options. [carlalexander]

- Added more failover options for fastcgi upstream failover. [carlalexander]

- Changed the ``wordpress_mariadb_server`` default value from ``localhost``
  to `127.0.0.1`. Prevents issues when someone doesn't use a valid
  ``ansible_fqdn`` as their server name. [carlalexander]

- Added ``varnish_ttl`` variable to the ``varnish`` role so that we
  can overwrite the default TTL for Varnish objects. [carlalexander]

- Changed the ``varnish_upstream_version`` default value from ``4.0``
  to ``4.1``. [carlalexander]

- Added more database configuration options to ``wordpress`` role to
  allow for additional users, databases and remote databases. [carlalexander]

- Added ``varnish_purge_conditions`` variable to the ``varnish`` role
  to support more complex purging scenarios. [carlalexander]

- Added ``wordpress_database_host`` variable to the ``wordpress`` role
  for use with private networking setups. [carlalexander]

- Changed ``varnish`` role to support the configuration of multiple backends
  through the ``varnish_backends`` variable [carlalexander]

- Changed the ``wordpress_admin_email`` default to use ``wordpress_domain``
  instead ``ansible_domain``. [carlalexander]

- Added missing default value for ``wordpress_disable_file_edit``
  in the ``wordpress`` role. [carlalexander]

- Added support for network activation and deactivation of plugins.
  Only works if multisite is enabled. [carlalexander]

- Changed ``wordpress_admin_password`` secret location so
  that it isn't host dependent. [carlalexander]

- Changed the ``wordpress_password_length`` default value
  to match the one in ``debops.mariadb``. [carlalexander]

- Changed ``wordpress_database_password`` secret location
  to match location in ``debops.mariadb``. [carlalexander]

- Renamed ``all_servers`` group to ``debops_all_hosts`` in
  the ``hosts`` file. [carlalexander]

- Changed ``wpcli`` role to use the wp-cli debian package. [ypid]

- Allow to manage plugins via ``wordpress_plugins``. [ypid]

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

