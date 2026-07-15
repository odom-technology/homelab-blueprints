# VM guest standard

## Required metadata

- Stable guest name and numeric ID policy.
- Owner, purpose, environment, source repository, and physical placement.
- CPU, RAM, disk, network, startup order, recovery priority, and backup class.
- Data classification, secret inputs, listeners, dependencies, and health checks.

## Baseline

- Use supported firmware/machine settings and install the guest agent.
- Apply explicit CPU, RAM, and disk limits; avoid allocating all host capacity.
- Use cloud-init or another repeatable bootstrap where supported.
- Restrict management access and document every listener.
- Enable time synchronization and centralized logging appropriate to data sensitivity.
- Define backup, restore, upgrade, rollback, and decommission procedures.

## Device passthrough

Document why passthrough is required, host kernel/firmware settings, device ownership,
guest recovery on different hardware, backup limitations, and the effect on host console
or other guests.
