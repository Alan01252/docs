debops.ruby
###########

|Travis CI| |test-suite| |Ansible Galaxy|

.. |Travis CI| image:: http://img.shields.io/travis/debops/ansible-ruby.svg?style=flat
   :target: http://travis-ci.org/debops/ansible-ruby

.. |test-suite| image:: http://img.shields.io/badge/test--suite-ansible--ruby-blue.svg?style=flat
   :target: https://github.com/debops/test-suite/tree/master/ansible-ruby/

.. |Ansible Galaxy| image:: http://img.shields.io/badge/galaxy-debops.ruby-660198.svg?style=flat
   :target: https://galaxy.ansible.com/list#/roles/1595



``debops.ruby`` role installs selected Ruby version via APT package manager.
By default APT picks the Ruby packages to install automatically - if you
have backported Ruby 2.1 packages, they will be installed if available; if
you don't have them, ``debops.ruby`` will install current Ruby packages
available on your system.

If you want to install Ruby 2.1 packages on Debian Wheezy, set
``ruby_version: 'backport'`` in your inventory and this role will use
``debops.backporter`` role to automatically backport all required packages
from Debian Jessie. These packages will be installed on the build host and
uploaded to Ansible Controller to a specific directory, where
``debops.reprepro`` role can find them and automatically import them to local
APT repository, at which point these packages will become available to all
hosts in a cluster.

This role will also install gems from `RubyGems`_ specified in a list.

.. _RubyGems: http://rubygems.org/

Installation
~~~~~~~~~~~~

This role requires at least Ansible ``v1.7.0``. To install it, run::

    ansible-galaxy install debops.ruby


Role dependencies
~~~~~~~~~~~~~~~~~

- ``debops.apt_preferences``
- ``debops.backporter``


Role variables
~~~~~~~~~~~~~~

List of default variables available in the inventory::

    ---
    
    # Specify version of Ruby to install:
    # - 'apt':      (default) will install Ruby packages automatically depending on
    #               what's available in APT at the time
    #
    # - 'backport': will enable backporting of packages from the next distribution
    #               (currently on Debian Wheezy it's required to install Ruby 2.1
    #               packages)
    #
    ruby_version: 'apt'
    
    # Install 'rubygems-integration' package (on older distributions it might not
    # exist)
    ruby_gems_integration: True
    
    # Lists of additional APT packages to install with Ruby packages (for all
    # hosts, group of hosts, specific host or role dependency). You can use these
    # lists to for example install packaged gems.
    ruby_packages: []
    ruby_group_packages: []
    ruby_host_packages: []
    ruby_dependent_packages: []
    
    # Lists of Ruby gems to install from RubyGems.org. Role will use conservative
    # approach and not install or update any gems, that are already installed, either
    # via gem or via APT.
    ruby_default_gems: [ 'bundler' ]
    ruby_gems: []
    ruby_group_gems: []
    ruby_host_gems: []
    ruby_dependent_gems: []




Authors and license
~~~~~~~~~~~~~~~~~~~

``debops.ruby`` role was written by:

- Maciej Delmanowski | `e-mail <mailto:drybjed@gmail.com>`__ | `Twitter <https://twitter.com/drybjed>`__ | `GitHub <https://github.com/drybjed>`__

License: `GPLv3 <https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29>`_

