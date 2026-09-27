# Security Policy

## Reporting a Vulnerability

**Do not open a public GitHub issue for security vulnerabilities.**

If you discover a security issue in the provisioning scripts or configurations, please email us directly at:

📧 **[security@hut.one](mailto:security@hut.one)**

### What to expect
- We will acknowledge receipt of your report within 48 hours.
- We will provide an initial assessment and a timeline for resolution.
- We will credit responsible disclosures in our release notes (unless you prefer to remain anonymous).

## Scope

**In scope:**
- The Bash provisioning scripts in `/playbook/scripts/`
- The `nftables` firewall configurations in `/playbook/configs/`
- The WireGuard configuration templates

**Out of scope:**
- The Hut.one desktop application (separate security policy)
- Third-party dependencies (please report to upstream maintainers)
- Vulnerabilities requiring physical access to the server
