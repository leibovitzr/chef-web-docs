.. The contents of this file may be included in multiple topics (using the includes directive).
.. The contents of this file should be modified in a way that preserves its ability to appear in multiple topics.

The ``processes`` matcher tests if the named process is running on the system:

.. code-block:: ruby

   its('processes') { should eq ['syslog'] }
