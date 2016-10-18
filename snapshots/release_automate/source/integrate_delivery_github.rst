.. THIS PAGE IS IDENTICAL TO docs.chef.io/integrate_delivery_github.html BY DESIGN
.. THIS PAGE IS LOCATED AT THE /release/delivery/ PATH.

=====================================================
Integrate Chef Automate with GitHub
=====================================================

.. include:: ../../includes_chef_automate/includes_chef_automate_mark.rst 

You may integrate Chef Automate and GitHub Enterprise or a project that is hosted at https://github.com/. If you do this, you will be able to use GitHub as a **Source Code Provider** when creating a project. Additionally, when adding users to Chef Automate, to integrate them to a GitHub project, you must first complete the integration between Chef Automate and GitHub.

.. note:: This procedure is for Chef Automate deployments that will use GitHub Enterprise or https://github.com/ as the source control manager. Chef Automate also comes with default git capabilities that do not require the GitHub OAuth application.

This guide assumes you have successfully set up the following:

* A Chef Automate server set up
* User accounts in GitHub Enterprise and Chef Automate with matching usernames
* Have established SSL trust between Chef Automate and GitHub Enterprise servers

Trust SSL Certificate
=====================================================
Run the following steps to set up self-signed certificates for Chef Automate.

.. note:: This is only required if the GitHub Enterprise uses a self-signed SSL certificate or an internal certificate authority.

Debian
-----------------------------------------------------
For the Debian platform, do the following:

#. Log into the Chef Automate server as root.
#. Run the following command:

   .. code-block:: bash

      cd /usr/local/share/ca-certificates

#. Run the following command:

   .. code-block:: bash

      openssl s_client -showcerts -connect {your-ghe-server}:443 </dev/null 2>/dev/null|openssl x509 -outform PEM >{your-ghe-server}.crt

#. Run the following command:

   .. code-block:: bash

      update-ca-certificates

RHEL, Centos
-----------------------------------------------------
For Red Hat Enterprise Linux (6.x and higher) and CentOS (6.x and higher), do the following:

#. Log into the Chef Automate server as root.
#. Run the following command:

   .. code-block:: bash

      yum install ca-certificates

   .. note:: For 6.x servers, run this command only once.

#. Run the following command:

   .. code-block:: bash

      update-ca-trust force-enable

   .. note:: For 6.x servers, run this command only once.

#. Run the following command:

   .. code-block:: bash

      cd /etc/pki/ca-trust/source/anchors/

#. Run the following command:

   .. code-block:: bash

      openssl s_client -showcerts -connect {your-ghe-server}:443 </dev/null 2>/dev/null|openssl x509 -outform PEM >{your-ghe-server}.crt

#. Run the following command:

   .. code-block:: bash

      update-ca-trust extract

Create GitHub OAuth App
=====================================================
Go to one of the appropriate URLs listed below, depending on where you want to link the GitHub OAuth application:

* Individual Account: ``https://$GITHUB_SERVER/settings/applications``
* Organization: ``https://$GITHUB_SERVER/organizations/$ORGANIZATION/settings/applications``

Click **Register New Application** and set the following values:

.. list-table::
   :widths: 200 400
   :header-rows: 1

   * - Key
     - Value
   * - **Application Name**
     - ``Automate``
   * - **Homepage URL**
     - ``https://$AUTOMATE_SERVER/e/$DELIVERY_ENTERPRISE``
   * - **Authorization Callback URL**
     - ``https://$AUTOMATE_SERVER/api/v0/github_auth_callback``

Click **Register Application** and take note of the generated ``Client ID`` and ``Client Secret`` in the upper left corner.

Add App to Chef Automate
=====================================================
To add the GitHub OAuth app to Chef Automate, log in to the Chef Automate server and run the following command:

**For GitHub Enterprise**

.. code-block:: bash

   $ delivery-ctl setup-github-enterprise $GHE_SERVER_ROOT_URL $CLIENT_ID $CLIENT_SECRET

**For GitHub.com**

.. code-block:: bash

   $ delivery-ctl setup-github $CLIENT_ID $CLIENT_SECRET

Request GitHub Token
=====================================================
Log in to the Chef Automate server and run the following command.

**For GitHub Enterprise**

.. code-block:: bash

   $ delivery-ctl setup-github-enterprise-token $AUTOMATE_ENTERPRISE

**For GitHub.com**

.. code-block:: bash

   $ delivery-ctl setup-github-token $AUTOMATE_ENTERPRISE

Follow the URL given to finish authorizing Chef Automate with GitHub.

.. note:: If you are using a service account with GitHub Enterprise, you need to complete the OAuth process as the service account user.

Create a Project
=====================================================
Before you begin you will need an existing GitHub repo with at least one commit and also you have to grant admin rights to the Chef Automate account connected to GitHub.

#. Open your organization page in the Chef Automate web UI and click the Add icon (plus sign) for **Add a New Project**. A text area opens.
#. Select the **GitHub** option for **Source Code Provider** and enter the **GitHub Organization Name**, **GitHub Project Name** (your project name should match your GitHub repo name), and the branch you wish to use as your primary pipeline.
#. Click **Save & Close**.

There is currently no process for migrating an existing Chef Automate project to one that is backed by GitHub.

Add Linked Users
=====================================================
.. include:: ../../includes_delivery_integration/includes_delivery_integration_github_add_linked_users.rst

Initialize a Project
=====================================================
After associating the appropriate GitHub and Chef Automate user accounts, you can setup and initialize your GitHub repo to be managed by Chef Automate.

#. Create a local clone of a GitHub repo and ``cd`` into it.
#. Create a ``.delivery/cli.toml`` using ``delivery setup``:

   .. code-block:: bash

      $ delivery setup --ent=$DELIVERY_ENTERPRISE --org=$DELIVERY_ORG --user=$DELIVERY_USER_NAME --server=$DELIVERY_SERVER

#. Run ``delivery init``to generate a ``.delivery/config.json`` file, create a build cookbook, and submit a change to Chef Automate to initialize a pipeline for the project. Changes are opened in the Chef Automate web UI. At this point, a corresponding pull request is shown in GitHub.

   .. include:: ../../step_ctl_delivery/step_ctl_delivery_init_github_project.rst

#. Push the code to GitHub.

   .. code-block:: bash

      $ git push origin add_delivery_config

#. Finally, create a pull request from this change in the GitHub webui.

Handle Untrusted PRs
=====================================================
By default all pull requests from GitHub users that are not linked with a Chef Automate user will be ignored.

To accept pull requests from an unlinked user you may add the ``untrusted_github_user`` using the command below.

.. code-block:: bash

   $ sudo delivery-ctl create-user $AUTOMATE_ENTERPRISE untrusted_github_user --roles=committer

A pull request opened by a GitHub user who is not linked with a Chef Automate user will be labeled as ``Quarantined``. A change for this pull request owned by ``untrusted_github_user`` will be created but the **Verify** stage will not be triggered. An authorized user may review the pull request and add a comment with ``@delivery review`` command to reassign the change to their user account and trigger the **Verify** stage.
