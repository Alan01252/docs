debops.auth
###########

|Travis CI| |test-suite| |Ansible Galaxy|

.. |Travis CI| image:: http://img.shields.io/travis/debops/ansible-auth.svg?style=flat
   :target: http://travis-ci.org/debops/ansible-auth

.. |test-suite| image:: http://img.shields.io/badge/test--suite-ansible--auth-blue.svg?style=flat
   :target: https://github.com/debops/test-suite/tree/master/ansible-auth/

.. |Ansible Galaxy| image:: http://img.shields.io/badge/galaxy-debops.auth-660198.svg?style=flat
   :target: https://galaxy.ansible.com/list#/roles/1553



``debops.auth`` manages basic user authentication and authorization on
configured host, including setting up system groups with elevated
privileges.

Installation
~~~~~~~~~~~~

This role requires at least Ansible ``v1.7.0``. To install it, run::

    ansible-galaxy install debops.auth




Role variables
~~~~~~~~~~~~~~

List of default variables available in the inventory::

    ---
    
    # List of default accounts that are given admin status by being added to
    # 'admins' system group
    auth_admin_accounts: [ '{{ ansible_ssh_user }}' ]
    
    # List of default system accounts that are used in the playbook
    auth_system_groups:
    
      # Global system administrators, unrestricted root access, unrestricted SSH
      - 'admins'
    
      # Users in this group can connect to the host using SSH service
      - 'sshusers'
    
      # Users in this group have access only to chrooted SFTP service (without full
      # shell access) and cannot use SSH public keys in ~/.ssh/authorized_keys file
      # (only keys in '/etc/ssh/authorized_keys.d/user' are allowed)
      - 'sftponly'
    
      # Users in this group can reload nginx service using sudo and have access to
      # /etc/nginx/sites-local/ directory where they can put nginx vhost
      # configuration files to be enabled by Ansible in nginx
      # (this might be moved to 'nginx' role in the future)
      - 'webadmins'




Authors and license
~~~~~~~~~~~~~~~~~~~

``debops.auth`` role was written by:

- Maciej Delmanowski | `e-mail <mailto:drybjed@gmail.com>`_ | `Twitter <https://twitter.com/drybjed>`_ | `GitHub <https://github.com/drybjed>`_

License: `GPLv3 <https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29>`_

