# ansible-kibana

An Ansible role for installing and configuring [Kibana](http://www.elasticsearch.org/overview/kibana/).

## Role Variables

- `kibana_version` - Kibana version to install (default: `4.0.1`)
- `kibana_os` - Kibana operating system build (default: `linux`)
- `kibana_arch` - Kibana architecture build (default: `x64`)
- `kibana_dir` - Directory to extract the Kibana archive (default: `/opt`)
- `kibana_host` - Kibana address to bind to (default: `0.0.0.0`)
- `kibana_port` - Kibana port (default: `5601`)
- `kibana_elasticsearch` - ElasticSearch endpoint (default: `http://localhost:9200`)
- `kibana_index` - Name of Kibana index in ElasticSearch (default: `.kibana`)
- `kibana_log` - Kibana log path (default: `/var/log/kibana.log`)
- `kibana_log_rotate_count` - Kibana log rotation count (default: `5`)
- `kibana_log_rotate_interval` - Kibana log rotation interval (default: `daily`)
- `kibana_ca` - Certificate
- `kibana_ssl_key_file` - Key file
- `kibana_ssl_cert_file` - Cert file
- `kibana_verify_ssl` -  set to false to have a complete disregard for the validity of the SSL cert.
- `kibana_elasticsearch_username` - basic auth username for maintaining the ```kibana_index```
- `kibana_elasticsearch_password` - basic auth password for maintaining the ```kibana_index```
- `kibana_service_startonboot` - start kibana service on boot - default no
- `kibana_service_state` - kibana service state - default enabled


## Include role in a larger playbook
### Add this role as a git submodule
Assuming your playbook structure is such as:
```
- my-master-playbook
  |- vars
  |- roles
  |- my-master-playbook-main.yml
  \- my-master-inventory.ini
```

Checkout this project as a submodule under roles:

```
$  cd roles
$  git submodule add https://github.com/comperiosearch/ansible-kibana.git ./kibana
$  git submodule update --init
$  git commit ./submodule -m "Added submodule as ./subm"
```

### Include this playbook as a role in your master playbook
Example `my-master-playbook-main.yml`:

```
---

#########################
# Kibana install #
#########################

- hosts: all_nodes
  user: ubuntu
  sudo: yes

  roles:
    - kibana

  vars_files:
    - vars/my-vars.yml
```




