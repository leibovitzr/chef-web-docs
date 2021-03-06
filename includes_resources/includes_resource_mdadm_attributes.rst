.. The contents of this file may be included in multiple topics (using the includes directive).
.. The contents of this file should be modified in a way that preserves its ability to appear in multiple topics.

This resource has the following properties:
   
``bitmap``
   **Ruby Type:** String

   |path bitmap|

``chunk``
   **Ruby Type:** Integer

   |chunk_size| This property should not be used for a RAID 1 mirrored pair (i.e. when the ``level`` property is set to ``1``). Default value: ``16``.

``devices``
   **Ruby Type:** Array

   |device mdadm| Default value: ``[]``.

``exists``
   **Ruby Types:** TrueClass, FalseClass

   |raid_device exists| Default value: ``false``.

``ignore_failure``
   **Ruby Types:** TrueClass, FalseClass

   |ignore_failure| Default value: ``false``.

``layout``
   **Ruby Type:** String

   The |raid5| parity algorithm. Possible values: ``left-asymmetric`` (or ``la``), ``left-symmetric`` (or ``ls``), ``right-asymmetric`` (or ``ra``), or ``right-symmetric`` (or ``rs``).

``level``
   **Ruby Type:** Integer

   |level mdadm| Default value: ``1``.

``mdadm_defaults``
   **Ruby Types:** TrueClass, FalseClass

   |mdadm_defaults| Default value: ``false``.  

``metadata``
   **Ruby Type:** String

   |raid_device superblock_type| Default value: ``0.90``.

``notifies``
   **Ruby Type:** Symbol, 'Chef::Resource[String]'

   .. include:: ../../includes_resources_common/includes_resources_common_notification_notifies.rst

   .. include:: ../../includes_resources_common/includes_resources_common_notification_timers.rst

   .. include:: ../../includes_resources_common/includes_resources_common_notification_notifies_syntax.rst

``provider``
   **Ruby Type:** Chef Class

   Optional. |provider resource_parameter|

``raid_device``
   **Ruby Type:** String

   |raid_device mdadm| |resource_block_default| |see syntax|

``retries``
   **Ruby Type:** Integer

   |retries| Default value: ``0``.

``retry_delay``
   **Ruby Type:** Integer

   |retry_delay| Default value: ``2``.

``subscribes``
   **Ruby Type:** Symbol, 'Chef::Resource[String]'

   .. include:: ../../includes_resources_common/includes_resources_common_notification_subscribes.rst

   .. include:: ../../includes_resources_common/includes_resources_common_notification_timers.rst

   .. include:: ../../includes_resources_common/includes_resources_common_notification_subscribes_syntax.rst
