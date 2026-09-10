# Decision example: keep the network core outside the cluster

- Status: example

## Context

A homelab shares Internet and Wi-Fi with household devices. Server experimentation must
not make basic connectivity depend on a hypervisor guest.

## Decision

Keep the modem, gateway/firewall, primary switch, and wireless AP outside the cluster and
on independent power. Use an existing combined router only if it can enforce the required
VLAN and recovery policy; otherwise use dedicated rack-independent network devices.

## Consequences

- Rack shutdown does not remove routing or Wi-Fi.
- Public client DNS remains available during rack outages.
- Management and server VLANs can be established before installing compute.
- Host and guest firewalls remain defense in depth behind default-deny inter-zone policy.

Adopters should write their own decision record; this example is not universally best.
