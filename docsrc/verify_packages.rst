=====================================================
Verify Signed Packages
=====================================================

Signed packages that are built by Chef may be verified using the steps described below.

RPMs
=====================================================

A Chef package built for RPM Package Manager can be verified using the key located at http://downloads.chef.io/chef.gpg.key.

To verify any Chef package built for RPM:

#. Import the key

   .. code-block:: bash

      $ rpm --import http://downloads.chef.io/chef.gpg.key

#. Verify the signature. For example, the Chef development kit:

   .. code-block:: bash

      $ rpm -K chefdk-0.2.2-1.x86_64.rpm

   which will return something similar to:

   .. code-block:: bash

      $ chefdk-0.2.2-1.x86_64.rpm: (sha1) dsa sha1 md5 gpg OK
