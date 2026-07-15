# Sanitization review for reusable blueprints

## Automated candidates

- Secret scanners and high-entropy checks.
- Patterns for private/public addresses, MAC addresses, serial formats, domains, email,
  Tailnet names, and account identifiers.
- Schema validation requiring documentation-value markers.
- Generated-output and rendered-diagram checks.

## Manual review

- Does the example reveal topology or relationships even after values are replaced?
- Do commit history, tags, releases, artifacts, or container layers retain old values?
- Do screenshots contain browser profiles, notifications, tabs, or image metadata?
- Can copied commands cause destructive or Internet-exposing behavior without warning?
- Are security limitations and required local changes explicit?

An encrypted production value is still production data and should not be copied into a
public example unless the encryption and metadata exposure have been deliberately
reviewed.
