# Example three-node architecture

```text
Example Internet
      |
Existing router (gateway, DHCP, Wi-Fi)
      |
Managed access switch
   +-- lab-pve01: network core
   +-- lab-pve02: trusted home systems
   +-- lab-pve03: applications and compute
```

## Assumptions

- The router is intentionally outside the virtualized cluster.
- All nodes have one network interface and local SSD storage.
- The switch and router provide one untagged LAN.
- Guest isolation uses VMs/LXCs and firewalls; physical-client segmentation is deferred.
- Cluster membership provides quorum and management, not automatic workload HA.
- Backups leave the protected node.

## Example placement

| Node | Guests | Failure-domain purpose |
| --- | --- | --- |
| `lab-pve01` | `lab-dns01`, optional remote-access router | Quiet network core |
| `lab-pve02` | `lab-dns02`, automation, MQTT, cameras | Second DNS domain and trusted services |
| `lab-pve03` | Monitoring, apps, public origin, CI, AI | Variable and higher-risk compute |

## What this example does not solve

- Wireless IoT or camera VLAN isolation.
- Shared-storage availability.
- Automatic restart of guests after a node loss.
- Long camera retention on small local disks.
- Secure handling of real credentials.
