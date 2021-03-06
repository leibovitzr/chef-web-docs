.. The contents of this file may be included in multiple topics (using the includes directive).
.. The contents of this file should be modified in a way that preserves its ability to appear in multiple topics.

This resource has the following properties:
   
``code``
   **Ruby Type:** String

   |code quoted_string|
   
``creates``
   **Ruby Type:** String

   |creates file_exists|
   
``cwd``
   **Ruby Type:** String

   |cwd|
   
``environment``
   **Ruby Type:** Hash

   |environment variables|
   
``flags``
   **Ruby Type:** String

   |flags|
   
``group``
   **Ruby Types:** String, Integer

   |group command|
   
``ignore_failure``
   **Ruby Types:** TrueClass, FalseClass

   |ignore_failure| Default value: ``false``.
   
``notifies``
   **Ruby Type:** Symbol, 'Chef::Resource[String]'

   .. include:: ../../includes_resources_common/includes_resources_common_notification_notifies.rst

   .. include:: ../../includes_resources_common/includes_resources_common_notification_timers.rst

   .. include:: ../../includes_resources_common/includes_resources_common_notification_notifies_syntax.rst
   
``path``
   **Ruby Type:** Array

   |path resource execute| The default value uses the system path.

   .. warning:: .. include:: ../../includes_resources_common/includes_resources_common_resource_execute_attribute_path.rst

      For example:

      .. code-block:: ruby

         csh 'mycommand' do
           environment 'PATH' => "/my/path/to/bin:#{ENV['PATH']}"
         end

``provider``
   **Ruby Type:** Chef Class

   Optional. |provider resource_parameter| |see providers|
   
``retries``
   **Ruby Type:** Integer

   |retries| Default value: ``0``.
   
``retry_delay``
   **Ruby Type:** Integer

   |retry_delay| Default value: ``2``.
   
``returns``
   **Ruby Types:** Integer, Array

   |return_value cmd| Default value: ``0``.
   
``subscribes``
   **Ruby Type:** Symbol, 'Chef::Resource[String]'

   .. include:: ../../includes_resources_common/includes_resources_common_notification_subscribes.rst

   .. include:: ../../includes_resources_common/includes_resources_common_notification_timers.rst

   .. include:: ../../includes_resources_common/includes_resources_common_notification_subscribes_syntax.rst
   
``timeout``
   **Ruby Types:** Integer, Float

   |timeout command| Default value: ``3600``.
   
``user``
   **Ruby Types:** String, Integer

   |user command|
   
``umask``
   **Ruby Types:** String, Integer

   |umask|
