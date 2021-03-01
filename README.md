Role Common
=========

Common settings for servers (hostname, username, timezone, locales, ntp, unattended-upgrades).

Requirements
------------

- Make sure your current user can login to every server by SSH public-private-key.
- Ensure package `sudo`is installed and current user is member of the `sudo` group.
- Caution: This role can change the hostnames, so update your inventory accordingly.

Role Variables
--------------

- `adminuser`: New or already existing admin user. The role ensures that this user is present on every host.
- `locale`: Locale, e.g. "de_DE.UTF-8".
- `timezone`: Timezone, e.g. "Europe/Berlin".
- `ntp_server`: List of primary NTP servers querried by ntp.
- `ntp_server_backup`: List of backup NTP servers, querried by ntp when primary NTP servers are not available.

Dependencies
------------

- `community.general`: For setting locale and timezone.
- `ansible.posix`

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
        - common

License
-------

MIT
