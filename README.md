pyslackers.docker
=========

Ansible role to install and run docker containers/services.

Role Variables
--------------

* `docker_containers`: Dict of docker containers to run (with container name as `key`).
    * `image`: Image to run
    * Most parameters of the `docker_container` ansible module are supported.

* `docker_services`: Dict of docker services to run with compose (the `key` is used as `project_name`).
    * Most parameters of the `docker_service` ansible module are supported

Example Playbook
----------------

```yml
- hosts: localhost
  vars:
    docker_containers:
      nginx:
        image: nginx
        ports: 80:80
    docker_services:
      nginx:
        definition:
          version: '2'
          services:
            web:
              image: nginx
              ports:
                - 81:80
  roles: 
    - pyslackers.docker
```

License
-------

MIT
