=====================================================
Install Chef!
=====================================================

Chef is installed and configured in three main phases: setting up the Chef server, setting up a workstation, and then installing the chef-client on each node that will be under management by Chef:

* :doc:`Install the Chef Server </install_server>`; the Chef server may be :doc:`configured for high availability </server_high_availability>`, including `using Amazon Web Services <https://docs.chef.io/install_server_ha_aws.html>`_ machines and `on-premises using DRBD <https://docs.chef.io/install_server_ha_drbd.html>`_, and may be configured as `a single backend machine with multiple frontend machines <https://docs.chef.io/install_server_tiered.html>`_
* Set up your workstation by :doc:`installing the Chef DK </install_dk>`
* :doc:`Install the chef-client </install_bootstrap>`

Chef also has additional features that can be enabled as part of the setup and configuration process.

* The :doc:`Chef management console </manage>` provides a web user interface for managing objects on the Chef server
* :doc:`Chef reporting </reporting>` enables chef-client run reporting data from within the Chef management console
* :doc:`Chef replication </server_replication>` enables the synchronization of data from a primary Chef server to one (or more) secondary servers
* :doc:`Chef push jobs </push_jobs>` runs a job---an action or a command---against nodes independently of a chef-client run. Chef push jobs has :doc:`some additional configuration steps </install_push_jobs>`

.. tag server_replication_legacy_notice_short

.. note:: The capabilities of Chef replication can be reproduced using the features of Chef Automate workflow and we encourage customers to adopt Chef Automate going forward.

.. end_tag

In addition, there are some :doc:`post-configuration options </install_server_post>` for the Chef server.
