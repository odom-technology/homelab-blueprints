# Decision example: keep the router outside the cluster

- Status: example

## Context

A homelab shares Internet and Wi-Fi with household devices. Server experimentation must
not make basic connectivity depend on a hypervisor guest.

## Decision

Retain the existing router as gateway, DHCP server, firewall/NAT boundary, and wireless
AP. Attach the cluster through an access switch.

## Consequences

- Rack shutdown does not remove routing or Wi-Fi.
- DNS filtering still needs a documented rack-outage fallback.
- Initial VLAN routing may be unavailable.
- Guest and host firewalls carry more responsibility for server workload separation.

Adopters should write their own decision record; this example is not universally best.
