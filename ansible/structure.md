"""
Ansible recomments to use below folder/file strcture for organizing playbooks.

Article - https://www.digitalocean.com/community/tutorials/how-to-manage-multistage-environments-with-ansible

"""

.
├── ansible.cfg
├── environments/
│   │
│   ├── 000_cross_env_vars
│   │
│   ├── dev/
│   │   ├── group_vars/
│   │   │   ├── all/
│       │   │   ├── 000_cross_env_vars -> ../../../000_cross_env_vars
│   │   │   │   └── env_specific
│   │   │   ├── db
│   │   │   └── web
│   │   └── hosts
│   │
│   ├── prod/
│   │   ├── group_vars/
│   │   │   ├── all/
│   │   │   │   ├── 000_cross_env_vars -> ../../../000_cross_env_vars
│   │   │   │   └── env_specific
│   │   │   ├── db
│   │   │   └── web
│   │   └── hosts
│   │
│   └── stage/
│       ├── group_vars/
│       │   ├── all/
│       │   │   ├── 000_cross_env_vars -> ../../../000_cross_env_vars
│       │   │   └── env_specific
│       │   ├── db
│       │   └── web
│       └── hosts
│
├── playbook.yml
│
└── . . .


""" 

- Create these folder structure
- Create files accordingly
- Synlink common-all-env file 000_cross_env_vars under each env specific all folder
- Update ansible.cfg with a default env (so that if you don't specify "-i", that gets called (usually yr dev)

"""
$ cat ansible.cfg
[defaults]
inventory = ./environments/dev
$
