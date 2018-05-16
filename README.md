ansible-secure-ssh
==================

A role that takes some basic steps to secure SSHD.  If you are looking for a role that goes much more in depth I recommend taking a look at https://github.com/dev-sec/ansible-ssh-hardening.

Requirements
------------

None

Role Variables
--------------

**secure_ssh_utility_group** - The name of the utility group that the two utility users will be assigned to. (Note: This role does not currently use the group that is created.) _Default: utilty_

**secure_ssh_console_user** - The name of the user to be created that can only access the host via console. _Default: greedo_

**secure_ssh_console_user_pass** - The crypted password that the user defined in secure_ssh_console_user will use.  Follow the instructions at http://docs.ansible.com/ansible/latest/reference_appendices/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module on how to properly generate a crypted password. _Default: None_

**secure_ssh_user** - The user to be created that can access the host via SSH. _Default: dengar_

**secure_ssh_user_pub_key** - The pubkey of the secure_ssh_user. _Default: None_

Example Playbook
----------------

```
  ---
  - hosts: all
    remote_user: root
    vars:
      secure_ssh_console_user_pass: "$6$RSywjWK49JxHculX$rp9klWFR.ZfBmYu3Y7miHEirlbPat/mqAEulr2f4pTCuq4s5/QibbpaHCJbNQb5HBkC9SzUF9PicHctmgEyLx0" # Han shot first.
      secure_ssh_user_pub_key: "{{ lookup('file', '~/.ssh/id_rsa.pub') }}"
    roles:
      - ansible-secure-ssh
```

License
-------

MIT

Author Information
------------------

Mike Keller (mike.k@blu-web.com)
