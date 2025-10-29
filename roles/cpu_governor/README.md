# Role: cpu_governor

Switch CPU operation mode from power-saving to performance.

## Workflow

- Set governor for all CPUs
- Apply cpufrequtils default governor
- Apply tuned profile (`latency-performance`, `throughput-performance`, or `realtime-virtual-guest`)
- Verify profile applied
- Optionally set per-CPU scaling governor if sysfs interface is present

## Variables

- `cpu_governor_profile`: tuned profile (default: `throughput-performance`)

## Example

```yaml
- hosts: all
  become: true
  roles:
    - role: cpu_governor
      vars:
        cpu_governor_profile: latency-performance
