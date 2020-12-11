# InstrumentalD role for Ansible

[![GitHub workflow status](https://img.shields.io/github/workflow/status/ayltai/ansible-instrumentald/CI?style=flat)](https://github.com/ayltai/ansible-instrumentald/actions)
[![Ansible quality score](https://img.shields.io/badge/quality-5-success)](https://galaxy.ansible.com/ayltai/instrumentald)
[![Ansible role](https://img.shields.io/badge/role-ayltai.instrumentald-blue)](https://galaxy.ansible.com/ayltai/instrumentald)
![Maintenance](https://img.shields.io/maintenance/yes/2020?style=flat)
[![Release](https://img.shields.io/github/release/ayltai/ansible-instrumentald.svg?style=flat)](https://github.com/ayltai/ansible-instrumentald/releases)
[![License](https://img.shields.io/github/license/ayltai/ansible-instrumentald.svg?style=flat)](https://github.com/ayltai/ansible-instrumentald/blob/master/LICENSE)

Install and configure [InstrumentalD](https://instrumentalapp.com/) on RHEL/CentOS-based and Ubuntu systems

[![Buy me a coffee](https://img.shields.io/static/v1?label=Buy%20me%20a&message=coffee&color=important&style=flat&logo=buy-me-a-coffee&logoColor=white)](https://buymeacoff.ee/ayltai)

## Quick start

### Installation
```sh
ansible-galaxy install ayltai.instrumentald
```

### Usage
```yaml
---
- hosts: all
  roles:
    - ayltai.instrumentald
  vars:
    instrumental_api_key: replace_me
```

## Variables

| Name                            | Default | Description |
|---------------------------------|---------|-------------|
| `instrumental_api_key`          | `replace_me` | Your Instrumental account API key. |
| `instrumentald_docker_sockets`  | `[]` | The socket address of the Docker instances to be monitored. |
| `instrumentald_memcached_urls`  | `[]` | The URL of the Memcached instances to be monitored. |
| `instrumentald_mongodb_urls`    | `[]` | The URL of the MongoDB instances to be monitored. |
| `instrumentald_mysql_urls`      | `[]` | The URL of the MySQL instances to be monitored. |
| `instrumentald_nginx_urls`      | `[]` | The URL of the Nginx instances to be monitored. |
| `instrumentald_postgresql_urls` | `[]` | The URL of the PostgreSQL instances to be monitored. |
| `instrumentald_redis_urls`      | `[]` | The URL of the Redis instances to be monitored. |
| `instrumentald_package_name`    | `instrumentald_1.1.1_linux-x86_64` | The package name of InstrumentalD to be installed. |

## Development
This project uses [Docker](https://www.docker.com) to create an unified environment for development.

### Install Docker
Download and install Docker from [here](https://docs.docker.com/get-docker).

### Build Docker image
```sh
docker build --tag instrumentald:latest .
```

### Run Docker container
```sh
docker run \
--privileged \
-v $(pwd):/ansible-instrumentald \
-v /var/run/docker.sock:/var/run/docker.sock \
-v /sys/fs/cgroup:/sys/fs/cgroup:ro \
-it --rm \
instrumentald:latest
```

Now you have a shell running on a system with all the necessary tools installed.

### Install dependencies
In the Docker container, run:
```sh
pip3 install -r requirements.txt
```

### Unit testing
In the Docker container, run:
```sh
molecule test
```

## License
[MIT](https://github.com/ayltai/ansible-instrumentald/blob/master/LICENSE)

## References
* [Instrumental](https://instrumentalapp.com/)
* [Ansible](https://www.ansible.com)
* [Ansible Galaxy](https://galaxy.ansible.com)
