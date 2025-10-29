```markdown
# Role: encrypt_partition

Encrypt the partition that is present on the disk next to the root partition

## Workflow

- Determine root partition via UUID
- Read list of partitions on that disk
- Pick next partition (index +1)
- Check partition size to pick correct luks format
- Run safety assertions
- Encrypt with LUKS
- Format and mount
- Update `/etc/crypttab` and `/etc/fstab`

## Variables

Same as in `encrypt_disk`:
- `luks_name`
- `filesystem`
- `mount_point`
- `use_keyfile`
- `keyfile_path`

## Example

```yaml
- hosts: all
  become: true
  roles:
    - role: encrypt_partition
      vars:
        mount_point: /mnt/part_securedata
