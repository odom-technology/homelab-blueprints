# ODOM Homelab Blueprints

Reusable, sanitized building blocks for homelab infrastructure. Blueprints are derived
from tested patterns but contain no production credentials, addresses, identifiers,
domains, inventory, or policy.

## Repository map

- `ansible/` — reusable roles and collection scaffolding.
- `opentofu/` — infrastructure modules and composition examples.
- `cloud-init/` — guest bootstrap templates.
- `packer/` — reproducible image examples.
- `proxmox/` — VM, LXC, hook, and lifecycle patterns.
- `docker/` — Compose, health-check, and persistent-data patterns.
- `examples/` — complete sanitized reference scenarios.
- `schemas/` — schemas for blueprint inputs and metadata.
- `scripts/` — safe validation and administrative helpers.
- `tests/` — automated verification and example smoke tests.
- `docs/` — design decisions, limitations, and security guidance.

Blueprints favor explicit inputs, least privilege, predictable rollback, and clean
removal. They are examples, not a substitute for reviewing local requirements.

## First reference set

The initial examples document a three-node Proxmox cluster behind an existing router,
two independent DNS guests, guest standards, service metadata, and a Tailnet-only
application boundary. All addresses and names are documentation values.

See [open blueprint issues](ISSUES.md) before treating any scaffold as deployment-ready.
