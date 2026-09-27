# Contributing to Hut.one

Thank you for your interest in improving the Hut.one playbook! 

Because these scripts directly manipulate firewalls, routing tables, and cryptographic keys on production servers, we maintain a strict standard for contributions.

## How to Contribute

1. **Fork** the repository.
2. **Create a branch** for your feature or fix (`git checkout -b fix/nftables-masquerade`).
3. **Test locally:** Ensure your changes work on a clean Debian 13 installation.
4. **Commit** your changes with clear, descriptive messages.
5. **Open a Pull Request** detailing what you changed and why.

## Code Standards

- **Idempotency:** Scripts must be safe to run multiple times without breaking the server state.
- **Fail-Safe:** Firewall rules must default to `drop` and explicitly allow only required traffic. Never open a port wider than necessary.
- **Comments:** Comment complex `nftables` or `ip route` logic heavily. Future users (and future us) need to understand *why* a rule exists.

## What We Are Currently Looking For

- Better error handling and rollback mechanisms in the Bash scripts.
- Support for additional Linux distributions (currently targeting Debian 13).
- Hardening of the `sysctl` network tuning parameters.
