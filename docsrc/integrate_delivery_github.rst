=====================================================
Integrate Chef Automate with GitHub
=====================================================

.. tag chef_automate_mark

.. image:: ../images/chef_automate_full.png
   :width: 40px
   :height: 17px

.. end_tag

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
.. tag delivery_integration_github_add_linked_users

You must associate a GitHub user with a Chef Automate user in order to successfully create changes from GitHub pull requests.

To onboard a user for an integrated GitHub Enterprise project or one that is hosted at https://github.com/:

#. Have the user that you want to add clone the repo for the project you want them to join. Ensure that they have write permissions to the repo if you want to allow them to submit pull requests.
#. Add or edit any users who are managed by the LDAP integration.
#. From a local checkout of a Chef Automate project, run the appropriate Chef Automate command that associates a GitHub user with a Chef Automate user.

   .. note:: The Delivery CLI commands are for a user to link their own account to GitHub, or others if the user has the **Admin** role; ``api`` is an argument to the Delivery CLI command. The ``delivery-ctl`` command can only be run by an administrator from the Chef Automate server and can affect any user.

   For GitHub Enterprise:

   .. code-block:: bash

      $ delivery api put users/$AUTOMATE_USERNAME/set-oauth-alias --data='{"app_name":"github-enterprise","alias":"$GITHUB_USERNAME"}'

   For GitHub:

   .. code-block:: bash

      $ delivery api put users/$AUTOMATE_USERNAME/set-oauth-alias --data='{"app_name":"github","alias":"$GITHUB_USERNAME"}'

   *Or*, as an administrator, run the command line tool ``delivery-ctl``. The command uses the enterprise name you set when configuring Chef Automate. The username can be an LDAP username (if LDAP integration has been completed), or an internal username:

    For GitHub Enterprise:

    .. code-block:: bash

       $ delivery-ctl link-github-enterprise-user $AUTOMATE_ENTERPRISE_NAME $AUTOMATE_USERNAME $GITHUB_USERNAME

    For GitHub:

   .. code-block:: bash

      $ delivery-ctl link-github-user $AUTOMATE_ENTERPRISE_NAME $AUTOMATE_USERNAME $GITHUB_USERNAME

The associated user can now checkout the repository, make changes on a feature branch and submit the changes for review.

Note the following constraints:

* You may not link two GitHub accounts to a single Chef Automate user.
* Two users may not share a GitHub account

.. end_tag

Initialize a Project
=====================================================
After associating the appropriate GitHub and Chef Automate user accounts, you can setup and initialize your GitHub repo to be managed by Chef Automate.

#. Create a local clone of a GitHub repo and ``cd`` into it.
#. Create a ``.delivery/cli.toml`` using ``delivery setup``:

   .. code-block:: bash

      $ delivery setup --ent=$DELIVERY_ENTERPRISE --org=$DELIVERY_ORG --user=$DELIVERY_USER_NAME --server=$DELIVERY_SERVER

#. Run ``delivery init``to generate a ``.delivery/config.json`` file, create a build cookbook, and submit a change to Chef Automate to initialize a pipeline for the project. Changes are opened in the Chef Automate web UI. At this point, a corresponding pull request is shown in GitHub.

   .. tag ctl_delivery_init_github_project

   To initialize a project using a GitHub repository, run a command similar to:

   .. code-block:: bash

      $ delivery init --github ORG_NAME -r REPO_NAME

   where ``ORG_NAME`` is the name of the GitHub organization and ``REPO_NAME`` is the name of the repository in GitHub. For example to initialize the ``seapower`` repository in GitHub with the ``chef-cookbooks`` organization:

   .. code-block:: bash

      $ delivery init --github chef-cookbooks -r seapower

   and returns output similar to:

   .. code-block:: bash

      Chef Delivery
      Loading configuration from /Users/albertatom/chef/delivery/organizations/sandbox/seapower
      Is /Users/albertatom/chef/delivery/organizations/sandbox/seapower a git repo?  yes
      Project seapower already exists.
      Creating and checking out add-delivery-config feature branch: done
      Generating build cookbook skeleton
      Using cached copy of build-cookbook generator "/Users/albertatom/.delivery/cache/generator-cookbooks/pcb"
      Build-cookbook generated: "chef" "generate" "cookbook" ".delivery/build-cookbook" "-g" "/Users/albertatom/.delivery/cache/generator-cookbooks/pcb"
      Adding and commiting build-cookbook: done
      Writing configuration to /Users/albertatom/chef/delivery/organizations/sandbox/seapower/.delivery/config.json
      New delivery configuration
      --------------------------
      {
        "version": "2",
        "build_cookbook": {
          "path": ".delivery/build-cookbook",
          "name": "build-cookbook"
        },
        "skip_phases": [],
        "build_nodes": {},
        "dependencies": []
      }
      Git add and commit delivery config: done
      Push add-delivery-config branch and create Pull Request

   .. end_tag

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
