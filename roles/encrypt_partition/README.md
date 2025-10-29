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

- `part_luks_name`
- `part_filesystem`
- `part_mount_point`
- `part_use_keyfile`
- `part_luks_keyfile`
- `part_luks_passphrase`

## Example

```yaml
- hosts: all
  become: true
  roles:
    - role: encrypt_partition
      vars:
        part_mount_point: /mnt/part_securedata
