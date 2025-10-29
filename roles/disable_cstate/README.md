# Role: disable_cstate

Disable CPU C-states for performance-sensitive workloads.

## Workflow

- Configure kernel boot parameters
- Optionally disable C-states via sysfs at runtime
- Optionally deploy a systemd service holding `/dev/cpu_dma_latency` open

## Variables

- `disable_cstate_kernel_opts`: kernel parameters (default: `processor.max_cstate=0 intel_idle.max_cstate=0 idle=poll`)
- `disable_cstate_apply_runtime`: apply sysfs runtime (default: true)
- `disable_cstate_apply_dma_latency`: deploy systemd service for `/dev/cpu_dma_latency` (default: false)

## Example

```yaml
- hosts: all
  become: true
  roles:
    - disable_cstate
      vars:
        disable_cstate_apply_dma_latency: true
