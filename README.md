# Ansible Test Task

This repository implements several automation roles and playbooks as part of test assignment.
It includes capabilities to:

- Encrypt a second disk (non-root)
- Encrypt the partition that is present on the disk next to the root partition
- Disable all CPU C-states
- Switching CPU operation from power-saving mode to more productive mode.
- Rename the active network interface
- Display list of CPUs and info about Intel Hyper-Threading (AMD multithreading).

### Structure

├── inventories/ # Host definitions by environment
├── playbooks/ # Individual playbooks that call roles
├── roles/ # Modular roles implementing each domain
└── README.md

### Usage

Some variables are encerypted with ansible-vault, so you might need to use --ask-vault-pass in that case.

Run the full workflow:
```bash
ansible-playbook -i inventories/hosts.yml test-task.yml --ask-vault-pass

Or run a specific playbook:
```bash
ansible-playbook -i inventory/hosts.yml playbooks/encrypt_disk.yml --ask-vault-pass


*Prerequisites*
Ansible ≥ 2.14 (for import_playbook, include_tasks)
Linux hosts (Ubuntu 20.04/24.04)
Appropriate privileges (become / root)
