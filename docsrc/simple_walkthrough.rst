=====================================================
Simple Walkthrough
=====================================================

The Chef development kit is a package that contains everything you need to start using Chef, along with a collection of tools and libaries that can help improve the code you are using to run your business.

Install the Chef DK
=====================================================
.. tag install_chef_dk

To install the Chef development kit:

#. Visit this page: http://downloads.chef.io/chef-dk/. The Chef development kit supports Mac OS X, Red Hat Enterprise Linux, Ubuntu, and Microsoft Windows.
#. Select a platform, and then a package. (chef-docs uses the Mac OS X setup within the documentation.)
#. Click the download button.
#. Follow the steps in the installer and install the Chef development kit to your machine. The Chef development kit is installed to ``/opt/chefdk/`` on UNIX and Linux systems. 
#. When finished, open a command window and enter the following:

   .. code-block:: bash

      $ chef verify

   This will verify the main components of the Chef development kit: the chef-client, the Chef development kit library, and the tools that are built into the Chef development kit. The output should be similar to:

   .. code-block:: bash

      Running verification for component '...'
      ..........
      ---------------------------------------------
      Verification of component '...' succeeded.

#. Optional. Set the default shell. On Microsoft Windows it is strongly recommended to use Windows PowerShell and cmd.exe.

.. end_tag

.. 
.. What's in the Chef DK?
.. -----------------------------------------------------
.. .. include:: ../includes_chef_dk/includes_chef_dk_tools.rst
.. 
.. .. include:: ../includes_chef_dk/includes_chef_dk_tools_main.rst
..

Set the System Ruby
=====================================================
.. tag ruby_set_system_ruby_as_chefdk_ruby

For many users of Chef, the Chef development kit version of Ruby that is included in the Chef development kit should be configured as the default version of Ruby.

#. Open a command window and enter the following:

   .. code-block:: bash

      $ which ruby

   which will return something like ``/usr/bin/ruby``.
#. To use the Chef development kit version of Ruby as the default Ruby, edit the ``$PATH`` and ``GEM`` environment variables to include paths to the Chef development kit. For example, on a machine that runs Bash, run:

   .. code-block:: bash

      echo 'eval "$(chef shell-init bash)"' >> ~/.bash_profile

   where ``bash`` and ``~/.bash_profile`` represents the name of the shell.

   If zsh is your preferred shell then run the following:

   .. code-block:: bash

    echo 'eval "$(chef shell-init zsh)"' >> ~/.zshrc

#. Run ``which ruby`` again. It should return ``/opt/chefdk/embedded/bin/ruby``.

.. note:: Using the Chef development kit-provided Ruby as your system Ruby is optional. This just depends on how you are using Ruby on your system. For many users, Ruby is primarily used for authoring Chef cookbooks and recipes. If that's true for you, then using the Chef development kit-provided Ruby as your system Ruby is recommended. But for other users who are already using tools like rbenv to manage Ruby versions, then that's OK too.

.. end_tag

.. note:: You may need to restart your shell for this change to be visible.

Your First Cookbook
=====================================================
We have already used the chef ``verify`` subcommand to verify the installation of the Chef development kit. Now let's use the chef ``generate`` subcommand to create the chef-repo, which is the main folder in which your Chef code will be stored. Run the following command:

.. code-block:: bash

   $ chef generate app name

where ``name`` is a name that you have chosen for the both the chef-repo and the default cookbook. We are calling ours ``chef-repo``; you can call yours whatever you want. You should have a directory structure at ``/Users/your_username/cookbook_name/`` similar to::

   /chef-repo
     /.git
     .gitignore
     .kitchen.yml
     /cookbooks
       /chef-repo
         Berksfile
         chefignore
         metadata.rb
         /recipes
           default.rb
     README.md

Update Default Recipe
=====================================================
Open the ``default.rb`` recipe in the cookbook you just created. Add the following resource to that recipe:

.. code-block:: ruby

   file "#{ENV['HOME']}/test.txt" do
     content 'This file created by Chef!'
   end

This recipe creates a file called ``test.txt`` at the path defined by the ``HOME`` environment variable. (To view that path, run ``echo "$HOME"`` in the command shell.)

Run the chef-client
=====================================================
Next, we'll run the chef-client. This is done via the command line and the command must be run from within the chef-repo.

* Use the ``--local-mode`` flag to run the chef-client locally on your machine exactly the same as if the chef-client were able to communicate with a Chef server. Local mode does not require a connection to a Chef server, public or private keys, or configuring of nodes. Many people use local mode for simple, local testing of recipes and cookbooks, often as a pre-cursor to running unit and integration tests against the same recipes and cookbooks.
* Use the ``--override-runlist`` flag to run only the recipe we have just created. (More about the run-list later.)

To run a cookbook's default recipe, only the name of the cookbook needs to be specified because the name of the cookbook is directly associated with the default recipe.

The following command will create the file ``test.txt``:

.. code-block:: bash

   $ chef-client --local-mode --override-runlist chef-repo

where ``chef-repo`` is the name of your cookbook.

As the chef-client adds the file to your system, output similar to the following is shown:

.. code-block:: bash

   Starting Chef Client, version 11.14.0.alpha.1
   [2014-06-13T16:13:10-07:00] WARN: No config file found or specified on command line, using command line options.
   [2014-06-13T16:13:11-07:00] WARN: SSL validation of HTTPS requests is disabled. 
   [2014-06-13T16:13:13-07:00] WARN: Run List override has been provided.
   [2014-06-13T16:13:13-07:00] WARN: Original Run List: []
   [2014-06-13T16:13:13-07:00] WARN: Overridden Run List: [recipe[chef-repo]]
   resolving cookbooks for run list: ["chef-repo"]
   Synchronizing Cookbooks:
     - chef-repo
   Compiling Cookbooks...
   Converging 1 resources
   Recipe: chef-repo::default
     * file[/Users/grantmc/test.txt] action create
       - create new file /Users/grantmc/test.txt
       - update content in file /Users/grantmc/test.txt from none to d9c88f
           --- /Users/grantmc/test.txt	2014-06-13 16:13:13.000000000 -0700
           +++ /var/folders/l0/6xjyqtvn60zdt7jk6n07wz2m0000gp/T/.test.txt20140613-9526-179gcje	2014-06-13 16:13:13.000000000 -0700
           @@ -1 +1,2 @@
           +This file created by Chef!

   [2014-06-13T16:13:13-07:00] WARN: Skipping final node save because override_runlist was given

   Running handlers:
   Running handlers complete

   Chef Client finished, 1/1 resources updated in 2.418878 seconds

That's it. The warnings, for the moment, can be ignored. Check the root of the path defined by the ``HOME`` environment variable and find the file named ``test.txt``. The file should contain ``This file created by Chef!``. Open that file, edit the string, and then save that file. Re-run the chef-client. Or delete the file. In both cases, re-run the chef-client. Chef will return the system to the state that is defined by the recipe.

We'll come back to working with Chef later on. Let's set up Kitchen so that we can use it to build a virtual machine against which we can run Chef.

Kitchen Setup
=====================================================
.. tag test_kitchen

Use `Kitchen <http://kitchen.ci>`_  to automatically test cookbook data across any combination of platforms and test suites:

* Defined in a .kitchen.yml file
* Uses a driver plugin architecture
* Supports cookbook testing across many cloud providers and virtualization technologies
* Supports all common testing frameworks that are used by the Ruby community
* Uses a comprehensive set of base images provided by `Bento <https://github.com/chef/bento>`_

.. end_tag

You will need some type of virtualization software for Kitchen. Vagrant is the default driver for Kitchen. Install Vagrant. Vagrant requires VirtualBox, so install VirtualBox. Once you're ready, we'll keep using the same cookbook created earlier.

Update Metadata
-----------------------------------------------------
In that cookbok, let's update the metadata. Open the ``metadata.rb`` file. It will look similar to:

.. code-block:: ruby

   name             ''
   maintainer       ''
   maintainer_email ''
   license          ''
   description      'Installs/Configures '
   long_description 'Installs/Configures '
   version          '0.1.0'

for now, let's just update the name and version settings, like this:

.. code-block:: ruby

   name 'chef-repo'
   maintainer 'docs'
   maintainer_email 'docs@chef.io'
   license 'Apache License, Version 2.0'
   description 'example metadata.rb'
   long_description 'This is an example metadata.rb file used in docs.chef.io.'
   version '0.1.0'

Verify .kitchen.yml
-----------------------------------------------------
Because Kitchen is installed as part of the Chef development kit, the .kitchen.yml file is already created:

.. code-block:: yaml

   ---
   driver:
     name: vagrant

   provisioner:
     name: chef_zero

   platforms:
     - name: ubuntu-14.04
     - name: centos-7.1

   suites:
     - name: default
       run_list:
         - recipe[chef-repo::default]
       attributes:

Verify that the default provisioner is chef-zero:

.. code-block:: yaml

   ...

   provisioner:
     name: chef_zero

   ...

Verify that the default recipe contains the name of the cookbook that was generated earlier:

.. code-block:: yaml

   suites:
     - name: default
       run_list:
         - recipe[chef-repo::default]
       attributes:

where ``chef-repo`` is the name of your cookbook.

This is all of the configuration Kitchen needs at this time. Let's set up some Kitchen instances, and then build virtual machines that can run Chef.

View Instance List
-----------------------------------------------------
From the chef-repo, run the following command to verify the list of Kitchen instances:

.. code-block:: bash

   $ kitchen list

to return a list similar to:

.. code-block:: bash

   Instance             Driver   Provisioner  Verifier  Transport  Last Action
   default-ubuntu-1404  Vagrant  ChefZero     Busser    Ssh        <Not Created>
   default-centos-71    Vagrant  ChefZero     Busser    Ssh        <Not Created>

There are two available default platforms---Ubuntu 12.04 and CentOS 6.5---that are pre-configured to use the Vagrant driver that is included with the Chef development kit.

Create CentOS Instance
-----------------------------------------------------
.. tag ctl_kitchen_create_centos_default

To create the default CentOS instance, run the following:

.. code-block:: bash

   $ kitchen create default-centos-71

CentOS is downloaded the first time this command is run, after which Vagrant is started. (This may take a few minutes.)

The output of the command is similar to:

.. code-block:: bash

   -----> Starting Kitchen (v1.4.2)
   -----> Creating <default-centos-71>...
          Bringing machine 'default' up with 'virtualbox' provider...
          ==> default: Box 'opscode-centos-6.5' could not be found. Attempting to find and install...
              default: Box Provider: virtualbox
              default: Box Version: >= 0
          ==> default: Adding box 'opscode-centos-6.5' (v0) for provider: virtualbox
              default: Downloading: https://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.5_chef-provisionerless.box
          ==> default: Successfully added box 'opscode-centos-6.5' (v0) for 'virtualbox'!
          ==> default: Importing base box 'opscode-centos-6.5'...
          ==> default: Matching MAC address for NAT networking...
          ==> default: Setting the name of the VM: default-centos-71_default_1403650129063_53517
          ==> default: Clearing any previously set network interfaces...
          ==> default: Preparing network interfaces based on configuration...
              default: Adapter 1: nat
          ==> default: Forwarding ports...
              default: 22 => 2222 (adapter 1)
          ==> default: Booting VM...
          ==> default: Waiting for machine to boot. This may take a few minutes...
              default: SSH address: 127.0.0.1:2222
              default: SSH username: vagrant
              default: SSH auth method: private key
              default: Warning: Connection timeout. Retrying...
          ==> default: Machine booted and ready!
          ==> default: Checking for guest additions in VM...
          ==> default: Setting hostname...
          ==> default: Machine not provisioning because `--no-provision` is specified.
          Vagrant instance <default-centos-71> created.
          Finished creating <default-centos-71> (4m0.59s).
   -----> Kitchen is finished. (11m29.76s)

.. end_tag

From the chef-repo, run the following command to verify the list of Kitchen instances:

.. code-block:: bash

   $ kitchen list

to return a list similar to:

.. code-block:: bash

   Instance             Driver   Provisioner  Verifier  Transport  Last Action
   default-ubuntu-1404  Vagrant  ChefZero     Busser    Ssh        <Not Created>
   default-centos-71    Vagrant  ChefZero     Busser    Ssh        Created

Create Ubuntu Instance
-----------------------------------------------------
.. tag ctl_kitchen_create_ubuntu_default

To create the default Ubuntu instance, run the following:

.. code-block:: bash

   $ kitchen create default-ubuntu-1404

Ubuntu is downloaded the first time this command is run, after which Vagrant is started. (This may take a few minutes.)

The output of the command is similar to:

.. code-block:: bash

   -----> Starting Kitchen (v1.4.2)
   -----> Creating <default-ubuntu-1404>...
          Bringing machine 'default' up with 'virtualbox' provider...
          ==> default: Box 'opscode-ubuntu-12.04' could not be found. Attempting to find and install...
              default: Box Provider: virtualbox
              default: Box Version: >= 0
          ==> default: Adding box 'opscode-ubuntu-12.04' (v0) for provider: virtualbox
              default: Downloading: https://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_ubuntu-12.04_chef-provisionerless.box
          ==> default: Successfully added box 'opscode-ubuntu-12.04' (v0) for 'virtualbox'!
          ==> default: Importing base box 'opscode-ubuntu-12.04'...
          ==> default: Matching MAC address for NAT networking...
          ==> default: Setting the name of the VM: default-ubuntu-1404_default_1403651715173_54200
          ==> default: Fixed port collision for 22 => 2222. Now on port 2200.
          ==> default: Clearing any previously set network interfaces...
          ==> default: Preparing network interfaces based on configuration...
              default: Adapter 1: nat
          ==> default: Forwarding ports...
              default: 22 => 2200 (adapter 1)
          ==> default: Booting VM...
   ==> default: Waiting for machine to boot. This may take a few minutes...
              default: SSH username: vagrant
              default: SSH auth method: private key
              default: Warning: Connection timeout. Retrying...
          ==> default: Machine booted and ready!
          ==> default: Checking for guest additions in VM...
          ==> default: Setting hostname...
          ==> default: Machine not provisioning because `--no-provision` is specified.
          Vagrant instance <default-ubuntu-1404> created.
          Finished creating <default-ubuntu-1404> (4m1.59s).
   -----> Kitchen is finished. (10m58.24s)

.. end_tag

From the chef-repo, run the following command to verify the list of Kitchen instances:

.. code-block:: bash

   $ kitchen list

to return a list similar to:

.. code-block:: bash

   Instance             Driver   Provisioner  Verifier  Transport  Last Action
   default-ubuntu-1404  Vagrant  ChefZero     Busser    Ssh        Created
   default-centos-71    Vagrant  ChefZero     Busser    Ssh        Created

Now we're all set up! We're going to use the same recipe and cookbook that we already created.

Converge CentOS
-----------------------------------------------------
.. tag ctl_kitchen_converge_centos_default

To converge the default CentOS instance, run the following:

.. code-block:: bash

   $ kitchen converge default-centos-71

The chef-client is downloaded the first time this command is run. The output of the command is similar to:

.. code-block:: bash

   -----> Starting Kitchen (v1.4.2)
   -----> Converging <default-centos-71>...
          Preparing files for transfer
          Preparing cookbooks from project directory
          Removing non-cookbook files before transfer
          Preparing nodes
   -----> Installing Chef Omnibus (true)
          downloading https://www.chef.io/chef/install.sh
            to file /tmp/install.sh
          ...
          Downloading Chef ...
          Installing Chef ...
          Thank you for installing Chef!
          Transferring files to <default-centos-71>
          [2014-06-27T18:41:04+00:00] INFO: Forking chef instance to converge...
          Starting Chef Client, version 12.4.1
          [2014-06-27T18:45:18+00:00] INFO: *** Chef 12.4.1 ***
          [2014-06-27T18:45:18+00:00] INFO: Chef-client pid: 3226
          [2014-06-27T18:45:25+00:00] INFO: Setting the run_list to ["recipe[chef-repo::default]"] from CLI options
          [2014-06-27T18:45:25+00:00] INFO: Run List is [recipe[chef-repo::default]]
          [2014-06-27T18:45:25+00:00] INFO: Run List expands to [chef-repo::default]
          [2014-06-27T18:45:25+00:00] INFO: Starting Chef Run for default-centos-71
          [2014-06-27T18:45:25+00:00] INFO: Running start handlers
          [2014-06-27T18:42:40+00:00] INFO: Start handlers complete.
          Compiling Cookbooks...
          Converging 1 resources
          Recipe: chef-repo::default
            * file[/root/test.txt] action create... INFO: Processing file[/root/test.txt] 
              action create (chef-repo::default line 10)
          [2014-06-27T18:42:40+00:00] INFO: file[/root/test.txt] created file /root/test.txt
            - create new file /root/test.txt... INFO: file[/root/test.txt] updated file contents /root/test.txt
            - update content in file /root/test.txt from none to d9c88f
          --- /root/test.txt	2014-06-27 18:42:40.695889276 +0000
          +++ /tmp/.test.txt20140627-2810-1xdx98p	2014-06-27 18:42:40.695889276 +0000
          @@ -1 +1,2 @@
          +This file created by Chef!
            - restore selinux security context
          [2014-06-27T18:42:40+00:00] INFO: Chef Run complete in 0.168252291 seconds
          Running handlers:
          [2014-06-27T18:42:40+00:00] INFO: Running report handlers
          Running handlers complete
          [2014-06-27T18:42:40+00:00] INFO: Report handlers complete
          Chef Client finished, 1/1 resources updated in 7.152725504 seconds
          Finished converging <default-centos-71> (0m8.43s).
   -----> Kitchen is finished. (0m15.96s)

.. end_tag

Converge Ubuntu
-----------------------------------------------------
.. tag ctl_kitchen_converge_ubuntu_default

To converge the default Ubuntu instance, run the following:

.. code-block:: bash

   $ kitchen converge default-ubuntu-1404

The chef-client is downloaded the first time this command is run. The output of the command is similar to:

.. code-block:: bash

   -----> Starting Kitchen (v1.4.2)
   -----> Converging <default-ubuntu-1404>...
          Preparing files for transfer
          Preparing cookbooks from project directory
          Removing non-cookbook files before transfer
          Preparing nodes
   -----> Installing Chef Omnibus (true)
          downloading https://www.chef.io/chef/install.sh
            to file /tmp/install.sh
          ...
          Downloading Chef ...
          Installing Chef ...    
          Thank you for installing Chef!       
          Transferring files to <default-ubuntu-1404>
          [2014-06-27T18:48:01+00:00] INFO: Forking chef instance to converge...       
          Starting Chef Client, version 12.4.1       
          [2014-06-27T18:48:01+00:00] INFO: *** Chef 12.4.1 ***       
          [2014-06-27T18:48:01+00:00] INFO: Chef-client pid: 1246       
          [2014-06-27T18:48:03+00:00] INFO: Setting the run_list to ["recipe[chef-repo::default]"] from CLI options       
          [2014-06-27T18:48:03+00:00] INFO: Run List is [recipe[chef-repo::default]]       
          [2014-06-27T18:48:03+00:00] INFO: Run List expands to [chef-repo::default]       
          [2014-06-27T18:48:03+00:00] INFO: Starting Chef Run for default-ubuntu-1404       
          [2014-06-27T18:48:03+00:00] INFO: Running start handlers       
          [2014-06-27T18:48:03+00:00] INFO: Start handlers complete.       
          Compiling Cookbooks...       
          Converging 1 resources       
          Recipe: chef-repo::default       
            * file[/home/vagrant/test.txt] action create... INFO: Processing file[/home/vagrant/test.txt] 
              action create (chef-repo::default line 10)       
          [2014-06-27T18:48:03+00:00] INFO: file[/home/vagrant/test.txt] created file /home/vagrant/test.txt       
            - create new file /home/vagrant/test.txt... INFO: file[/home/vagrant/test.txt] updated file contents /home/vagrant/test.txt       
            - update content in file /home/vagrant/test.txt from none to d9c88f       
          --- /home/vagrant/test.txt	2014-06-27 18:48:03.233096345 +0000       
           +++ /tmp/.test.txt20140627-1246-178u9dg	2014-06-27 18:48:03.233096345 +0000       
          @@ -1 +1,2 @@       
          +This file created by Chef!       
          [2014-06-27T18:48:03+00:00] INFO: Chef Run complete in 0.015439954 seconds       
          Running handlers:       
          [2014-06-27T18:48:03+00:00] INFO: Running report handlers       
          Running handlers complete       
          [2014-06-27T18:48:03+00:00] INFO: Report handlers complete       
          Chef Client finished, 1/1 resources updated in 1.955915841 seconds       
          Finished converging <default-ubuntu-1404> (0m15.67s).
   -----> Kitchen is finished. (0m15.96s)

.. end_tag

Verify Instance List
-----------------------------------------------------
To verify if both instances have been converged, run the following command:

.. code-block:: bash

   $ kitchen list

.. code-block:: bash

   Instance             Driver   Provisioner  Verifier  Transport  Last Action
   default-ubuntu-1404  Vagrant  ChefZero     Busser    Ssh        Converged
   default-centos-71    Vagrant  ChefZero     Busser    Ssh        Converged

Now you can run your cookbooks in a virtual instance managed by Kitchen on multiple platforms (Ubuntu and CentOS).

Configure NTP
=====================================================
Instead of putting a text file on these Kitchen instances, let's try something more useful and install Network Time Protocol (NTP). Within the cookbook we're already using, let's update the default recipe to install and configure Network Time Protocol (NTP) using the **package**, **template**, and **service** resources, a template file, and an attributes file.

Add Template
-----------------------------------------------------
The **template** resource looks for templates in a cookbook's ``/templates`` directory. Template files in this directory must be Embedded Ruby (ERB) files. The chef has an argument that will handle most of this process for you. Let's create that directory and the template file we'll use to configure Network Time Protocol (NTP) using this command. Let's use the same cookbook we've been using. From within that cookbook repo, run the following command:

.. code-block:: bash

   $ chef generate template ntp.conf

which will return something similar to:

.. code-block:: bash

   Compiling Cookbooks...
     Recipe: code_generator::template
       * directory[/Users/grantmc/chef-repo/cookbooks/chef-repo/templates/default] action create
         - create new directory /Users/grantmc/chef-repo/cookbooks/chef-repo/templates/default
       * template[/Users/grantmc/chef-repo/cookbooks/chef-repo/templates/default/ntp.conf.erb] action create
         - create new file /Users/grantmc/chef-repo/cookbooks/chef-repo/templates/default/ntp.conf.erb
         - update content in file /Users/grantmc/chef-repo/cookbooks/chef-repo/templates/default/ntp.conf.erb from none to e3b0c4

and a directory structure in that cookbook similar to::

   /chef-repo
     /.git
	 .gitignore
     .kitchen.yml
     /cookbooks
       /chefdocs
         Berksfile
         chefignore
         metadata.rb
         /recipes
           default.rb
		 /templates
		   /default
		     ntp.conf.erb
     README.md

and an empty ``ntp.conf.erb`` file. Let's edit this file and define its contents. Open this file and add the following:

.. code-block:: ruby

   restrict default kod nomodify notrap nopeer noquery
   restrict -6 default kod nomodify notrap nopeer noquery
   restrict 127.0.0.1
   restrict -6 ::1
   server <%= @ntp_server %>
   server  127.127.1.0     # local clock
   driftfile /var/lib/ntp/drift
   keys /etc/ntp/keys

Add Attributes
-----------------------------------------------------
The name of the init script that is used to run Network Time Protocol (NTP) is ``ntp`` on Debian-based platforms (such as Ubuntu) and is ``ntpd`` on Red Hat Enterprise Linux-based platforms. Let's use an attribute in our cookbook to tell the chef-client what to do on both platforms using a single cookbook attribute. Like for templates, the chef has an argument that will handle most of this process for you. Let's create that directory and the default attribute file we'll use to tell the chef-client how to handle the attribute. Let's use the same cookbook we've been using. From within that cookbook repo, run the following command:

.. code-block:: bash

   $ chef generate attribute default

which will return something similar to:

.. code-block:: bash

   Compiling Cookbooks...
     Recipe: code_generator::attribute
       * directory[/Users/grantmc/chef-repo/cookbooks/chef-repo/attributes] action create
         - create new directory /Users/grantmc/chef-repo/cookbooks/chef-repo/attributes
       * template[/Users/grantmc/chef-repo/cookbooks/chef-repo/attributes/default.rb] action create
         - create new file /Users/grantmc/chef-repo/cookbooks/chef-repo/attributes/default.rb
         - update content in file /Users/grantmc/chef-repo/cookbooks/chef-repo/attributes/default.rb from none to e3b0c4

and a directory structure in that cookbook similar to::

   /chef-repo
     /.git
	 .gitignore
     .kitchen.yml
     /cookbooks
       /chefdocs
	     /attributes
		   default.rb
         Berksfile
         chefignore
         metadata.rb
         /recipes
           default.rb
		 /templates
		   /default
		     ntp.conf.erb
     README.md

and an empty ``default.rb`` file under ``/attributes``. Let's edit this file and define its contents. Open this file and add the following:

.. code-block:: ruby

   default[:ntp][:service] =
     case platform_family
       when 'rhel', 'fedora'
         'ntpd'
       when 'debian'
         'ntp'
       else
         'ntpd'
     end

This attribute uses conditions to tell the chef-client the correct name of the init script that will be used to start Network Time Protocol (NTP), by platform. The attribute that is being set by this code block is ``node[:ntp][:service]`` and the chef-client can use this attribute to identify the correct init script for Network Time Protocol (NTP) on any node and for any platform. If Debian, use ``ntp`` and for everything else use ``ntpd``.

Edit Recipe
-----------------------------------------------------
To install Network Time Protocol (NTP), a recipe needs to do three things:

# Install Network Time Protocol (NTP)
# Create a configuration file; this will be done using the ``ntp.conf.erb`` template file
# Start the ``ntp`` or ``ntpd`` service, depending on the platform; this will be done using the ``node[:ntp][:service]`` attribute

Open the ``default.rb`` recipe file and replace the contents of that file with the following:

.. code-block:: ruby

   package 'ntp' do
     action :install
   end

   template '/etc/ntp.conf' do
     source 'ntp.conf.erb'
     variables( :ntp_server => 'time.nist.gov' )
     notifies :restart, 'service[ntp_service]'
   end

   service 'ntp_service' do
     service_name node[:ntp][:service]
     action [:enable, :start]
   end

The **package** resource installs the Network Time Protocol (NTP) package. The **template** resource gets the template file from the cookbook, and then uses it to create a ``ntp.conf`` file in the ``/etc/ntp.conf`` directory on the node, after which it notifies the **service** resource to restart the ``ntp`` or ``ntpd`` service. The **service** resource ensures that the ``ntp`` or ``ntpd`` service is started and enabled.

Install NTP on CentOS
-----------------------------------------------------
Now let's install Network Time Protocol (NTP) in CentOS. From the chef-repo, run:

.. code-block:: bash

   $ kitchen converge default-centos-71

As it installs, the chef-client will report back something similar to the following:

.. code-block:: bash

   -----> Starting Kitchen (v1.2.2.dev)
   -----> Converging <default-centos-71>...
          Preparing files for transfer
          Preparing cookbooks from project directory
          Removing non-cookbook files before transfer
          Preparing nodes
          Transferring files to <default-centos-71>
          [2014-07-10T20:43:50+00:00] INFO: Starting chef-zero on port 8889 with repository at repository at /tmp/kitchen
          One version per cookbook
          [2014-07-10T20:43:50+00:00] INFO: Forking chef instance to converge...
          Starting Chef Client, version 12.4.1
          [2014-07-10T20:34:52+00:00] INFO: *** Chef 12.4.1 ***
          [2014-07-10T20:34:52+00:00] INFO: Chef-client pid: 4229
          [2014-07-10T20:35:00+00:00] INFO: Setting the run_list to ["recipe[chef-repo::default]"] from CLI options
          [2014-07-10T20:35:00+00:00] INFO: Run List is [recipe[chef-repo::default]]
          [2014-07-10T20:35:00+00:00] INFO: Run List expands to [chef-repo::default]
          [2014-07-10T20:35:00+00:00] INFO: Starting Chef Run for default-centos-71
          [2014-07-10T20:35:00+00:00] INFO: Running start handlers
          [2014-07-10T20:35:00+00:00] INFO: Start handlers complete.
          [2014-07-10T20:35:00+00:00] INFO: HTTP Request Returned 404 Not Found : Object not found: /reports/nodes/default-centos-71/runs
          resolving cookbooks for run list: ["chef-repo::default"]
          [2014-07-10T20:35:00+00:00] INFO: Loading cookbooks [chef-repo@0.1.0]
          Synchronizing Cookbooks:
          [2014-07-10T20:35:00+00:00] INFO: Storing updated cookbooks/chef-repo/attributes/default.rb in the cache.
            - chef-repo
          Compiling Cookbooks...   
          Converging 3 resources
          Recipe: chef-repo::default
            * package[ntp] action install[2014-07-10T20:35:00+00:00] INFO: Processing package[ntp] action install (chef-repo::default line 10)
            * service[ntp_service] action enable[2014-07-10T20:35:18+00:00] INFO: Processing service[ntp_service] action enable (chef-repo::default line 14)   
            * service[ntp_service] action start[2014-07-10T20:35:18+00:00] INFO: Processing service[ntp_service] action start (chef-repo::default line 14)
            * template[/etc/ntp.conf] action create[2014-07-10T20:35:18+00:00] INFO: Processing template[/etc/ntp.conf] action create (chef-repo::default line 19)
          [2014-07-10T20:35:18+00:00] INFO: template[/etc/ntp.conf] backed up to /tmp/kitchen/backup/etc/ntp.conf.chef-20140710203518.551604
          [2014-07-10T20:35:18+00:00] INFO: template[/etc/ntp.conf] updated file contents /etc/ntp.conf
              - update content in file /etc/ntp.conf from 12d181 to 5b4e15
              - restore selinux security context
          [2014-07-10T20:35:18+00:00] INFO: template[/etc/ntp.conf] sending restart action to service[ntp_service] (delayed)
            * service[ntp_service] action restart[2014-07-10T20:35:18+00:00] INFO: Processing service[ntp_service] action restart (chef-repo::default line 14)
          [2014-07-10T20:35:20+00:00] INFO: service[ntp_service] restarted
              - restart service service[ntp_service]
          [2014-07-10T20:35:20+00:00] INFO: Chef Run complete in 20.062008227 seconds
          Running handlers:
          [2014-07-10T20:35:20+00:00] INFO: Running report handlers
          Running handlers complete
          [2014-07-10T20:35:20+00:00] INFO: Report handlers complete
          Chef Client finished, 2/5 resources updated in 27.444399186 seconds
          Finished converging <default-centos-71> (0m30.97s).
   -----> Kitchen is finished. (0m31.28s)

Install NTP on Ubuntu
-----------------------------------------------------
And finally, install Network Time Protocol (NTP) in Ubuntu. From the chef-repo, run:

.. code-block:: bash

   $ kitchen converge default-ubuntu-1404

As it installs, the chef-client will report back something similar to the following:

.. code-block:: bash

   -----> Starting Kitchen (v1.2.2.dev)
   -----> Converging <default-ubuntu-1404>...
          Preparing files for transfer
          Preparing cookbooks from project directory
          Removing non-cookbook files before transfer
          Preparing nodes
          Transferring files to <default-ubuntu-1404>
          [2014-07-10T20:41:26+00:00] INFO: Starting chef-zero on port 8889 with repository at repository at /tmp/kitchen       
          One version per cookbook       
          [2014-07-10T20:41:26+00:00] INFO: Forking chef instance to converge...       
          Starting Chef Client, version 12.4.1       
          [2014-07-10T20:41:26+00:00] INFO: *** Chef 12.4.1 ***       
          [2014-07-10T20:41:26+00:00] INFO: Chef-client pid: 2106       
          [2014-07-10T20:41:28+00:00] INFO: Setting the run_list to ["recipe[chef-repo::default]"] from CLI options       
          [2014-07-10T20:41:28+00:00] INFO: Run List is [recipe[chef-repo::default]]       
          [2014-07-10T20:41:28+00:00] INFO: Run List expands to [chef-repo::default]       
          [2014-07-10T20:41:28+00:00] INFO: Starting Chef Run for default-ubuntu-1404       
          [2014-07-10T20:41:28+00:00] INFO: Running start handlers       
          [2014-07-10T20:41:28+00:00] INFO: Start handlers complete.       
          [2014-07-10T20:41:28+00:00] INFO: HTTP Request Returned 404 Not Found : Object not found: /reports/nodes/default-ubuntu-1404/runs       
          resolving cookbooks for run list: ["chef-repo::default"]       
          [2014-07-10T20:41:28+00:00] INFO: Loading cookbooks [chef-repo@0.1.0]       
          Synchronizing Cookbooks:       
          [2014-07-10T20:41:28+00:00] INFO: Storing updated cookbooks/chef-repo/attributes/default.rb in the cache.       
            - chef-repo       
          Compiling Cookbooks...       
          Converging 3 resources       
          Recipe: chef-repo::default       
            * package[ntp] action install[2014-07-10T20:41:28+00:00] INFO: Processing package[ntp] action install (chef-repo::default line 10)       
            * service[ntp_service] action enable[2014-07-10T20:41:28+00:00] INFO: Processing service[ntp_service] action enable (chef-repo::default line 14)    
            * service[ntp_service] action start[2014-07-10T20:41:28+00:00] INFO: Processing service[ntp_service] action start (chef-repo::default line 14)       
          [2014-07-10T20:41:28+00:00] INFO: service[ntp_service] started
              - start service service[ntp_service]
            * template[/etc/ntp.conf] action create[2014-07-10T20:41:28+00:00] INFO: Processing template[/etc/ntp.conf] action create (chef-repo::default line 19)
          [2014-07-10T20:41:28+00:00] INFO: template[/etc/ntp.conf] backed up to /tmp/kitchen/backup/etc/ntp.conf.chef-20140710204128.387392       
          [2014-07-10T20:41:28+00:00] INFO: template[/etc/ntp.conf] updated file contents /etc/ntp.conf       
               - update content in file /etc/ntp.conf from 12d181 to 5b4e15       
          [2014-07-10T20:41:28+00:00] INFO: template[/etc/ntp.conf] sending restart action to service[ntp_service] (delayed)       
            * service[ntp_service] action restart[2014-07-10T20:41:28+00:00] INFO: Processing service[ntp_service] action restart (chef-repo::default line 14)       
          [2014-07-10T20:41:29+00:00] INFO: service[ntp_service] restarted
              - restart service service[ntp_service]
          [2014-07-10T20:41:29+00:00] INFO: Chef Run complete in 1.372541156 seconds       
          Running handlers:       
          [2014-07-10T20:41:29+00:00] INFO: Running report handlers       
          Running handlers complete       
          [2014-07-10T20:41:29+00:00] INFO: Report handlers complete       
          Chef Client finished, 3/5 resources updated in 3.313988417 seconds       
          Finished converging <default-ubuntu-1404> (0m6.49s).
   -----> Kitchen is finished. (0m6.79s)

.. note:: Did it work? Sometimes on the Ubuntu platform the Apt cache gets out of date and the chef-client is unable to download the correct package. This will result in an exception and the chef-client run will fail. Add this to the default recipe to run the ``apt-get-update`` command at the start of the chef-client run:

   .. code-block:: ruby

      execute 'apt-get-update' do
        command 'apt-get update'
        ignore_failure true
      end

   The **execute** resource block won't run on CentOS because the CentOS platform uses the Yum package manager, and not the Apt package manager.

   Re-run the following command:

   .. code-block:: bash

      $ kitchen converge default-ubuntu-1404

Verify Instance List
-----------------------------------------------------
To verify if both instances have been converged, run the following command:

.. code-block:: bash

   $ kitchen list

.. code-block:: bash

   Instance             Driver   Provisioner  Verifier  Transport  Last Action
   default-ubuntu-1404  Vagrant  ChefZero     Busser    Ssh        Converged
   default-centos-71    Vagrant  ChefZero     Busser    Ssh        Converged

.. 
.. Add Debian
.. -----------------------------------------------------
.. It's simple to add additional platforms for testing. For example, let's add support in Kitchen for Debian. First, update the .kitchen.yml file:
.. 
.. .. code-block:: javascript
.. 
..    platforms:
..      - name: ubuntu-14.04
..      - name: centos-7.1
..      - name: debian-8.1
.. 
.. Run the following command:
.. 
.. .. code-block:: bash
.. 
..    $ kitchen list
.. 
.. .. code-block:: bash
.. 
..    Instance             Driver   Provisioner  Verifier  Transport  Last Action
..    default-ubuntu-1404  Vagrant  ChefZero     Busser    Ssh        Converged
..    default-centos-71    Vagrant  ChefZero     Busser    Ssh        Converged
..    default-debian-81    Vagrant  ChefZero     Busser    Ssh        <Not Created>
.. 
.. Run the following command:
.. 
.. .. code-block:: bash
.. 
..    $ kitchen create default-debian-81
.. 
.. Re-run ``kitchen list`` and the last action for ``default-debian-81`` is updated to ``Created``.
.. 
.. Now run the following command:
.. 
.. .. code-block:: bash
.. 
..    $ kitchen create default-debian-81
.. 
.. and the recipe will converge on the node just like it did for the Ubuntu and CentOS instances and the last action is updated to ``Converged``.
.. 
.. Compare the results of all three converge processes to see how Chef behaves on all three platforms. While there are some differences between the platforms, the results are identical.
..

.. 
.. More About Resources
.. =====================================================
.. The chef-client includes many built-in resources: **execute**, **directory**, **package**, **service**, **file**, **template**, **user**, **script**, and **git**.
.. 
.. The sections below quickly describe the most popular resources. For the full list of built-in Chef resources, see `Resources <https://docs.chef.io/resource.html#resources>`_. You can also `create your own resources <https://docs.chef.io/lwrp_custom.html>`_ or `use the resources built into the community cookbooks <http://supermarket.chef.io>`_.
.. 
.. Execute Commands
.. -----------------------------------------------------
.. Commands are executed using the **execute** resource using an attribute to specify the actual command to run. See `execute <https://docs.chef.io/resource_execute.html>`_ for more information about executing commands.
.. 
.. Manage Directories
.. -----------------------------------------------------
.. Directories are hierarchies of folders that comprise all the information stored on a computer. There are two ways to manage directories. The first is via the **directory** resource, which manages directories starting from the root directory. And the second is the **remote_directory**, which transfers directory structures defined in cookbooks to nodes. See `directory <https://docs.chef.io/resource_directory.html>`_ for more information about managing directories. If the directory is defined in a cookbook, use `remote_directory <https://docs.chef.io/resource_remote_directory.html>`_ instead.
.. 
.. Manage Packages
.. -----------------------------------------------------
.. Packages are collections of files that comprise software applications or some part of an operating system. Use the package resource to manage these packages, unless they are sourced via RubyGems and installed directly from within recipes or are sourced from a cookbook. See `package <https://docs.chef.io/resource_package.html>`_ for more information about managing packages. There are quite a few platform-specific package resources as well, though most of the time simply using the **package** is all that's necessary. For packages that are located in cookobooks, use `chef_gem <https://docs.chef.io/resource_chef_gem.html>`_. And for packages that are only included via recipes, use `gem_package <https://docs.chef.io/resource_gem_package.html>`_.
.. 
.. Manage Services
.. -----------------------------------------------------
.. Services can be started, stopped, enabled, disabled, reloaded, and restarted. See `service <https://docs.chef.io/resource_service.html>`_ for more information about managing services.
.. 
.. Manage Files
.. -----------------------------------------------------
.. Files are managed in several ways. The **file** resource manages files that are already present on a node. Files are transferred to nodes from cookbooks using the **cookbook_file** resource and are transferred to nodes from remote locations using the **remote_file** resource. See `file <https://docs.chef.io/resource_file.html>`_ for more information about managing files, `remote_file <https://docs.chef.io/resource_remote_file.html>`_ for transferring files from remote locations, and `cookbook_file <https://docs.chef.io/resource_cookbook_file.html>`_ for transferring files that are located in cookbooks.
.. 
.. Manage Templates
.. -----------------------------------------------------
.. Templates are used to generate files based on variables and logic contained within the template file. Chef uses Embedded Ruby (ERB) templates and Ruby expressions and statements to define the template file. Template source files must be located within cookbooks. See `template <https://docs.chef.io/resource_template.html>`_ for more information about managing files using Embedded Ruby (ERB) templates.
.. 
.. Manage Users, Groups
.. -----------------------------------------------------
.. Users and groups can be added, updated, removed. User passwords can be locked and unlocked. See `group <https://docs.chef.io/resource_user.html>`_ for more information about managing users and user passwords. The `group <https://docs.chef.io/resource_group.html>`__ resource manges groups.
.. 
.. Use Script Interpreters
.. -----------------------------------------------------
.. Script interpreters execute scripts on a node, similar to the **execute** resource, and with the ability to specify the interpreter that the chef-client should use. See `script <https://docs.chef.io/resource_script.html>`_ for more (general) information about using scripts in recipes. Interpreter-specific resources are available, with `bash <https://docs.chef.io/resource_bash.html>`_ being the most popular. Also available: `csh <https://docs.chef.io/resource_csh.html>`_, `perl <https://docs.chef.io/resource_perl.html>`_, `powershell_script <https://docs.chef.io/resource_powershell_script.html>`__, `python <https://docs.chef.io/resource_python.html>`_, and `ruby <https://docs.chef.io/resource_ruby.html>`_. Two Microsoft Windows-specific resources are also available: `batch <https://docs.chef.io/resource_batch.html>`_ and `powershell_script <https://docs.chef.io/resource_powershell_script.html>`__.
.. 
.. Use Source Control
.. -----------------------------------------------------
.. Most users of Chef keep their code in some type of version source control. Chef can interact with this code from recipes. git is a very popular choice. The `git <https://docs.chef.io/resource_git.html>`_ resource is used to manage files that exist in a git repository. There is also a resource for `subversion <https://docs.chef.io/resource_subversion.html>`_, another popular version source control tool.
.. 
.. 
.. About Cookbooks
.. =====================================================
.. .. include:: ../includes_cookbooks/includes_cookbooks.rst
.. 
.. Every cookbook follows a defined structure, but individiaul cookbooks can take on many different styles depending on how your organization wants to manage its code, who authored them, and how they are intended to be used. Some cookbooks contain only a single, default recipe. Others may contain only a library file. Some may contain only a few attributes. And other cookbooks may contain several custom resources along with many attributes and templates, and so on.
.. 
.. Some cookbooks you will build yourself. Some cookbooks will be provided by the community. Most community cookbooks will be managed using Berkshelf, which is a dependency manager included in the Chef development kit. Occasionally, a community cookbook will be forked, but more often a wrapper cookbook is created to handle your organization-specific requirements while still allowing use of the community cookbook.
.. 
.. The most important thing to know about cookbooks is that there are lots of ways to build good ones. There are patterns to follow, there are guidelines. There are recomended ways of dealing with attributes. There are recommended ways of creating custom resources. But ultimately, a good cookbook is the one that works for your organization. Ideally, this cookbook works across your infrastructure. Most organizations have a mix of private (internal) and public (community) cookbooks in use in their organization.
.. 
.. 
.. Cookbook Patterns
.. -----------------------------------------------------
.. .. include:: ../includes_cookbook/includes_cookbook_pattern.rst
.. 
.. 
.. About Ruby
.. =====================================================
.. .. include:: ../includes_ruby/includes_ruby.rst
..

Conclusion
=====================================================
.. tag chef_about

Chef is a thin DSL (domain-specific language) built on top of Ruby. This approach allows Chef to provide just enough abstraction to make reasoning about your infrastructure easy. Chef includes a built-in taxonomy of all the basic resources one might configure on a system, plus a defined mechanism to extend that taxonomy using the full power of the Ruby language. Ruby was chosen because it provides the flexibility to use both the simple built-in taxonomy, as well as being able to handle any customization path your organization requires.

.. end_tag

