<div align="center">

# 🏈 Hut.one — The Playbook

**Cryptographically separated multi-hop WireGuard orchestration.**

Your servers. Your keys. Your privacy.

[Architecture](docs/architecture.md) • [Security](SECURITY.md) • [Credits](CREDITS.md) • [Quick Start](#quick-start)

</div>

## What Is This?

This repository contains the **open-source provisioning scripts** that power the [Hut.one](https://hut.one) desktop application. 

These scripts handle the heavy lifting of turning standard Linux machines into a secure, multi-hop VPN network:

- 🔒 **Default-Deny Firewalls:** Locks down servers using `nftables`.
- 🛡️ **Relay & Exit Configuration:** Sets up WireGuard nodes with strict forwarding rules.
- 🔑 **Key Management:** Generates and manages cryptographic keys safely.
- ⚡ **Kernel Tuning:** Enables IP forwarding and network optimizations.
- 🧹 **Safe Teardown:** Ensures servers can be wiped and rebuilt without locking you out of SSH.

## The Architecture

Unlike traditional VPNs where a single provider sees everything, Hut.one uses a **relay/exit separation** model:

```text
You ──► Relay (sees your IP, can't decrypt) ──► Exit (decrypts, can't see you) ──► Internet
```

| Component | Sees Your IP? | Can Decrypt? | Sees Destinations? |
|-----------|:------------:|:------------:|:------------------:|
| **You**       | ✅            | ✅            | ✅                  |
| **Relay**     | ✅            | ❌            | ❌                  |
| **Exit**      | ❌            | ✅            | ✅                  |

**No single node has the complete picture.** Read our full [Threat Model](docs/threat-model.md).

## Quick Start (Manual Setup)

If you want to set this up manually without the Hut.one desktop app:

```bash
# 1. Clone the playbook
git clone https://github.com/hut-one/hut-one.git
cd hut-one

# 2. Audit your server (Checks OS, kernel, and WireGuard support)
./playbook/scripts/audit.sh user@your-relay-server

# 3. Set up a relay node (Opaque UDP forwarder)
./playbook/scripts/setup-relay.sh user@your-relay-server

# 4. Set up an exit node (WireGuard endpoint + NAT)
./playbook/scripts/setup-exit.sh user@your-exit-server
```

*Prefer a visual interface? The [Hut.one desktop app](https://hut.one) wraps these scripts in a drag-and-drop UI with real-time deployment feedback.*

## Trust, But Verify

This repository is intentionally open source. We believe privacy tools should be auditable. If you find a security issue, please see [SECURITY.md](SECURITY.md).

## Standing on the Shoulders of Giants

Hut.one is a proud user of [WireGuard](https://www.wireguard.com/) and is heavily inspired by the architectural research of [Obscura](https://obscura.net/). See [CREDITS.md](CREDITS.md) for our full acknowledgments.

## License

MIT License — see [LICENSE](LICENSE).
