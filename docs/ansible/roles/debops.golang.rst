debops.golang
#############

|Travis CI| |test-suite| |Ansible Galaxy|

.. |Travis CI| image:: http://img.shields.io/travis/debops/ansible-golang.svg?style=flat
   :target: http://travis-ci.org/debops/ansible-golang

.. |test-suite| image:: http://img.shields.io/badge/test--suite-ansible--golang-blue.svg?style=flat
   :target: https://github.com/debops/test-suite/tree/master/ansible-golang/

.. |Ansible Galaxy| image:: http://img.shields.io/badge/galaxy-debops.golang-660198.svg?style=flat
   :target: https://galaxy.ansible.com/list#/roles/1698



Install Go language (golang) support using Debian packages. You can choose
to install the system's default version of Go or use the 1.3.x version that
has been backported from Debian Jessie.

Installation
~~~~~~~~~~~~

This role requires at least Ansible ``v1.7.1``. To install it, run::

    ansible-galaxy install debops.golang


Role dependencies
~~~~~~~~~~~~~~~~~

- ``debops.backporter``


Role variables
~~~~~~~~~~~~~~

List of default variables available in the inventory::

    ---
    
    # Install either the 'apt' or 'backport' version of Golang
    #   'apt'      whatever version is available through apt on your OS/distro
    #   'backport' for when you're building the backport on your build server
    #
    # Versions for a few popular distros:
    #   Debian Wheezy: 1.0.2 -> backport version is 1.3.1
    #   Debian Jessie: 1.3.1
    #   Ubuntu Trusty: 1.2.1
    golang_version: 'apt'




Authors and license
~~~~~~~~~~~~~~~~~~~

``debops.golang`` role was written by:

- Nick Janetakis | `e-mail <mailto:nick.janetakis@gmail.com>`_ | `Twitter <https://twitter.com/nickjanetakis>`_ | `GitHub <https://github.com/nickjj>`_

License: `GPLv3 <https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29>`_

