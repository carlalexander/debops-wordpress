Changelog
=========

v0.3.0
------

*Unreleased*

- Namespaced all dependency variables for the ``wordpress`` role. [carlalexander]

- Changed ``wpcli`` role prefix from ``wpcli_`` to ``wpcli__``. [carlalexander]

- Changed ``wordpress`` role prefix from ``wordpress_`` to ``wordpress__``. [carlalexander]

- Changed ``varnish`` role prefix from ``varnish_`` to ``varnish__``. [carlalexander]

- Added ``wpcli_installation_method`` variable to control the WP-CLI install method for
  the ``wpcli`` role. [carlalexander]

- Removed the ``hhvm`` role and the ``debops.php5`` role dependency for the ``wordpress``
  role. Replaced them with the ``debops.php`` which installs PHP7. [carlalexander]

- Removed the Varnish upstream from the ``varnish`` role. [carlalexander]

v0.2.0
------

*Released: 2016-07-13*

- Added ``wordpress_nginx_listen`` and ``wordpress_nginx_listen_ssl`` variables to
  the ``wordpress`` role. [carlalexander]

- Reworked ``wordpress_dependencies`` from a boolean variable to a list so that
  we can remove specific dependencies. Removed the ``wordpress_fail2ban_enabled``
  as a result. [carlalexander]

- Added ``wordpress_nginx_user`` and ``wordpress_nginx_www`` variables to the
  ``wordpress`` role. [carlalexander]

- Added support for the ``Content-Security-Policy`` header to the ``wordpress``
  role. [carlalexander]

- Added ``varnish_add_ban_lurker_headers`` variable so to add support for
  the Varnish ban lurker in the ``varnish`` role. [carlalexander]

- Added ``wordpress_varnish_normalize_query_parameters`` variable so that
  you can control the normalization of query parameters in the ``varnish``
  role. [carlalexander]

- Added the server ip address to the ``wordpress_fail2ban_ignoreip``
  variable. [carlalexander]

- Added ``wordpress_nginx_pki_realm`` variable to control the default
  PKI realm used by ``debops.nginx``. [carlalexander]

- Renamed ``swapfile_swappiness`` to ``swapfile__swappiness``. [carlalexander]

- Added ``wordpress_cron_path`` variable so that you control the path to
  ``wp-cron.php`` for the WordPress cron job. [carlalexander]

- Added ``wordpress_install_enabled`` variable so that you can disable
  the installation of WordPress. [schrapel]

- Added ``wordpress_fail2ban_enabled`` variable so that you can disable
  the installation and configuration of fail2ban. [carlalexander]

- Added ``debops.fail2ban`` dependency to ``wordpress`` role. [carlalexander]

- Renamed ``wordpress_varnish_server``, ``wordpress_backend_server``,
  ``wordpress_php_upstream`` and ``wordpress_varnish_upstream``. [carlalexander]

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

