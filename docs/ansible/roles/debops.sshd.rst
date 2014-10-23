debops.sshd
###########

|Travis CI| |test-suite| |Ansible Galaxy|

.. |Travis CI| image:: http://img.shields.io/travis/debops/ansible-sshd.svg?style=flat
   :target: http://travis-ci.org/debops/ansible-sshd

.. |test-suite| image:: http://img.shields.io/badge/test--suite-ansible--sshd-blue.svg?style=flat
   :target: https://github.com/debops/test-suite/tree/master/ansible-sshd/

.. |Ansible Galaxy| image:: http://img.shields.io/badge/galaxy-debops.sshd-660198.svg?style=flat
   :target: https://galaxy.ansible.com/list#/roles/1602



This role configures OpenSSH server for public key access, disables
password authentication and creates a specific configuration options for
``sftponly`` accounts.

Installation
~~~~~~~~~~~~

This role requires at least Ansible ``v1.7.0``. To install it, run::

    ansible-galaxy install debops.sshd


Role dependencies
~~~~~~~~~~~~~~~~~

- ``debops.ferm``
- ``debops.sshkeys``
- ``debops.auth``
- ``debops.tcpwrappers``


Role variables
~~~~~~~~~~~~~~

List of default variables available in the inventory::

    ---
    
    # List of IP addresses or CIDR networks to allow access to SSH without
    # restrictions.
    # They will be configured in iptables (via ferm) and /etc/hosts.allow (via
    # tcpwrappers).
    sshd_allow: []
    sshd_group_allow: []
    sshd_host_allow: []
    
    # By default SSH access from unknown IP addresses is limited and filtered by
    # iptables, you can disable this by changing variable below to 'true'. You will
    # have to enable access in iptables and tcpwrappers from any IP address
    # separately.
    sshd_unlimited_access: 'false'
    
    sshd_Port: 22
    sshd_PermitRootLogin: 'without-password'
    sshd_PasswordAuthentication: 'no'
    sshd_X11Forwarding: 'no'
    sshd_AllowGroups: 'root admins sshusers sftponly'
    
    sshd_authorized_keys: '/etc/ssh/authorized_keys'
    sshd_authorized_keys_monkeysphere: '/var/lib/monkeysphere/authorized_keys/%u'
    sshd_authorized_keys_global: '{{ sshd_authorized_keys }}/%u'
    sshd_authorized_keys_user: '%h/.ssh/authorized_keys %h/.ssh/authorized_keys2'
    
    sshd_known_hosts: []




Authors and license
~~~~~~~~~~~~~~~~~~~

``debops.sshd`` role was written by:

- Maciej Delmanowski | `e-mail <mailto:drybjed@gmail.com>`_ | `Twitter <https://twitter.com/drybjed>`_ | `GitHub <https://github.com/drybjed>`_

License: `GPLv3 <https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29>`_

