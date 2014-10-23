debops.phpmyadmin
#################

|Travis CI| |test-suite| |Ansible Galaxy|

.. |Travis CI| image:: http://img.shields.io/travis/debops/ansible-phpmyadmin.svg?style=flat
   :target: http://travis-ci.org/debops/ansible-phpmyadmin

.. |test-suite| image:: http://img.shields.io/badge/test--suite-ansible--phpmyadmin-blue.svg?style=flat
   :target: https://github.com/debops/test-suite/tree/master/ansible-phpmyadmin/

.. |Ansible Galaxy| image:: http://img.shields.io/badge/galaxy-debops.phpmyadmin-660198.svg?style=flat
   :target: https://galaxy.ansible.com/list#/roles/1587



This role installs `PHPMyAdmin`_ interface for MySQL database. At the
moment it is designed to manage only a database on ``localhost``, and is
usually enabled by ``debops.mysql`` role itself in a specifically written
play. In the future it will be redesigned as a standalone installation when
secure access to remote databases is available.

.. _PHPMyAdmin: http://www.phpmyadmin.net/

Installation
~~~~~~~~~~~~

This role requires at least Ansible ``v1.7.0``. To install it, run::

    ansible-galaxy install debops.phpmyadmin


Role dependencies
~~~~~~~~~~~~~~~~~

- ``debops.secret``
- ``debops.php5``
- ``debops.nginx``


Role variables
~~~~~~~~~~~~~~

List of default variables available in the inventory::

    ---
    
    # Should PHPMyAdmin role manage its own dependencies?
    phpmyadmin_dependencies: True
    
    # What subdomain should be used for PHPMyAdmin in nginx configuration
    phpmyadmin_domain: [ 'mysql.{{ ansible_domain }}' ]
    
    # Default length of generated passwords
    phpmyadmin_password_length: '20'
    
    # Default PHPMyAdmin control password
    phpmyadmin_control_password: "{{ lookup('password', secret + '/credentials/' + ansible_fqdn + '/mysql/phpmyadmin/password length=' + phpmyadmin_password_length) }}"
    
    # List of IP addresses or network ranges in CIDR format, allowed to access
    # PHPMyAdmin. Leave empty to allow access from all IP addresses/networks
    phpmyadmin_allow: []
    
    # Max upload size for nginx and php5
    phpmyadmin_upload_size: '64M'
    
    # Maximum number of PHP5 processes for PHPMyAdmin
    phpmyadmin_php5_max_children: '20'




Authors and license
~~~~~~~~~~~~~~~~~~~

``debops.phpmyadmin`` role was written by:

- Maciej Delmanowski | `e-mail <mailto:drybjed@gmail.com>`_ | `Twitter <https://twitter.com/drybjed>`_ | `GitHub <https://github.com/drybjed>`_

License: `GPLv3 <https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29>`_

