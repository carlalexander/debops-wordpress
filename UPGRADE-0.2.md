# UPGRADE FROM 0.1 to 0.2

**Important Note:** `{{ ansible_fqdn }}` refers to the fully-qualified domain name of your server. In most cases, this means
the name of your server.

### General

 * Rename `[all_servers]` group to `[debops_all_hosts]` in `hosts` file

### MariaDB

 * Move `secret/credentials/{{ ansible_fqdn }}/mariadb/root/password` to `secret/credentials/{{ ansible_fqdn }}/mariadb/localhost/root/password`

 * Move `secret/credentials/{{ ansible_fqdn }}/mariadb/{{ wordpress_database_user }}/password` to `secret/mariadb/{{ ansible_fqdn }}/credentials/{{ wordpress_database_user }}/password`

### WordPress

 * Move `secret/credentials/{{ ansible_fqdn }}/wordpress/{{ wordpress_admin_username }}/password` to `secret/wordpress/{{ wordpress_domain }}/credentials/{{ wordpress_admin_username }}/password`

 * Rename `wordpress_database_hostname` option to `wordpress_database_server`

 * Rename `wordpress_database_username` option to `wordpress_database_user`

 * Rename `wordpress_url` option to `wordpress_domain`
