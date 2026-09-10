# Redundant local DNS example

## Topology

- `lab-dns01` runs on physical node 1.
- `lab-dns02` runs on physical node 2.
- Two service routers on different nodes advertise the same exact resolver routes.
- A restricted private split namespace publishes both resolver addresses.
- Router DHCP and ordinary public DNS remain rack-independent.
- Each resolver reaches upstream DNS independently.
- Administration uses a restricted management path.

## Required invariants

1. Either resolver can answer without the other.
2. Policy differences are detected before deployment.
3. TCP and UDP queries are tested.
4. IPv4 and IPv6 behavior are intentional.
5. A client-level check detects upstream and filtering failures.
6. Loss of both resolvers removes only the private namespace; public names still resolve.

## Anti-patterns

- Publishing rack resolvers as global DNS without accepting the full-rack dependency.
- Hosting both resolvers on the same physical node.
- Advertising a whole server or management subnet when individual routes are sufficient.
- Treating process health as successful resolution.
- Exposing port 53 with an Internet-facing port forward.
- Backing up query logs without deciding whether they are sensitive.
