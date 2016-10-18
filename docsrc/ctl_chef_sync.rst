=====================================================
chef-sync-ctl (executable)
=====================================================

.. tag server_replication_legacy_notice_long

.. note:: This topic is meant to support existing customers using Chef replication. The capabilities of Chef replication can be reproduced using the features of Chef Automate workflow and we encourage customers to adopt Chef Automate going forward.

.. end_tag

.. tag ctl_chef_sync_summary

chef-sync-ctl is the command line tool for Chef replication, which allows asynchronous replication of cookbook content across Chef server organizations. This is done from a single, primary Chef server organization to one (or more) replicas of that Chef server.

.. end_tag

.. note:: .. tag chef_subscriptions

          This feature is included as part of the Chef Automate license agreement and is `available via subscription <https://www.chef.io/pricing/>`_.

          .. end_tag

manager-log
=====================================================
.. tag ctl_chef_sync_manager_log

Use to show the log file for the synchronization manager. This subcommand should only be run for replica organizations.

This option has the following syntax:

.. code-block:: bash

   $ chef-sync-ctl manager-log

.. end_tag

prepare-org
=====================================================
.. tag ctl_chef_sync_prepare_org

Use to prepare the specified organization for synchronization by associating the synchronizing user, and then making that user an administrator. This subcommand must be run on both the single, primary Chef server organization and all replica organizations.

This option has the following syntax:

.. code-block:: bash

   $ chef-sync-ctl prepare-org ORG_NAME

This option will compile a list of group names, organization names, and actors (users, clients, and groups).

.. end_tag

sync-log
=====================================================
.. tag ctl_chef_sync_log

Use to show the log file for the specified organization. This subcommand should only be run for replica organizations.

This option has the following syntax:

.. code-block:: bash

   $ chef-sync-ctl sync-log ORG_NAME

.. end_tag

sync-start
=====================================================
.. tag ctl_chef_sync_start

Use to start synchronizing an organization. This subcommand should only be run for replica organizations.

This option has the following syntax:

.. code-block:: bash

   $ chef-sync-ctl sync-start ORG_NAME

.. end_tag

sync-status
=====================================================
.. tag ctl_chef_sync_status

Use to show the current status of all organizations that are synchronizing. This subcommand should only be run for replica organizations.

This option has the following syntax:

.. code-block:: bash

   $ chef-sync-ctl sync-status

and will return a list that shows the organization name, its status, the last synchronization time, and the time at which the synchronization process will begin again.

.. end_tag

sync-stop
=====================================================
.. tag ctl_chef_sync_stop

Use to stop synchronizing an organization. This subcommand should only be run for replica organizations.

This option has the following syntax:

.. code-block:: bash

   $ chef-sync-ctl sync-stop ORG_NAME

.. end_tag

unsynced-objects
=====================================================
.. tag ctl_chef_sync_unsynced_objects

Use to show unsynchronized objects for the specified organization. This subcommand should only be run for replica organizations.

This option has the following syntax:

.. code-block:: bash

   $ chef-sync-ctl unsynced-objects ORG_NAME

.. end_tag

