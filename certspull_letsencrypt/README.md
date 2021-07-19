Role Name
=========

This role pulls certificates from a remote host to a local destination (typically a role's `files/` folder) based on user-specified from/to variables.

Requirements
------------

None.

Role Variables
--------------

Set the following variables via a mechanism like `host_vars/(hostname)`, your playbook, or the ansible command line:
* `certs_remote_folder` : remote pathspec
* `certs_local_folder` : local pathspec
* override the `cert_files` list if you're using some other naming convention

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
    - hosts: servers
      roles:
         - role: certspull_letsencrypt  # or renamed role via requirements.yml
           certs_remote_prefix: /home/certuser/certs
           certs_local_prefix: roles/nginx/files/certs
```
License
-------

GNU 2.0

Author Information
------------------

No comment.

Installation
------------

As part of a larger playbook, add the following in `requirements.yml` (`name` can be whatever you prefer):
```
- name: certupdate_nginx
  src: git+https://github.com/zer0master/ansible-certspull-letsencrypt.git
  scm: git
```
Then from the base of your repo, install with
```
ansible-galaxy role install -vvvv --role-file requirements.yml --roles-path roles/
```
This assumes a layout with roles, host/group_vars, and possibly inventory as first-level folders.
