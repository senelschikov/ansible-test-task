```markdown
# Role: rename_interface

Rename the primary network interface to a desired name (default `eth0`) using Netplan.

## Workflow

- Detect main interface via `ansible_default_ipv4.interface`
- Replace interface name with new name
- Apply configuration (`netplan apply`)
- Verify interface exists
- Show interface details

## Variables

- `target_iface_name`: desired new name (default `eth0`)

## Example

```yaml
- hosts: all
  become: true
  roles:
    - role: rename_interface
      vars:
        target_iface_name: net0
