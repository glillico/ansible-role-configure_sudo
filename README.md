# Ansible Role : configure_sudo

This role configures files in the /etc/sudoers.d/ directry on the server.

## Requirements

None.

## Role Variables

### defaults/main.yml

    configure_sudo_setup_users: true

Should the sudoers files for users be created.

    configure_sudo_setup_groups: true

Should the sudoers files for groups be created.

    configure_sudo_user_file: 'u_{{ item.configure_sudo_users_name }}'

The names of the file to use for user configuration.

    configure_sudo_group_file: 'g_{{ item.configure_sudo_groups_name }}'

The names of the file to use for group configuration.

### vars/main.yml

    configure_sudo_sudoers_dir: /etc/sudoers.d

The directory that the sudoers files are stored in.

### User configuration.

    configure_sudo_users_name:

The users name.

    configure_sudo_users_hosts:

The hostname of the server this is allowed to be run on.

    configure_sudo_users_operator:

The user the allowed command should be run as.

    configure_sudo_users_option:

Sudo options such as NOPASSWD or NOEXEC

    configure_sudo_users_command:

Command allowed to be executed by sudo.

    configure_sudo_users_state:

### Group configuration.

    configure_sudo_groups_name:

The group name.

    configure_sudo_groups_hosts:

The hostname of the server this is allowed to be run on.

    configure_sudo_groups_operator:

The user the allowed command should be run as.

    configure_sudo_groups_option:

Sudo options such as NOPASSWD or NOEXEC

    configure_sudo_groups_command:

Command allowed to be executed by sudo.

    configure_sudo_groups_state:

Whether this line should be present or not in the sudoers file.

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
