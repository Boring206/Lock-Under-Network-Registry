# Lock-Under-Network Registry

> The official signed plugin registry for the [L.U.N. Sovereign AI Governance](https://github.com/Boring206/Lock-Under-Network) system.

Every plugin listed here has been:
1. **Code-reviewed** by the L.U.N. maintainer
2. **Cryptographically signed** with the official `lun_master.key` (Ed25519)
3. **Merkle-proven** — tamper-evident via `lun certify`

---

## Official Plugins

| Name | Description | Tier |
|:--|:--|:--:|
| `lun-std-security` | RCE, XSS, unsafe blocks, hardcoded secrets | 1 |
| `lun-std-quality` | Complexity limits, function length, AI boilerplate | 1 |
| `lun-std-privacy` | PII leak, credential exposure, telemetry | 1 |
| `lun-std-no-todo` | Blocks `// TODO` deferral | 2 |
| `lun-std-pruner` | `.unwrap()`, file size > 10KB | 2 |
| `lun-std-hallucination` | Virtual APIs, deprecated library patterns | 2 |
| `lun-law-moltbot` | AI agent automation allowlist | 3 |
| `lun-law-dos-attack` | Infinite loops, unbounded recursion, FD exhaustion | 3 |

---

## Installing Plugins

```bash
# Install from registry
lun law install lun-std-security

# List all available plugins
lun law list

# Verify signatures locally
lun certify
```

---

## Contributing a Community Plugin

Want your plugin listed here? See [CONTRIBUTING.md](./CONTRIBUTING.md).

---

**Public key (for verification):**
```
9c583f50b1115689e87a674e8f6c9c3a0340dcca012355629838eb326c73ca32
```
