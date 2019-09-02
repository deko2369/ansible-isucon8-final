## Requirements

* Ubuntu 18.04 LTS

## How to use

```
# edit remote server
$ vim inventory

# edit ansible setting (remote username etc, etc...)
$ vim ansible.cfg

# provisioning
$ ansible-playbook -i inventory bench.yml -K
$ ansible-playbook -i inventory blackbox.yml -K
$ ansible-playbook -i inventory webapp.yml -K
```

## Specifications

### User information

* User: isucon
* Password: isucon

### Blackbox

```
$ systemctl start isucoin.blackbox.service
```

### Webapp

```
$ systemctl start isucoin.service
```
