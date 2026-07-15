# Tailnet-only service decision points

Before implementation, decide:

- Whether the service receives its own Tailnet identity or uses a host-level proxy.
- Which user/group/tag identities may connect.
- Whether the application itself binds only to loopback/private networking or also to
  the LAN.
- How HTTPS certificates and names are issued.
- Whether the application supports subpaths or requires its own hostname.
- How health monitoring reaches the service without broadening user access.
- What local integrations require LAN egress.
- How access behaves if the Tailnet control plane is temporarily unreachable.

Validate from an authorized Tailnet client, an unauthorized Tailnet client, an ordinary
LAN client, and an Internet client. Only the intended path should succeed.
