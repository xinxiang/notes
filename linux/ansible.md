# Inventory
Add in /etc/ansible/hosts
```
[tapor]
old ansible_host=142.150.190.161 ansible_python_interpreter=/usr/local/bin/python2
new ansible_host=142.150.190.162
```
```
# ansible-inventory --list -y
all:
  children:
    tapor:
      hosts:
        new:
          ansible_host: 142.150.190.162
        old:
          ansible_host: 142.150.190.161
          ansible_python_interpreter: /usr/local/bin/python2
    ungrouped: {}

# ansible tapor --list-hosts
  hosts (2):
    old
    new
```
## Note
On old tapor, /usr/bin/python2 is version 2.4. Without ansible_python_interpreter, 
```
old | FAILED! => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "module_stderr": "Shared connection to 142.150.190.161 closed.\r\n", 
    "module_stdout": "  File \"/home/doe/.ansible/tmp/ansible-tmp-1612897030.28-22604-109673667683507/AnsiballZ_ping.py\", line 72\r\n    with open(args_path, 'rb') as f:\r\n            ^\r\nSyntaxError: invalid syntax\r\n", 
    "msg": "MODULE FAILURE\nSee stdout/stderr for the exact error", 
    "rc": 1
}
```

# Commands

```
ansible localhost -m ping -e 'ansible_python_interpreter=/usr/bin/python3'
ansible-playbook sample-playbook.yml -e 'ansible_python_interpreter=/usr/bin/python3'
```

# Reference
* Install & Config: https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-20-04
* Copy files: https://www.middlewareinventory.com/blog/how-to-copy-files-between-remote-servers-ansible-fetch-sync/
