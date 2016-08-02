# UPGRADE FROM 0.2 to 0.3

**Important Note:** `{{ ansible_fqdn }}` refers to the fully-qualified domain name of
your server. In most cases, this means the name of your server.

### Varnish

 * Rename all `varnish_*` variables to `varnish__*`.

### WordPress

 * Rename all `wordpress_*` variables to `wordpress__*`.
