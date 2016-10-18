=====================================================
chef-sync.rb
=====================================================

.. tag chef_automate_mark

.. image:: ../images/chef_automate_full.png
   :width: 40px
   :height: 17px

.. end_tag

.. tag config_rb_sync

The chef-sync.rb file is the default configuration file used by Chef replication.

.. end_tag

.. note:: .. tag chef_subscriptions

          This feature is included as part of the Chef Automate license agreement and is `available via subscription <https://www.chef.io/pricing/>`_.

          .. end_tag

Settings
=====================================================
.. tag config_rb_sync_settings

This configuration file has the following settings:

``bootstrap``
   Indicates whether an attempt to bootstrap the Chef server is made. Generally only enabled on systems that have bootstrap enabled via a ``server`` entry. Default value: ``true``.

``chef_base_path``
   Default value: ``'/opt/opscode'``.

``ec_sync_client['dir']``
   The working directory. The default value is the recommended value. Default value: ``'/var/opt/chef-sync/ec_sync_client'``.

``ec_sync_client['enable']``
   Enable a service. Default value: ``true``.

``ec_sync_client['ha']``
   Run the Chef server in a high availability topology. Default value: ``false``.

``ec_sync_client['log_directory']``
   The directory in which log data is stored. The default value is the recommended value. Default value: ``'/var/log/opscode/chef-sync/client'``.

``ec_sync_client['log_rotation']``
   The log rotation policy for this service. Log files are rotated when they exceed ``file_maxbytes``. The maximum number of log files in the rotation is defined by ``num_to_keep``. Default value: ``{ 'file_maxbytes' => 104857600, 'num_to_keep' => 10 }``

``ec_sync_client['master']``
   Default value: ``'https://127.0.0.1'``.

``ec_sync_client['organizations']``
   Default value: ``[]``.

``ec_sync_client['replica']``
   Default value: ``'https://127.0.0.1'``.

``ec_sync_client['socket_path']``
   Default value: ``'/var/opt/chef-sync/ec_sync_client/ec_sync.sock'``.

``ec_sync_client['sync_key']``
   Default value: ``'/etc/chef-sync/ec_sync_user.pem'``.

``ec_sync_client['sync_user']``
   Default value: ``'ec_sync_user'``.

``ec_sync_server['auth_skew']``
   Default value: ``'900'``.

``ec_sync_server['db_pool_size']``
   The number of open connections to PostgreSQL that are maintained by the service. Default value: ``10``.

``ec_sync_server['dir']``
   The working directory. The default value is the recommended value. Default value: ``'/var/opt/chef-sync/ec_sync_server'``.

``ec_sync_server['enable']``
   Enable a service. Default value: ``true``.

``ec_sync_server['ha']``
   Run the Chef server in a high availability topology. Default value: ``false``.

``ec_sync_server['listen']``
   The IP address on which the service is to listen. Default value: ``'127.0.0.1'``.

``ec_sync_server['log_directory']``
   The directory in which log data is stored. The default value is the recommended value. Default value: ``'/var/log/opscode/chef-sync/server'``.

``ec_sync_server['log_rotation']``
   The log rotation policy for this service. Log files are rotated when they exceed ``file_maxbytes``. The maximum number of log files in the rotation is defined by ``num_to_keep``. Default value: ``{ 'file_maxbytes' => 104857600, 'num_to_keep' => 10 }``

``ec_sync_server['port']``
   The port on which the service is to listen. Default value: ``9996``.

``ec_sync_server['vip']``
   The virtual IP address. Default value: ``'127.0.0.1'``.

``install_path'``
   Default value: ``'/opt/chef-sync'``.

``master``
   Use to specify the root URL for the master Chef server.

``name``
   Default value: ``'sync'``.

``organization``
   An array that specifies the source and destination organization pairs for synchronization.

``replica``
   Use to specify the root URL for the replica Chef server.

``role``
   Use to specify if ``chef-sync`` is installed as a master Chef server, a replica Chef server, or both. Possible values: ``:master``, ``:master_and_replica``, ``:replica``. Default value: ``:replica``.

``user['home']``
   The home directory for the user under which Chef server services run. Default value: ``'/opt/opscode/embedded'``.

``user['shell']``
   The shell for the user under which Chef server services run. Default value: ``'/bin/sh'``.

``user['username']``
   The user name under which Chef server services run. Default value: ``opscode``.

.. end_tag

