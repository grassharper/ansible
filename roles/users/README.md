Ansible role to manage users and groups

## Configuration knobs

* users_create_same_group (default: true) - Making each user have their own group with group name same as user name
* users_default_group (default: users) - The group all users should belong to
* users_create_homedirs (default: true) - Create home dirs for new users
* users: [], groups: [] - Lists of users and groups to create

## User create

* username - The user's username.
* name - The full name of the user
* uid - The numeric user id for the user (for uid consistency across systems)
* password - Optionally set the user's password to this crypted value. Otherwise the account will be locked
* groups - A list of supplementary groups for the user.
* state - Whether the account should exist or not
* ssh-key - This should be a list of ssh keys for the user.

Note: To generate crypted passwords for the user module you can use Python. First, ensure that the Passlib password hashing library is installed:
```bash
$ pip install passlib
```
SHA512 password values can then be generated as follows:

```bash
$ /usr/local/bin/python
Python 2.7.10 (default, Jul 13 2015, 12:18:59) 
[GCC 4.2.1 Compatible Apple LLVM 6.0 (clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from passlib.hash import sha512_crypt;
>>> import getpass;
>>> print sha512_crypt.encrypt(getpass.getpass())
Password: Password 
$6$rounds=100000$XHGMl4d87ndInP/X$sVIHOVLOVii1SVr7hmw4eCx58h37u6h0rclCm6BbD8pk/wo5rbm7NLkZrJ4Ou8tirinP7t6zJEM/YVFQH7ayY.
```


Example:

    ---
    users:
      - username: grassharper
        name: AB
        groups: ['wheel']
        uid: 1001
        state: present
        ssh_key:

