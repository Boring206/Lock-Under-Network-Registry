# Contributing a Plugin to the L.U.N. Registry

Any developer can contribute a law plugin. Once reviewed and signed by the maintainer, it becomes an **officially certified** plugin that all L.U.N. users can install with `lun law install <name>`.

---

## Two Ways to Write a Law

### Option A — `.lunpolicy` (Recommended for most rules)

No Rust required. A simple DSL that anyone can write:

```lunpolicy
name = "lun-community-no-console-log"
version = "1.0.0"
description = "Block console.log in production JavaScript"

[[rules]]
id = "no-console-log"
severity = "error"
pattern = "console\\.log("
message = "Remove console.log before committing to production."
languages = ["javascript", "typescript"]
```

Use `L.U.N: Draft New Law (AI-Powered)` in the VS Code extension to generate one automatically.

### Option B — Rust WASM Plugin (For complex logic)

Use the SDK template:

```bash
lun plugin init my-law-name
cd my-law-name
# Edit src/lib.rs
cargo build --target wasm32-wasip1 --release
```

See [`lun_plugin_sdk`](https://github.com/Boring206/Lock-Under-Network/tree/main/lun_plugin_sdk) for the full API.

---

## Submission Steps

### 1. Fork this repository

```bash
git clone https://github.com/Boring206/Lock-Under-Network-Registry.git
cd Lock-Under-Network-Registry
git checkout -b community/my-law-name
```

### 2. Add your plugin file

- **`.lunpolicy`**: Place in `community/<your-law-name>.lunpolicy`
- **WASM plugin**: Place the compiled `.wasm` in `community/<your-law-name>.wasm`

```
Lock-Under-Network-Registry/
  community/
    my-law-name.lunpolicy   ← your file here
    my-law-name.wasm        ← or compiled WASM
```

### 3. Open a Pull Request

Fill in the [PR template](.github/PULL_REQUEST_TEMPLATE.md). The maintainer will:

1. Review the law logic for safety and correctness
2. Test against the standard test suite (`lun check`)
3. Sign the WASM with `lun_master.key` (Ed25519)
4. Add the entry to `registry.json`
5. Merge → plugin becomes immediately available to all users

---

## Naming Convention

| Type | Format | Example |
|:--|:--|:--|
| Official Standard | `lun-std-<topic>` | `lun-std-security` |
| Official Law | `lun-law-<topic>` | `lun-law-dos-attack` |
| Community | `lun-community-<topic>` | `lun-community-no-console-log` |
| Organisation | `lun-org-<org>-<topic>` | `lun-org-acme-api-rules` |

---

## What Gets Rejected

- Rules that block legitimate development patterns without justification
- Rules with regex patterns that cause catastrophic backtracking
- WASM plugins that use `unsafe` blocks without justification
- Plugins that attempt file system access outside the WASM sandbox
- Duplicate/near-duplicate rules already covered by `lun-std-*`

---

## After Acceptance

Your plugin will appear in:
- `registry.json` with official Ed25519 signature
- `lun law list` output for all users
- The registry README table with your name as author

**The signature means**: the L.U.N. maintainer has reviewed and cryptographically vouches for this plugin. Users can verify this with `lun verify-cert`.
