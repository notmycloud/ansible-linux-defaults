# ansible-linux-defaults
Highly opinionated defaults for Linux systems.

Shell support is BASH only for now.
I am open to making changes or improvements as longs as they make sense to me and suit my pruposes.
Feel free to fork.

## Usage
playbook.yaml
```
---
- name: Play Name
  hosts: MyHosts
  
  roles:
    - role: notmycloud.linux_defaults
      vars:
        default_packages: # Set this to override the default packages to install as per `vars/{{OS-Family}}`
        default_shell: # Set this to override the default shell to configure and for new users.
        default_root_pass: # Set this to the password root should have. Plaintext, will be hashed and salted.
        default_shell_aliases: # Array of aliases to add to the shell
          - name: 'ls'
            command: 'ls -lah'
        global_users: # Array of users to create on every host.
          - name: username
            pass: P@$$w0rd1
            authorized_keys:
              - "key_1"
              - "key_2"
            sudo: bool
        host_users: # See global_users, will be merged at runtime so you can specify users that are only on 1 host.
```

## Support
For support, please raise an issue and provide the following items
- Sample task/playbook to replicate your issue
- Resultant file that is created.
- If modifying an existing file, please provide the unmodified version as well.
