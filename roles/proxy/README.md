Proxy
=====

A role to set proxy from system-wide to specific services.

Requirements
------------

Just details of the proxy.

Role Variables
--------------

- proxy_ip: Proxy IP address. it's necessary to set proxy correctly.
- proxy_port: Proxy port. it's necessary to set proxy correctly.
- proxy_scope: In which scope should the proxy set. By set the value for system_wide, shell_session, systemd_services, wget, apt and yum to 'true', the role will configure the proxy for that. Attention that if you don't define the proxy_scope variable, role will set proxy for all of them.
- proxy_remove: In which scope should the proxy removed. By set the value for system_wide, shell_session, systemd_services, wget, apt and yum to 'true', if the proxy was set for it, the role will remove that.
- proxy_systemd_services: If in proxy_scope the systemd_services value be 'true', for systemd services that define here (as list), the role will set proxy.

Dependencies
------------

No other role.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: Set proxy on the machines
      hosts: all
      become: true
      roles:
      - role: proxy
        vars:
          proxy_ip: "192.168.1.20"
          proxy_port: "1810"
          proxy_scope:
            system_wide: true
            shell_session: true
            systemd_services: true
            wget: true
            apt: true
            yum: true
          proxy_remove:
            system_wide: false
            shell_session: false
            systemd_services: false
            wget: false
            apt: false
            yum: false
          proxy_systemd_services:
            - containerd
