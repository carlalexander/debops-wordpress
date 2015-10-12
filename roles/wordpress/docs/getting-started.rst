Getting started
===============

.. contents::
   :local:

Ansible tags
------------

You can use Ansible ``--tags`` or ``--skip-tags`` parameters to limit what
tasks are performed during Ansible run. This can be used after host is first
configured to speed up playbook execution, when you are sure that most of the
configuration has not been changed.

Available role tags:

``role::wordpress``
  Main role tag, should be used in the playbook to execute all of the role
  tasks as well as role dependencies.

``type::dependency``
  This tag specifies which tasks are defined in role dependencies. You can use
  this to omit them using ``--skip-tags`` parameter.

``depend-of::wordpress``
  Execute all ``carlalexander.wordpress`` role dependencies in its context.

``depend::secret:wordpress``
  Run ``debops.secret`` dependent role in ``carlalexander.wordpress`` context.

``depend::php5:wordpress``
  Run ``debops.php5`` dependent role in ``carlalexander.wordpress`` context.

``depend::nginx:wordpress``
  Run ``debops.nginx`` dependent role in ``carlalexander.wordpress`` context.

``depend::pki:wordpress``
  Run ``debops.pki`` dependent role in ``carlalexander.wordpress`` context.

``depend::redis:wordpress``
  Run ``debops.redis`` dependent role in ``carlalexander.wordpress`` context.

``depend::hhvm:wordpress``
  Run ``carlalexander.hhvm`` dependent role in ``carlalexander.wordpress`` context.

``depend::mariadb:wordpress``
  Run ``debops.mariadb`` dependent role in ``carlalexander.wordpress`` context.

``depend::varnish:wordpress``
  Run ``carlalexander.varnish`` dependent role in ``carlalexander.wordpress`` context.

``depend::wpcli:wordpress``
  Run ``carlalexander.wpcli`` dependent role in ``carlalexander.wordpress`` context.

``role::wordpress:plugins``
  Manage WordPress plugins.

