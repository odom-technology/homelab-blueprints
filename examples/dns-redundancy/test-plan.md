# DNS redundancy test plan

| Test | Expected result |
| --- | --- |
| Query resolver 1 over UDP/TCP | Correct filtered response |
| Query resolver 2 over UDP/TCP | Equivalent correct response |
| Stop resolver 1 guest | Clients resolve through resolver 2 |
| Stop resolver 2 guest | Clients resolve through resolver 1 |
| Stop route router 1 | All approved resolver routes remain through router 2 |
| Stop route router 2 | All approved resolver routes remain through router 1 |
| Block resolver 1 upstream | Health check detects functional failure |
| Compare policy exports | No unexplained rules or rewrites differ |
| Test IPv6-capable client | No bypass through unintended resolver |
| Stop both resolvers | Public DNS continues; private split names fail closed |
| Restore both resolvers | Republish private split DNS after resolver and route validation |

Record client operating system, lease behavior, resolver addresses, timestamps, and
evidence. Never run the full-outage test without independent gateway and console access.
