# Ansible Role : configure_sudo

[![CI](https://github.com/glillico/ansible-role-configure_sudo/workflows/CI/badge.svg)](https://github.com/glillico/ansible-role-configure_sudo/actions?query=workflow%3ACI)

This role configures files in the /etc/sudoers.d/ directry on the server.

## Requirements

None.

## Role Variables

### defaults/main.yml

|Variable|Description|
|---|---|
|configure_sudo_setup_users|Should the sudoers files for users be created.<br>(Options: `true`, `false`)|
|configure_sudo_setup_groups|Should the sudoers files for groups be created.<br>(Options: `true`, `false`)|
|configure_sudo_user_file|The names of the file to use for user configuration.|
|configure_sudo_group_file|The names of the file to use for group configuration.|

### vars/main.yml

|Variable|Description|
|---|---|
|configure_sudo_sudoers_dir|The directory that the sudoers files are stored in.|

### User configuration.

|Variable|Description|
|---|---|
|configure_sudo_users_name|The users name.|
|configure_sudo_users_hosts|The hostname of the server this is allowed to be run on.|
|configure_sudo_users_operator|The user the allowed command should be run as.|
|configure_sudo_users_option|Sudo options such as NOPASSWD or NOEXEC|
|configure_sudo_users_command|Command allowed to be executed by sudo.|
|configure_sudo_users_state|Whether this line should be present or not in the sudoers file.|

### Group configuration.

|Variable|Description|
|---|---|
|configure_sudo_groups_name|The group name.|
|configure_sudo_groups_hosts|The hostname of the server this is allowed to be run on.|
|configure_sudo_groups_operator|The user the allowed command should be run as.|
|configure_sudo_groups_option|Sudo options such as NOPASSWD or NOEXEC|
|configure_sudo_groups_command|Command allowed to be executed by sudo.|
|configure_sudo_groups_state|Whether this line should be present or not in the sudoers file.|

#### Examples

##### User Configuration.

###### Configure testuser1 to be able to run the `/bin/whoami` command as root.

```
   - configure_sudo_users_name: 'testuser1'
     configure_sudo_users_hosts: 'ALL'
     configure_sudo_users_operator: 'ALL'
     configure_sudo_users_option: ''
     configure_sudo_users_command: '/bin/whoami'
     configure_sudo_users_state: 'present'
```

###### Configure testuser2 to be able to run the `/bin/whoami` command as root without entering a password.
```
   - configure_sudo_users_name: 'testuser2'
     configure_sudo_users_hosts: 'ALL'
     configure_sudo_users_operator: 'ALL'
     configure_sudo_users_option: 'NOPASSWD:'
     configure_sudo_users_command: '/bin/whoami'
     configure_sudo_users_state: 'present'
```

##### Group Configuration.

##### Configure testgroup1 to be able to run the `/bin/whoami` command as root.
```
   - configure_sudo_groups_name: 'testgroup1'
     configure_sudo_groups_hosts: 'ALL'
     configure_sudo_groups_operator: 'ALL'
     configure_sudo_groups_option: ''
     configure_sudo_groups_command: '/bin/whoami'
     configure_sudo_groups_state: 'present'
```

##### Configure testgroup2 to be able to run the `/bin/whoami` command as root without entering a password.
```
   - configure_sudo_groups_name: 'testgroup2'
     configure_sudo_groups_hosts: 'ALL'
     configure_sudo_groups_operator: 'ALL'
     configure_sudo_groups_option: 'NOPASSWD:'
     configure_sudo_groups_command: '/bin/whoami'
     configure_sudo_groups_state: 'present'
```

## Dependencies

None.

## Example Playbook

    - hosts: servers
      vars_files:
        - vars/main.yml
      roles:
        - glillico.configure_sudo

## License

MIT

## Author Information

This role was created in 2020 by Graham Lillico.
