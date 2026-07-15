# LXC guest standard

Prefer unprivileged containers. Use a VM when the workload runs untrusted code, needs a
stronger kernel boundary, requires complex device passthrough, or does not fit container
backup and upgrade behavior.

## Required decisions

- Privileged or unprivileged, with justification.
- Nesting and keyctl requirements.
- UID/GID mappings and persistent-volume ownership.
- Device access and cgroup permissions.
- Network listeners and firewall policy.
- Resource limits, startup order, backup, restore, and migration constraints.

Do not enable broad nesting or privileged mode merely to make a copied deployment
command work. Record the smallest required capability and test removal.
