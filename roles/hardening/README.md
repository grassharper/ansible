Ansible Hardening Role
=========

Ansible role apply various security related best practices - server hardening.

Requirements
------------

Tested on FreeBSD, Centos

Example Playbook
----------------

    ---
    - hosts: all
      gather_facts: yes
      become: yes
      become_user: root

      roles:
        - roles/hardening

License
-------

WTFPL-2.0
