## How to use

```
# edit remote server
$ vim inventory

# edit ansible setting (remote username etc, etc...)
$ vim ansible.cfg

# provisioning
$ ansible-playbook -i inventory bench.yml -K
```

## TODO
* Regenerate crt/key files for SSL
