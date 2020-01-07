# Ansible Role: Docker Traefik

[![Build Status](https://travis-ci.org/ambimax/ansible-role-docker-traefik.svg?branch=master)](https://travis-ci.org/ambimax/ansible-role-docker-traefik)

Installs traefik for docker on Debian/Ubuntu linux servers.

## Requirements

None

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):


```
traefik_user: root
traefik_group: docker
traefik_docker_domain: localhost

traefik_auth_users: []
traefik_certificates: []
traefik_debug: false
traefik_dir: /etc/traefik
traefik_hostname: "traefik.{{ traefik_docker_domain }}"
traefik_https: true
traefik_https_redirect: true
traefik_image: traefik:2.1
traefik_container_name: traefik
traefik_log_level: ERROR
traefik_log_file: ""
traefik_access_log_file: ""
traefik_networks:
  - traefik
traefik_network_scope: swarm
traefik_onhostrule: true
traefik_state: started
traefik_default_volumes:
  - "/var/run/docker.sock:/var/run/docker.sock"
  - "{{ traefik_dir }}/traefik.yml:/etc/traefik/traefik.yml"
  - "{{ traefik_dir }}/acme.json:/etc/traefik/acme.json"
  - "{{ traefik_dir }}/hostname:/etc/traefik/hostname"

traefik_volumes: []
traefik_users_basic_auth: []

traefik_docker_endpoint: unix://var/run/docker.sock
traefik_docker_enable_swarmmode: false
traefik_docker_swarmmode_refreshseconds: 15

traefik_acme_email: ''
traefik_acme_storage: '{{ traefik_dir }}/acme.json'
traefik_acme_domains: []
traefik_acme_staging: true
```

## Lets Encrypt SSL Support

```
traefik_acme_email: ''
traefik_acme_storage: '{{ traefik_dir }}/acme.json'
traefik_acme_domains: []
traefik_acme_staging: true
```

Make sure to set traefik_acme_staging to false when deploying to production.

## Custom volumes

```
traefik_volumes:
  - "{{ traefik_dir}}/logs:/var/log/traefik"
```

## Dependencies

None.

## Installation

```
$ ansible-galaxy install tschifftner.docker-traefik
```

## Example Playbook
```
- hosts: server

  roles:
	- { role: tschifftner.docker-traefik }
```

## Supported OS

 - Debian 9 (Stretch)
 - Debian 8 (Jessie)
 - Ubuntu 18.04 (Bionic Beaver)
 - Ubuntu 16.04 (Xenial Xerus)
 
## Required ansible version

Ansible 2.5+

## License

[MIT License](http://choosealicense.com/licenses/mit/)

## Author Information

 - [Tobias Schifftner](https://twitter.com/tschifftner), [ambimax® GmbH](https://www.ambimax.de)
