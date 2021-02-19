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

# playbook
## create directory

```
- name: create web-dir folder on host "{{groups['tapor'][1]}}"
  hosts: "{{groups['tapor'][1]}}"
  tasks:
  - name: create /data/tapor/web-dir
    file:
      path: /data/tapor/web-dir
      state: directory

```
## copy files and directories
```
- name: Sync Push files / directories from old to new - Executed on source host "{{groups['tapor'][0]}}"
  hosts: "{{groups['tapor'][1]}}" 
  user: doe 
  tasks:
    - name: Copy the file from old to new
      tags: sync-push
      synchronize:
        src: "{{ item }}"
        dest: "{{ item }}"
        mode: push
      delegate_to: "{{groups['tapor'][0]}}"
      register: syncfile
      with_items:
       - "/tmp/test.txt"
       - "/data/tapor/web-dir/doeapps/"
 ```
 * /tmp/test.txt will be copied from old to new
 * when copy directory, the parent directory has to be exist; /data/tapor/web-dir/ has to be existed on new server
 * without the trailing /; it becomes /data/tapor/web-dir/doeapps/doeapps on dest
```
with_items:
       - "/data/tapor/web-dir/doeapps"
```
## rysnc_opts
```
- name: Sync push Solr core from old to new - Executed on source host "{{groups['tapor'][0]}}; then manually put them into places on new server."
  hosts: "{{groups['tapor'][1]}}" 
  user: doe 
  tasks:
    - name: copy cores under /data1/solr/server
      tags: sync-push
      synchronize:
        src: "/data1/solr/server/"
        dest: "/tmp/cores/"
        archive: yes
        mode: push
        rsync_opts:
          - '--exclude=data'
          - '--exclude=solr.xml'
          - '--exclude=zoo.cfg'
      delegate_to: "{{groups['tapor'][0]}}"
      register: syncfile
```
**Note:** When I used "..." for rsync_opts, I got "Unsupported parameters for (synchronize) module: rysnc_opts ...", but double quotes worked in other tasks.

# Reference
* Install & Config: https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-20-04
* Copy files: https://www.middlewareinventory.com/blog/how-to-copy-files-between-remote-servers-ansible-fetch-sync/
