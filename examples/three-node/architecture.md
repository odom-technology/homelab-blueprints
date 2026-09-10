# Example three-node architecture

```text
Example Internet
      |
Rack-independent modem / gateway / primary switch / Wi-Fi
      |
Managed rack switch
   +-- lab-pve01: network core
   +-- lab-pve02: secondary core and trusted home systems
   +-- lab-pve03: dedicated public production
```

## Assumptions

- The router is intentionally outside the virtualized cluster.
- All nodes have one network interface and local SSD storage.
- The gateway, switches, and AP support management, server, public, IoT, sensor, and
  guest zones.
- Inter-zone policy defaults to deny with exact documented exceptions.
- Hypervisors use a management zone; guests use server or public zones by role.
- Cluster membership provides quorum and management, not automatic workload HA.
- Backups leave the protected node.
- Public DNS is client-native; private split DNS depends on the rack by design.

## Example placement

| Node | Guests | Failure-domain purpose |
| --- | --- | --- |
| `lab-pve01` | `lab-dns01`, exact-route router 1, internal status | Quiet network core |
| `lab-pve02` | `lab-dns02`, exact-route router 2, automation, MQTT, monitoring, cameras | Second core domain and trusted services |
| `lab-pve03` | Separate public origins and initial ephemeral runner | Public-production isolation |

## What this example does not solve

- Vendor-specific discovery across VLANs.
- Shared-storage availability.
- Automatic restart of guests after a node loss.
- Long camera retention on small local disks.
- Secure handling of real credentials.
- A later fourth compute/recovery vote; that requires independent quorum-device design.
