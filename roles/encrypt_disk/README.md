# Role: encrypt_disk

Encrypt the second disk in the system (one that is not the root partition) using LUKS, create a filesystem, and mount it.

## Workflow

- Detect candidate disks excluding the root device via UUID
- Run safety assertions
- Initialize and open LUKS container
- Format with a filesystem
- Mount at the configured mount point
- Update `/etc/crypttab` and `/etc/fstab`
- Regenerate initramfs if needed

## Variables

- `luks_name`: name for the encrypted mapping (default: `securedata`)
- `filesystem`: filesystem type (`ext4` by default)
- `mount_point`: mount target (default `/mnt/securedata`)
- `use_keyfile`: whether to use a keyfile instead of passphrase (default: `false`)
- `luks_keyfile`: location of keyfile if `use_keyfile=true`
- `luks_passphrase`: passphrase for encryption

## Example

```yaml
- hosts: all
  become: true
  roles:
    - role: encrypt_disk
      vars:
        use_keyfile: true
        luks_keyfile: /root/luks-securedata.key
