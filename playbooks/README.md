
---

### Playbook READMEs (`playbooks/*.yml`)

Each playbook just wraps a role:

- **encrypt_disk.yml** → runs `encrypt_disk`
- **encrypt_partition.yml** → runs `encrypt_partition`
- **disable_cstate.yml** → runs `disable_cstate`
- **cpu_governor.yml** → runs `cpu_governor`
- **rename_interface.yml** → runs `rename_interface`
- **show_cpu_info.yml** → runs `show_cpu_info`

Example (`playbooks/encrypt_disk.yml`):

```markdown
# Playbook: encrypt_disk.yml

Runs the `encrypt_disk` role on all hosts to encrypt the second disk.

## Usage
```bash
ansible-playbook -i inventory/hosts.yml playbooks/encrypt_disk.yml
