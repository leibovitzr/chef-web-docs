.. THIS PAGE DOCUMENTS chef-client version 12.1

=====================================================
powershell_script
=====================================================

.. include:: ../../includes_resources/includes_resource_powershell_script.rst

Syntax
=====================================================
.. include:: ../../includes_resources/includes_resource_powershell_script_syntax.rst

Actions
=====================================================
.. include:: ../../includes_resources/includes_resource_powershell_script_actions.rst

Properties
=====================================================
.. include:: ../../includes_resources/includes_resource_powershell_script_attributes_12-5.rst

Guards
-----------------------------------------------------
.. include:: ../../includes_resources_common/includes_resources_common_guards.rst

**Attributes**

.. include:: ../../includes_resources_common/includes_resources_common_guards_attributes.rst

**Arguments**

.. include:: ../../includes_resources_common/includes_resources_common_guards_arguments.rst

.. 
.. Providers
.. =====================================================
.. .. include:: ../../includes_resources_common/includes_resources_common_provider.rst
.. 
.. .. include:: ../../includes_resources_common/includes_resources_common_provider_attributes.rst
.. 
.. .. include:: ../../includes_resources/includes_resource_powershell_script_providers.rst
.. 

Examples
=====================================================
|generic resource statement|

**Write to an interpolated path**

.. include:: ../../step_resource/step_resource_powershell_write_to_interpolated_path.rst

**Change the working directory**

.. include:: ../../step_resource/step_resource_powershell_cwd.rst

**Change the working directory in Microsoft Windows**

.. include:: ../../step_resource/step_resource_powershell_cwd_microsoft_env.rst

**Pass an environment variable to a script**

.. include:: ../../step_resource/step_resource_powershell_pass_env_to_script.rst

**Evaluate for true and/or false**

.. include:: ../../step_resource/step_resource_powershell_convert_boolean_return.rst

**Use the flags attribute**

.. include:: ../../step_resource/step_resource_powershell_script_use_flag.rst

**Rename computer, join domain, reboot**

.. include:: ../../step_resource/step_resource_powershell_rename_join_reboot.rst
