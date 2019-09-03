ansible-isucon8-final
=====================

Ansible scripts for [isucon8-final](https://github.com/isucon/isucon8-final).

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

### Unix user information

* User: isucon
* Password: isucon

### Webapp

```
$ systemctl start isucoin.service
```

### Blackbox

```
$ systemctl start isucoin.blackbox.service
```

### Bench

```
$ cd isucon2018-final/
$ ./bench/bin/bench \
    -appep=https://<webapp>
    -bankep=https://<blackbox>:5515
    -logep=https://<blackbox>:5516
    -internalbank=https://<blackbox>:5515
    -internallog=https://<blackbox>:5516
    -result=result.json
    -log=stderr.log
$ cat result.json
{"job_id":"","ip_addrs":"https://<webapp>","pass":true,"score":417,"message":"ok", ...
```

## Main points of modification

* Added system file for systemctl management
    * [webapp](https://github.com/deko2369/ansible-isucon8-final/blob/master/roles/webapp/files/isucoin.service)
    * [blackbox](https://github.com/deko2369/ansible-isucon8-final/blob/master/roles/blackbox/files/isucoin.blackbox.service)
* Disabled SSL verification check (only Go)
    * [webapp](https://github.com/deko2369/ansible-isucon8-final/blob/master/roles/webapp/files/webapp.patch)
    * [bench](https://github.com/deko2369/ansible-isucon8-final/blob/master/roles/bench/files/bench.patch)
