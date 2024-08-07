# hcloud plugin

[![fluentci pipeline](https://shield.fluentci.io/x/hcloud)](https://pkg.fluentci.io/hcloud)
[![ci](https://github.com/fluentci-io/hcloud-plugin/actions/workflows/ci.yml/badge.svg)](https://github.com/fluentci-io/hcloud-plugin/actions/workflows/ci.yml)

This plugin sets up your CI/CD pipeline with a specific version of [hcloud cli](https://github.com/hetznercloud/cli).

## 🚀 Usage

Add the following command to your CI configuration file:

```bash
fluentci run --wasm hcloud setup
```

## Functions

| Name   | Description                               |
| ------ | ----------------------------------------- |
| setup  | Installs a specific version of hcloud cli.  |

## Code Usage

Add `fluentci-pdk` crate to your `Cargo.toml`:

```toml
[dependencies]
fluentci-pdk = "0.2.1"
```

Use the following code to call the plugin:

```rust
use fluentci_pdk::dag;

// ...

dag().call("https://pkg.fluentci.io/hcloud@v0.1.0?wasm=1", "setup", vec!["latest"])?;
```

## 📚 Examples

Github Actions:

```yaml
- name: Setup Fluent CI CLI
  uses: fluentci-io/setup-fluentci@v5
  with:
    wasm: true
    plugin: hcloud
    args: |
      setup
  env:
    GITHUB_ACCESS_TOKEN: ${{ secrets.GITHUB_TOKEN }}
- name: Show hcloud CLI version
  run: hcloud version
```
