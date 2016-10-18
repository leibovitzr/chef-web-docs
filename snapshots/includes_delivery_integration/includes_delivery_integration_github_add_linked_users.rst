.. The contents of this file may be included in multiple topics (using the includes directive).
.. The contents of this file should be modified in a way that preserves its ability to appear in multiple topics.

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
