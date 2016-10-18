=====================================================
Chef Manage Tasks
=====================================================

This topic is an alphabetical list of the various tasks that can be performed when using Chef management console.

Add Client
=====================================================
.. tag manage_webui_policy_client_add

To add a client key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Click **Create**.
#. In the **Create Client** dialog box, enter the name of the client key.

   .. image:: ../images/step_manage_webui_policy_client_add.png

   Click **Create Client**.
#. Copy the private key:

   .. image:: ../images/step_manage_webui_policy_client_add_private_key.png

   or download and save the private key locally:

   .. image:: ../images/step_manage_webui_policy_client_add_private_key_download.png

.. end_tag

Add Data Bag
=====================================================
.. tag manage_webui_policy_data_bag_add

To add a data bag:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Data Bags**.
#. Click **Create**.
#. In the **Create a Data Bag** dialog box, enter the name of the data bag.

   .. image:: ../images/step_manage_webui_policy_data_bag_add.png

#. Click **Create Data Bag**.

.. end_tag

Add Data Bag Item
=====================================================
.. tag manage_webui_policy_data_bag_add_item

To add a data bag item:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Data Bags**.
#. Select a data bag.
#. Click **Create Item**.
#. In the **Create a Data Bag Item** dialog box, enter the data bag identifier, and then JSON data that defines the data bag item.

   .. image:: ../images/step_manage_webui_policy_data_bag_add_item.png

#. Click **Create Data Bag Item**.

.. end_tag

Add Environment
=====================================================
.. tag manage_webui_policy_environment_add

To add an environment:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.
#. Click **Create**.
#. In the **Create an Environment** dialog box, enter the name of the environment and a description.

   .. image:: ../images/step_manage_webui_policy_environment_add.png

   Click **Next**.
#. Optional. Set a constraint by choosing a name, an operator, and a version:

   .. image:: ../images/step_manage_webui_policy_environment_add_constraint.png

   Click **Add**. Continue this process until all constraints are added. When finished, click **Next**.
#. Optional. Add default attributes as JSON data:

   .. image:: ../images/step_manage_webui_policy_environment_add_default_attribute.png

   Click **Next**.
#. Optional. Add override attributes as JSON data:

   .. image:: ../images/step_manage_webui_policy_environment_add_override_attribute.png

#. Click **Create Environment**.

.. end_tag

Add Group
=====================================================
To add a group:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Groups**.
#. Select a group.
#. Click the **Create**.

   .. image:: ../images/step_manage_webui_admin_groups_add.png

#. Enter the name of the group and then click **Create Group**.

Add Org
=====================================================
To add an organization:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Organizations**.
#. Click **Create**.
#. In the **Create an Organization** dialog box, enter the full and short names for the organization:

   .. image:: ../images/step_manage_webui_admin_organization_add.png

#. Click **Create Organization**.

Add Recipe to Run-list
=====================================================
.. tag manage_webui_node_run_list_add_role_or_recipe

To add a role or recipe to a run-list:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click **Edit Run List**.
#. In the **Edit Node Run List** dialog box, drag the role or recipe from the **Available Roles** or **Available Recipes** lists to the current run-list.

   .. image:: ../images/step_manage_webui_node_run_list_add_role_or_recipe.png

#. Click **Save Run List**.

.. end_tag

Add Role
=====================================================
.. tag manage_webui_policy_role_add

To add a role:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.
#. Click **Create**.
#. In the **Create Role** dialog box, enter the name of the role and a description.

   .. image:: ../images/step_manage_webui_policy_role_add.png

   Click **Next**.
#. Optional. Build the run-list from the list of available roles and recipes:

   .. image:: ../images/step_manage_webui_policy_role_add_run_list.png

   Click **Next**.
#. Optional. Add default attributes as JSON data:

   .. image:: ../images/step_manage_webui_policy_role_add_default_attribute.png

   Click **Next**.
#. Optional. Add override attributes as JSON data:

   .. image:: ../images/step_manage_webui_policy_role_add_override_attribute.png

#. Click **Create Role**.

.. end_tag

Add Role to Run-list
=====================================================
.. tag manage_webui_node_run_list_add_role_or_recipe

To add a role or recipe to a run-list:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click **Edit Run List**.
#. In the **Edit Node Run List** dialog box, drag the role or recipe from the **Available Roles** or **Available Recipes** lists to the current run-list.

   .. image:: ../images/step_manage_webui_node_run_list_add_role_or_recipe.png

#. Click **Save Run List**.

.. end_tag

Add Tag
=====================================================
.. tag manage_webui_node_tags_add

To add tags to a node (or a group of nodes):

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node (or a group of nodes).
#. Click **Manage Tags**.
#. In the **Manage Node Tags** dialog box, enter the name of the tag and then select **Add Tags** from the drop-down.

   .. image:: ../images/step_manage_webui_node_tags_add.png

#. Click **Update Tags**.

.. end_tag

Add Validation Client
=====================================================
.. tag manage_webui_policy_validation_add

To add a chef-validator key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Click **Create**.
#. In the **Create Client** dialog box, enter the name of the chef-validator key.

   .. image:: ../images/step_manage_webui_policy_validation_add.png

   Select the **Validation Client** option. Click **Create Client**.
#. Copy the private key:

   .. image:: ../images/step_manage_webui_policy_client_add_private_key.png

   or download and save the private key locally:

   .. image:: ../images/step_manage_webui_policy_client_add_private_key_download.png

.. end_tag

Change Password
=====================================================
.. tag manage_webui_admin_users_change_password

To change a user's password:

#. Open the Chef management console.
#. From the drop-down list next to your username, select **My Profile**.
#. Under **Users**, click **Change Password**.
#. In the **Change Password**, enter the old password and then the new password.

   .. image:: ../images/step_manage_webui_admin_users_change_password.png

#. When finished, click **Change Password**.

.. end_tag

Delete Client
=====================================================
.. tag manage_webui_policy_client_delete

To delete a client key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Select a client key.
#. Click **Delete**.

   .. image:: ../images/step_manage_webui_policy_client_delete.png

.. end_tag

Delete Cookbook
=====================================================
.. note:: The Chef management console web user interface currently requires that cookbooks be deleted using knife, the command line interface to the Chef server.

**To delete a cookbook**

.. tag knife_cookbook_delete

.. To delete version "0.8" from a cookbook named "smartmon", enter:

.. code-block:: bash

   $ knife cookbook delete cookbook_name version

For example:

.. code-block:: bash

   $ knife cookbook delete smartmon 0.8

Type ``Y`` to confirm a deletion.

.. end_tag

Delete Data Bag
=====================================================
.. tag manage_webui_policy_data_bag_delete

To delete a data bag:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Data Bags**.
#. Select a data bag.
#. Click **Delete**.

   .. image:: ../images/step_manage_webui_policy_data_bag_delete.png

.. end_tag

Delete Data Bag Item
=====================================================
.. tag manage_webui_policy_data_bag_delete_item

To delete a data bag item:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Data Bags**.
#. Select a data bag.
#. Select the **Items** tab.
#. Select a data bag.
#. Click **Delete**.

   .. image:: ../images/step_manage_webui_policy_data_bag_delete_item.png

.. end_tag

Delete Environment
=====================================================
.. tag manage_webui_policy_environment_delete

To delete an environment:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.
#. Select an environment.
#. Click **Delete**.

   .. image:: ../images/step_manage_webui_policy_environment_delete.png

.. end_tag

Delete Group
=====================================================
To delete a group:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Groups**.
#. Select a group.
#. Click **Delete**.

   .. image:: ../images/step_manage_webui_admin_groups_delete.png

.. note:: The ``admins``, ``billing_admins`` (hosted Chef server only), ``clients``, and ``users`` are required groups for the Chef server and cannot be deleted.

Delete Node
=====================================================
.. tag manage_webui_node_delete

To delete a node:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click **Delete**.
#. Confirm:

   .. image:: ../images/step_manage_webui_node_delete.png

.. end_tag

Delete Org
=====================================================
To delete an organization:

#. Contact Chef support.

Delete Role
=====================================================
.. tag manage_webui_policy_role_delete

To delete a role:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.
#. Select a role.
#. Click **Delete**.

   .. image:: ../images/step_manage_webui_policy_role_delete.png

.. end_tag

Delete Tag
=====================================================
.. tag manage_webui_node_tags_delete

To delete tags for a node (or a group of nodes):

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node (or a group of nodes).
#. Click **Manage Tags**.
#. In the **Manage Node Tags** dialog box, enter the name of the tag and then select **Delete Tags** from the drop-down.

   .. image:: ../images/step_manage_webui_node_tags_delete.png

#. Click **Update Tags**.

.. end_tag

Delete Validation Client
=====================================================
.. tag manage_webui_policy_validation_delete

To delete a chef-validator key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Select a chef-validator key.
#. Click **Delete**.

   .. image:: ../images/step_manage_webui_policy_validation_delete.png

.. end_tag

Download Cookbook File
=====================================================
.. tag manage_webui_policy_cookbook_file_download

To download a file that is located in a cookbook:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Cookbooks**.
#. Select the file type: **Attributes**, **Definitions**, **Files**, **Recipes**, **Templates**, or **Root Files**.
#. Select a file.
#. Click **Download File**:

   .. image:: ../images/step_manage_webui_policy_cookbook_download.png

#. Specify the location to which the file should be saved.

.. end_tag

Edit Data Bag Item
=====================================================
.. tag manage_webui_policy_data_bag_edit_item

To edit a data bag item:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Data Bags**.
#. Select a data bag.
#. Select the **Items** tab.
#. Select a data bag.
#. Click **Edit**.

   .. image:: ../images/step_manage_webui_policy_data_bag_edit_item.png

#. Make your changes.
#. Click **Save Item**.

.. end_tag

Edit Environment Defaults
=====================================================
.. tag manage_webui_policy_environment_view_attributes_default_edit

To edit default attributes for an environment:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.
#. Select an environment.
#. Click the **Attributes** tab.
#. Under **Default Attributes**, click **Edit**.
#. In the **Edit Environment Attributes** dialog box, enter the JSON data that defines the attribute (or attributes).

   .. image:: ../images/step_manage_webui_policy_environment_edit_attribute.png

#. Click **Save**.

.. end_tag

Edit Environment Details
=====================================================
.. tag manage_webui_policy_environment_edit_details

To edit the details of an environment:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.
#. Select an environment.
#. Click the **Details** tab.
#. Click **Edit**.

.. end_tag

Edit Environment Overrides
=====================================================
.. tag manage_webui_policy_environment_view_attributes_override_edit

To edit override attributes for an environment:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.
#. Select an environment.
#. Click the **Attributes** tab.
#. Under **Override Attributes**, click **Edit**.
#. In the **Edit Environment Attributes** dialog box, enter the JSON data that defines the attribute (or attributes).

   .. image:: ../images/step_manage_webui_policy_environment_edit_attribute.png

#. Click **Save Attributes**.

.. end_tag

Edit Node Attribute
=====================================================
.. tag manage_webui_node_attributes_edit

To edit node attributes:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click the **Attributes** tab.
#. Click **Edit**.
#. In the **Edit Node Attributes** dialog box, make your changes:

   .. image:: ../images/step_manage_webui_node_attributes_edit.png

#. Click **Save Attributes**.

.. end_tag

Edit Node Run-list
=====================================================
.. tag manage_webui_node_run_list_edit

To edit a run-list:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click **Edit Run List**.
#. In the **Edit Node Run List** dialog box, make your changes.
#. Click **Save Run List**.

.. end_tag

Edit Role Defaults
=====================================================
.. tag manage_webui_policy_role_view_attributes_default_edit

To edit default attributes for a role:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.
#. Select a role.
#. Click the **Attributes** tab.
#. Under **Default Attributes**, click **Edit**.
#. In the **Edit Role Attributes** dialog box, enter the JSON data that defines the attribute (or attributes).

   .. image:: ../images/step_manage_webui_policy_role_edit_attribute.png

#. Click **Save Attributes**.

.. end_tag

Edit Role Overrides
=====================================================
.. tag manage_webui_policy_role_view_attributes_override_edit

To edit override attributes for a role:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.
#. Select a role.
#. Click the **Attributes** tab.
#. Under **Override Attributes**, click **Edit**.
#. In the **Edit Role Attributes** dialog box, enter the JSON data that defines the attribute (or attributes).

   .. image:: ../images/step_manage_webui_policy_role_edit_attribute.png

#. Click **Save Attributes**.

.. end_tag

Edit Role Run-list
=====================================================
.. tag manage_webui_policy_role_edit_run_list

To edit the run-list for a role:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.
#. Select a role.
#. Click **Edit Run List**.

   .. image:: ../images/step_manage_webui_policy_role_edit_run_list.png

#. Make your changes.
#. Click **Save Run List**.

.. end_tag

Generate Config File
=====================================================
To generate a new knife configuration file:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Organizations**.
#. Click **Generate Knife Config**.
#. Specify the location to which the configuration file will be downloaded.

Get Starter Kit
=====================================================
To get the starter kit:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Organizations**.
#. Click **Starter Kit**.
#. Follow the steps on the starter kit page.

Invite a User
=====================================================
.. tag manage_webui_admin_organization_invite_user

To invite a user to an organization:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Organizations**.
#. Click **Invite User**.
#. In the **Invite User** dialog box, enter the Chef server user name for the user to be invited, and then click the **Invite** button:

   .. image:: ../images/step_manage_webui_admin_organization_invite_user.png

   .. image:: ../images/step_manage_webui_admin_organization_invite_user_pending.png

#. After the user accepts the invitation, they will be a member of this organization.

.. end_tag

Leave Org
=====================================================
.. tag manage_webui_admin_organization_leave

To leave an organization:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Organizations**.
#. Click **Leave Organization**.
#. In the **Leave Organization** dialog box, confirm that you want to leave the organization, and then click the **Leave Organization** button:

   .. image:: ../images/step_manage_webui_admin_organization_leave.png

.. end_tag

Log Out
=====================================================
To log out of the Chef management console:

#. Open the Chef management console.
#. From the drop-down list next to your username, select **Log Out**.

Remove Recipe from Run-list
=====================================================
.. tag manage_webui_node_run_list_remove_role_or_recipe

To remove a role or recipe from a run-list:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click **Edit Run List**.
#. In the **Edit Node Run List** dialog box, drag the role or recipe from the **Current Run List** to the list of available roles or recipes.

   .. image:: ../images/step_manage_webui_node_run_list_remove_role_or_recipe.png

#. Click **Save Run List**.

.. end_tag

Remove Admin from Org
=====================================================
.. tag manage_webui_admin_users_remove_admin_from_org

Removing a member of the ``admins`` group from an organization requires the user to be removed from the ``admins`` group before they can be removed from the organization:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Groups**.
#. Select the **Groups** group.
#. Select a user to be removed from the **Groups** group:

   .. image:: ../images/step_manage_webui_admin_remove_admin_pre.png

#. Click **Remove**.

   .. image:: ../images/step_manage_webui_admin_remove_admin_post.png

#. Click **Users**.
#. Select a user.
#. Click **Remove from Organization**.

   .. image:: ../images/step_manage_webui_admin_remove_admin_success.png

.. end_tag

Remove Role from Run-list
=====================================================
.. tag manage_webui_node_run_list_remove_role_or_recipe

To remove a role or recipe from a run-list:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click **Edit Run List**.
#. In the **Edit Node Run List** dialog box, drag the role or recipe from the **Current Run List** to the list of available roles or recipes.

   .. image:: ../images/step_manage_webui_node_run_list_remove_role_or_recipe.png

#. Click **Save Run List**.

.. end_tag

Remove User from Org
=====================================================
.. tag manage_webui_admin_users_remove_from_org

To remove a user from an organization:

#. Open the Chef management console.
#. From the drop-down list next to your username, select **My Profile**.
#. Under **Users**, click **Leave Organization**.
#. In the **Leave Organization** dialog box, confirm that the key should be regenerated and click the **Leave Organization** button:

   .. image:: ../images/step_manage_webui_admin_organization_leave.png

.. end_tag

Reset Client Key
=====================================================
.. tag manage_webui_policy_client_reset_key

To regenerate a client key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Select a client key.
#. Click the **Details** tab.
#. Click **Reset Key**.
#. In the **Reset Key** dialog box, confirm that the key should be regenerated and click the **Reset Key** button:

   .. image:: ../images/step_manage_webui_admin_organization_reset_key.png

#. Copy the private key:

   .. image:: ../images/step_manage_webui_policy_client_reset_key_copy.png

   or download and save the private key locally:

   .. image:: ../images/step_manage_webui_policy_client_reset_key_download.png

.. end_tag

Reset Node Key
=====================================================
.. tag manage_webui_node_reset_key

To reset the validation key for a node:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click **Edit Run List**.
#. In the **Reset Key** dialog box, confirm that the key should be regenerated and click the **Regenerate Key** button:

   .. image:: ../images/step_manage_webui_admin_organization_reset_key.png

#. In the **Reset Key** dialog box, copy the key directly from the dialog box or click the **Download** button to download the key to your local machine:

   .. image:: ../images/step_manage_webui_admin_organization_reset_key_regenerated.png

.. end_tag

Reset Org Key
=====================================================
To reset the validation key:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Organizations**.
#. Click **Reset Validation Key**.
#. In the **Reset Key** dialog box, confirm that the key should be regenerated and click the **Regenerate Key** button:

   .. image:: ../images/step_manage_webui_admin_organization_reset_key.png

#. In the **Reset Key** dialog box, copy the key directly from the dialog box or click the **Download** button to download the key to your local machine:

   .. image:: ../images/step_manage_webui_admin_organization_reset_key_regenerated.png

Reset User Key
=====================================================
.. tag manage_webui_admin_users_reset_key

To reset a user's validation key:

#. Open the Chef management console.
#. From the drop-down list next to your username, select **My Profile**.
#. Under **Users**, click **Reset Key**.
#. In the **Reset Key** dialog box, confirm that the key should be regenerated and click the **Regenerate Key** button:

   .. image:: ../images/step_manage_webui_admin_organization_reset_key.png

#. In the **Reset Key** dialog box, copy the key directly from the dialog box or click the **Download** button to download the key to your local machine:

   .. image:: ../images/step_manage_webui_admin_organization_reset_key_regenerated.png

.. end_tag

Reset Validation Client Key
=====================================================
.. tag manage_webui_policy_validation_reset_key

To reset a chef-validator key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Select a chef-validator key.
#. Click the **Details** tab.
#. Click **Reset Key**.
#. In the **Reset Key** dialog box, confirm that the key should be regenerated and click the **Reset Key** button:

   .. image:: ../images/step_manage_webui_admin_organization_reset_key.png

#. Copy the private key:

   .. image:: ../images/step_manage_webui_policy_client_reset_key_copy.png

   or download and save the private key locally:

   .. image:: ../images/step_manage_webui_policy_client_reset_key_download.png

.. end_tag

Search Nodes
=====================================================
.. tag manage_webui_nodes_search

To search nodes:

#. Open the Chef management console.
#. Click **Nodes**.
#. In the search box in the upper right, enter the search query and click the search icon.

   .. image:: ../images/step_manage_webui_nodes_search.png

#. The results will appear in the list below.

.. end_tag

Set Client Permissions
=====================================================
.. tag manage_webui_policy_client_permissions_set

To set permissions list for a client key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Select a client key.
#. Click the **Permissions** tab.
#. For each group listed under **Name**, select or de-select the **Read**, **Update**, **Delete**, and **Grant** permissions.

.. end_tag

Set Cookbook Permissions
=====================================================
.. tag manage_webui_policy_cookbook_permissions_set

To set permissions list for a cookbook object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Cookbooks**.
#. Select a cookbook.
#. Click the **Permissions** tab.
#. For each group listed under **Name**, select or de-select the **Read**, **Update**, **Delete**, and **Grant** permissions.

.. end_tag

Set Data Bag Permissions
=====================================================
.. tag manage_webui_policy_data_bag_permissions_set

To set permissions list for a data bag object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Data Bags**.
#. Select a data bag.
#. Click the **Permissions** tab.
#. For each group listed under **Name**, select or de-select the **Read**, **Update**, **Delete**, and **Grant** permissions.

.. end_tag

Set Environment
=====================================================
.. tag manage_webui_node_details_set_environment

To set the environment for a node:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click the **Details** tab.
#. In the top right, from the **Environment** drop-down, select the environment:

   .. image:: ../images/step_manage_webui_node_details_set_environment.png

#. Click **Save**.

.. end_tag

Set Environment Permissions
=====================================================
.. tag manage_webui_policy_environment_permissions_set

To set permissions list for an environment object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.
#. Select an environment.
#. Click the **Permissions** tab.
#. For each group listed under **Name**, select or de-select the **Read**, **Update**, **Delete**, and **Grant** permissions.

.. end_tag

Set Global Permissions
=====================================================
To set global permissions for Chef server objects:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Global Permissions**.
#. Select the Chef server object type: ``cookbooks``, ``data bags``, ``environments``, ``groups``, ``nodes``, or ``roles``.
#. Click the **Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. For each group listed under **Name**, select or de-select **List** and **Create** to update the global permissions list.

Set Group Permissions
=====================================================
To set the permissions list for a group:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Groups**.
#. Select a group.
#. Click the **Group Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. For each group listed under **Name**, select or de-select **List** and **Create** to update the global permissions list.

Set Node Permissions
=====================================================
.. tag manage_webui_node_permissions_set

To set permissions list for a node object:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click the **Permissions** tab.
#. For each group listed under **Name**, select or de-select the **Read**, **Update**, **Delete**, and **Grant** permissions.

.. end_tag

Set Role Permissions
=====================================================
.. tag manage_webui_policy_role_permissions_set

To set permissions list for a role object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.
#. Select a role.
#. Click the **Permissions** tab.
#. For each group listed under **Name**, select or de-select the **Read**, **Update**, **Delete**, and **Grant** permissions.

.. end_tag

Set Tag
=====================================================
To set tags for a node (or a group of nodes):

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node (or a group of nodes).
#. Click **Manage Tags**.
#. In the **Manage Node Tags** dialog box, enter the name of the tag and then select **Set Tags** from the drop-down.

   .. image:: ../images/step_manage_webui_node_tags_set.png

#. Click **Update Tags**.

Set Validation Client Permissions
=====================================================
To set permissions list for a chef-validator key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Select a chef-validator key.
#. Click the **Permissions** tab.
#. For each group listed under **Name**, select or de-select the **Delete**, **Grant**, **Read**, and/or **Update** permissions.

Switch Orgs
=====================================================
To switch organizations:

#. In the top navigation, next to **Organization**, select an organization from the drop-down list.

Update Client Permissions
=====================================================
.. tag manage_webui_policy_client_permissions_add

To update the permissions list for a client key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Select a client key.
#. Click the **Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. Select or de-select **Read**, **Update**, **Delete**, and **Grant** to update the permissions list for the user or group.

.. end_tag

Update Cookbook Permissions
=====================================================
.. tag manage_webui_policy_cookbook_permissions_add

To update the permissions list for a cookbook object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Cookbooks**.
#. Select a cookbook.
#. Click the **Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. Select or de-select **Read**, **Update**, **Delete**, and **Grant** to update the permissions list for the user or group.

.. end_tag

Update Data Bag Permissions
=====================================================
.. tag manage_webui_policy_data_bag_permissions_add

To update the permissions list for a data bag object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Data Bags**.
#. Select a data bag.
#. Click the **Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. Select or de-select **Read**, **Update**, **Delete**, and **Grant** to update the permissions list for the user or group.

.. end_tag

Update Environment Permissions
=====================================================
.. tag manage_webui_policy_environment_permissions_add

To update the permissions list for an environment object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.
#. Select an environment.
#. Click the **Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. Select or de-select **Read**, **Update**, **Delete**, and **Grant** to update the permissions list for the user or group.

.. end_tag

Update Global Permissions
=====================================================
To update the global permissions list for a Chef server object:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Global Permissions**.
#. Select the Chef server object type: ``cookbooks``, ``data bags``, ``environments``, ``groups``, ``nodes``, or ``roles``.
#. Click the **Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. Select or de-select **List** and **Create** to update the global permissions list.

Update Group Permissions
=====================================================
To update the permissions list for a group:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Groups**.
#. Select a group.
#. Click the **Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. Select or de-select **List** and **Create** to update the global permissions list.

Update Node Permissions
=====================================================
.. tag manage_webui_node_permissions_add

To update the permissions list for a node object:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click the **Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. Select or de-select **Read**, **Update**, **Delete**, and **Grant** to update the permissions list for the user or group.

.. end_tag

Update Role Permissions
=====================================================
.. tag manage_webui_policy_role_permissions_add

To update the permissions list for a role object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.
#. Select a role.
#. Click the **Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. Select or de-select **Read**, **Update**, **Delete**, and **Grant** to update the permissions list for the user or group.

.. end_tag

Update Validation Client Permissions
=====================================================
.. tag manage_webui_policy_validation_permissions_add

To update the permissions list for a chef-validator key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Select a chef-validator key.
#. Click the **Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. Select or de-select **Delete**, **Grant**, **Read**, and/or **Update** to update the permissions list for the user or group.

.. end_tag

View All Cookbook Files
=====================================================
To view cookbook files:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Cookbooks**.
#. Select a cookbook.
#. Click the **Content** tab.

View All Cookbooks
=====================================================
To view all cookbooks uploaded to the Chef server organization:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Cookbooks**.

View All Data Bags
=====================================================
To view a data bag:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Data Bags**.
#. Select a data bag.

View All Environments
=====================================================
To view all environments uploaded to the Chef server organization:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.

View All Roles
=====================================================
.. tag manage_webui_policy_roles_view

To view all roles uploaded to the Chef server organization:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.

.. end_tag

View Client Details
=====================================================
.. tag manage_webui_policy_client_view_details

To view client key details:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Select a client key.
#. Click the **Details** tab.

.. end_tag

View Client Permissions
=====================================================
.. tag manage_webui_policy_client_permissions_view

To view permissions for a client key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Select a client key.
#. Click the **Permissions** tab.
#. Set the appropriate permissions: **Delete**, **Grant**, **Read**, and/or **Update**.

.. end_tag

View Cookbook Details
=====================================================
.. tag manage_webui_policy_cookbook_view_details

To view cookbook details:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Cookbooks**.
#. Select a cookbook.
#. Click the **Details** tab:

   .. image:: ../images/step_manage_webui_policy_cookbook_view_details.png

.. end_tag

View Cookbook Permissions
=====================================================
.. tag manage_webui_policy_cookbook_permissions_view

To view permissions for a cookbook object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Cookbooks**.
#. Select a cookbook.
#. Click the **Permissions** tab.
#. Set the appropriate permissions: **Delete**, **Grant**, **Read**, and/or **Update**.

.. end_tag

View a Cookbook File
=====================================================
.. tag manage_webui_policy_cookbook_file_view

To view a cookbook file:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Cookbooks**.
#. Select a cookbook.
#. Click the **Content** tab.
#. Select the file type: **Attributes**, **Definitions**, **Files**, **Recipes**, **Templates**, or **Root Files**.
#. Select a file:

   .. image:: ../images/step_manage_webui_policy_cookbook_file_view.png

.. end_tag

View Current Run-list
=====================================================
.. tag manage_webui_node_run_list_view_current

To view the current run-list for a node:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click the **Details** tab.
#. The current run-list is shown in the lower right:

   .. image:: ../images/step_manage_webui_node_run_list_view_current.png

.. end_tag

View Data Bag Item
=====================================================
.. tag manage_webui_policy_data_bag_view_items

To view data bag items for a data bag:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Data Bags**.
#. Select a data bag.
#. Select the **Items** tab.

.. end_tag

View Data Bag Permissions
=====================================================
.. tag manage_webui_policy_data_bag_permissions_view

To view permissions for a data bag object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Data Bags**.
#. Select a data bag.
#. Click the **Permissions** tab.
#. Set the appropriate permissions: **Read**, **Update**, **Delete**, and **Grant**.

.. end_tag

View Environment Defaults
=====================================================
.. tag manage_webui_policy_environment_view_attributes_default_view

To view default attributes for an environment:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.
#. Select an environment.
#. Click the **Attributes** tab.

.. end_tag

View Environment Details
=====================================================
.. tag manage_webui_policy_environment_view_details

To view environment details:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.
#. Select an environment.
#. Click the **Details** tab.

.. end_tag

View Environment Overrides
=====================================================
.. tag manage_webui_policy_environment_view_attributes_override_view

To view override attributes for an environment:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.
#. Select an environment.
#. Click the **Attributes** tab.

.. end_tag

View Environment Permissions
=====================================================
.. tag manage_webui_policy_environment_permissions_view

To view permissions for an environment object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Environments**.
#. Select an enviromnent.
#. Click the **Permissions** tab.
#. Set the appropriate permissions: **Read**, **Update**, **Delete**, and **Grant**.

.. end_tag

View Global Permissions
=====================================================
To view global permissions:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Global Permissions**.
#. Select the Chef server object type: ``cookbooks``, ``data bags``, ``environments``, ``groups``, ``nodes``, or ``roles``.
#. Click the **Permissions** tab.
#. Click the **+ Add** button and enter the name of the user or group to be added.
#. Select or de-select **List** and **Create** to update the global permissions list.

View Group Details
=====================================================
To view group details:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Groups**.
#. Select a group.
#. Click the **Details** tab.

View Group Permissions
=====================================================
To view group permissions:

#. Open the Chef management console.
#. Click **Administration**.
#. Click **Groups**.
#. Select a group.
#. Click the **Group Permissions** tab.
#. Set the appropriate permissions: **Delete**, **Grant**, **Read**, and/or **Update**.

View Node Attributes
=====================================================
.. tag manage_webui_node_attributes

To view the attributes for a node:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click the **Attributes** tab.
#. Click **Edit**.

.. end_tag

View Node Permissions
=====================================================
.. tag manage_webui_node_permissions_view

To view permissions for a node:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Click the **Permissions** tab.
#. Set the appropriate permissions: **Delete**, **Grant**, **Read**, and/or **Update**.

.. end_tag

View Node Run-lists
=====================================================
.. tag manage_webui_nodes_view_run_list

To view all of the nodes:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Select the **Details** tab.
#. The run-list for the node appears under the **Run List** header:

   .. image:: ../images/step_manage_webui_nodes_view_run_list.png

.. end_tag

View Node Tags
=====================================================
.. tag manage_webui_nodes_view_tags

To view all of the nodes:

#. Open the Chef management console.
#. Click **Nodes**.
#. Select a node.
#. Select the **Details** tab.
#. The tags for the node appear under the **Tags** header:

   .. image:: ../images/step_manage_webui_nodes_view_tags.png

.. end_tag

View Nodes
=====================================================
To view all of the nodes:

#. Open the Chef management console.
#. Click **Nodes**.

   where:

   .. list-table::
      :widths: 60 420
      :header-rows: 1

      * - Setting
        - Description
      * - ``Node Name``
        - The name of the node.
      * - ``Platform``
        - The platform on which a node is running.
      * - ``FQDN``
        - The FQDN for the node.
      * - ``IP Address``
        - The IP address for the node.
      * - ``Uptime``
        - The amount of time the node has been running.
      * - ``Last Check-in``
        - The time of the most recent check-in by the chef-client running on that node.
      * - ``Environment``
        - The environment to which the node is associated.
      * - ``Actions``
        - The **Chef Manage** web user interface tasks available for this node.

View Role Defaults
=====================================================
.. tag manage_webui_policy_role_view_attributes_default_view

To view default attributes for a role:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.
#. Select a role.
#. Click the **Attributes** tab.

.. end_tag

View Role Details
=====================================================
.. tag manage_webui_policy_role_view_details

To view role details:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.
#. Select a role.
#. Click the **Details** tab.

.. end_tag

View Role Overrides
=====================================================
To view override attributes for a role:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.
#. Select a role.
#. Click the **Attributes** tab.

View Role Permissions
=====================================================
.. tag manage_webui_policy_role_permissions_view

To view permissions for a role object:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Roles**.
#. Select a role.
#. Click the **Permissions** tab.
#. Set the appropriate permissions: **Delete**, **Grant**, **Read**, and/or **Update**.

.. end_tag

View User Account Details
=====================================================
.. tag manage_webui_admin_users_view_account

To view user account settings:

#. Open the Chef management console.
#. From the drop-down list next to your username, select **My Profile**.

.. end_tag

View Validation Client Details
=====================================================
.. tag manage_webui_policy_validation_view_details

To view details for a chef-validator key:

#. Open the Chef management console.
#. Click **Policy**.
#. Click **Clients**.
#. Select a chef-validator key.

   .. image:: ../images/step_manage_webui_policy_validation_view_details.png

#. Click the **Details** tab.

.. end_tag

Reporting Tasks
=====================================================
This section is an alphabetical list of tasks available when using Reporting, a premium feature of the Chef server.

Filter by Environment
-----------------------------------------------------
.. tag manage_webui_reports_history_filter_by_environment

To filter report histories by environment:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Run History**.
#. From the **Filter by environment** drop-down, select ``All Environments``, ``_default``, or any custom environment:

   .. image:: ../images/step_manage_webui_reports_history_filter_by_environment.png

.. end_tag

Filter by Status
-----------------------------------------------------
.. tag manage_webui_reports_history_filter_by_status

To filter report histories by chef-client run status:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Run History**.
#. From the **Filter by status** drop-down, select ``All``, ``Success``, ``Failure``, or ``Started``:

   .. image:: ../images/step_manage_webui_reports_history_filter_by_status.png

.. end_tag

Show Runs by Date Range
-----------------------------------------------------
.. tag manage_webui_reports_dashboard_show_runs

To show a specific set of chef-client runs:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Dashboard**.
#. Select the range for which runs will be shown: all runs that occurred in the last 3 months, the last month, the last week, the last twenty-four hours, after a specific date, or between two specific dates:

   .. image:: ../images/step_manage_webui_reports_dashboard_show_runs.png

.. end_tag

Show Runs for Org
-----------------------------------------------------
.. tag manage_webui_reports_history_show_runs

To show a specific set of chef-client run histories:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Run History**.
#. Select the range for which run histories will be shown: all runs that occurred in the last 3 months, the last month, the last week, the last twenty-four hours, after a specific date, or between two specific dates.

.. end_tag

View Dashboard
-----------------------------------------------------
.. tag manage_webui_reports_dashboard

To view the reports dashboard:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Dashboard**.

.. end_tag

View Error Log
-----------------------------------------------------
.. tag manage_webui_reports_history_view_error_log

To view chef-client run error logs:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Run History**.
#. Select the range of chef-client runs to show, the correct environment, and correct status.
#. Select a chef-client run.
#. Select the **Error Log** tab:

   .. image:: ../images/step_manage_webui_reports_history_view_error_log.png

.. end_tag

View History
-----------------------------------------------------
.. tag manage_webui_reports_history

To report histories:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Run History**.

.. end_tag

View Run Counts
-----------------------------------------------------
.. tag manage_webui_reports_dashboard_view_run_counts

To view chef-client runs still running:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Dashboard**.
#. The chef-client runs that are still running are shown under the **Run Counts** header:

   .. image:: ../images/step_manage_webui_reports_dashboard_view_run_counts.png

   Select (or de-select) ``success``, ``failure``, and ``aborted`` to filter the view to only specific run outcomes:

   .. image:: ../images/step_manage_webui_reports_dashboard_view_dashboard_common_outcomes.png

.. end_tag

View Run Details
-----------------------------------------------------
.. tag manage_webui_reports_history_view_details

To view chef-client details:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Run History**.
#. Select the range of chef-client runs to show, the correct environment, and correct status.
#. Select a chef-client run.
#. Select the **Details** tab:

   .. image:: ../images/step_manage_webui_reports_history_view_details.png

   where:

   .. list-table::
      :widths: 60 420
      :header-rows: 1

      * - Setting
        - Description
      * - ``Step``
        - The order in which resources were executed during the chef-client run.
      * - ``Type``
        - The type of resource. https://docs.chef.io/resource.html#resources
      * - ``Name``
        - A string that describes the action taken. For example, a log entry or the name of the service that is enabled.
      * - ``Action``
        - The action taken by the resource type.
      * - ``Duration``
        - The amount of time required to complete the action.
      * - ``Diff``
        - The difference between the current state and the previous state. This setting is available for files managed by the **cookbook_file**, **file**, **remote_file**, and **template** resources.
      * - ``Parameters``
        - Opens the **Run Details** dialog box, which lists all of the parameters on the node that were changed during the chef-client run.

.. end_tag

View Run Durations
-----------------------------------------------------
.. tag manage_webui_reports_dashboard_view_run_durations

To view chef-client runs with errors:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Dashboard**.
#. The chef-client runs with errors are shown under the **Run Durations** header:

   .. image:: ../images/step_manage_webui_reports_dashboard_view_run_durations.png

   Hover over duration values to see the number of associated runs:

   .. image:: ../images/step_manage_webui_reports_dashboard_view_run_durations_hover.png

   Select (or de-select) ``success``, ``failure``, and ``aborted`` to filter the view to only specific run outcomes:

   .. image:: ../images/step_manage_webui_reports_dashboard_view_dashboard_common_outcomes.png

.. end_tag

View Run-specific Details
-----------------------------------------------------
.. tag manage_webui_reports_history_view_details_run_details

To view chef-client run-specific details:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Run History**.
#. Select the range of chef-client runs to show, the correct environment, and correct status.
#. Select a chef-client run.
#. Select the **Details** tab.
#. For a specific step, from the **Parameters** column, click the view icon to open the **Run Details** dialog box:

   .. image:: ../images/step_manage_webui_reports_history_view_details_run_details.png

   where:

   .. list-table::
      :widths: 60 420
      :header-rows: 1

      * - Setting
        - Description
      * - ``Parameters``
        - The parameters that were set by the resource during the chef-client run.
      * - ``Initial State``
        - The state of the parameter at the start of the chef-client run.
      * - ``Final State``
        - The state of the parameter at the end of the chef-client run.

.. end_tag

View Run-list
-----------------------------------------------------
.. tag manage_webui_reports_history_view_run_list

To view chef-client run-list details:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Run History**.
#. Select the range of chef-client runs to show, the correct environment, and correct status.
#. Select a chef-client run.
#. Select the **Run List** tab:

   .. image:: ../images/step_manage_webui_reports_history_view_run_list.png

.. end_tag

View Runs Summary
-----------------------------------------------------
.. tag manage_webui_reports_dashboard_view_run_summary

To view the chef-client runs summary:

#. Open the Chef management console.
#. Click **Reports**.
#. Click **Dashboard**.
#. The chef-client runs summaries are shown under the **Runs Summary** header:

   .. image:: ../images/step_manage_webui_reports_dashboard_view_run_summary.png

.. end_tag

