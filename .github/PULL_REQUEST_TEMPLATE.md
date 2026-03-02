## Community Plugin Submission

### Plugin Name
`lun-community-` <!-- fill in the rest -->

### Type
- [ ] `.lunpolicy` DSL rule
- [ ] Rust WASM plugin

### Description
<!-- What does this law enforce? What problem does it solve? -->

### Motivation
<!-- Why is this rule useful? Which AI coding mistake / security risk does it prevent? -->

### Languages Targeted
<!-- e.g., Rust, Python, JavaScript, TypeScript, All -->

### Test Cases

**Should VETO (bad code examples):**
```
<!-- paste 1-3 code snippets that should be blocked -->
```

**Should ALLOW (good code examples):**
```
<!-- paste 1-3 code snippets that should pass -->
```

### Self-Review Checklist

- [ ] The plugin name follows the `lun-community-<topic>` convention
- [ ] I have tested this locally with `lun check` against real code
- [ ] The VETO message is clear and actionable (tells the developer what to fix)
- [ ] This rule does not duplicate an existing `lun-std-*` plugin
- [ ] For WASM plugins: no `unsafe` blocks, no file system access outside sandbox
- [ ] For WASM plugins: compiled with `cargo build --target wasm32-wasip1 --release`

### Performance
<!-- Approximate latency per file check, if known. Target: < 5ms -->

### Author
GitHub: @<!-- your username -->
