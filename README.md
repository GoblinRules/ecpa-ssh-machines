# SSH and Machines

![Latest release](https://img.shields.io/github/v/release/GoblinRules/ecpa-ssh-machines)

Named SSH machine profiles, explicit key selection, pinned host keys and fixed read-only connection diagnostics.

This is the dedicated **release repository** for `ssh-machines`. It owns this plugin's releases and version history. The source lives in the shared [ECPA Plugins workspace](https://github.com/GoblinRules/ecpa-plugins/tree/master/plugins/ssh-machines); shared libraries are maintained once, rather than copied between release repositories.

## Install and update

Add this public registry in ECPA's plugin settings:

```text
https://raw.githubusercontent.com/GoblinRules/ecpa-plugins/master/registry.json
```

Refresh the Plugin store and install **SSH and Machines**. Existing users keep the same registry URL and plugin ID. Restart the core when prompted. Windows x64 binaries are available under [Releases](https://github.com/GoblinRules/ecpa-ssh-machines/releases).

## Documentation

- [Usage, configuration and supported features](https://github.com/GoblinRules/ecpa-plugins/tree/master/plugins/ssh-machines/README.md)
- [Shared agent tools documentation](https://github.com/GoblinRules/ecpa-plugins/blob/master/docs/agent-tools.md)
- [Source workspace and contributing](https://github.com/GoblinRules/ecpa-plugins)
- [Release process](https://github.com/GoblinRules/ecpa-plugins/blob/master/docs/releases.md)
- [Public-source and release privacy audit](https://github.com/GoblinRules/ecpa-plugins/blob/master/docs/publication-security-audit.md)
- [Central MCP runtime and Windows host setup](https://github.com/GoblinRules/ecpa-plugins/tree/master/runtime/mcp-gateway)

## Repository layout

```text
README.md                      Installation and source links
LICENSE                        MIT license
THIRD_PARTY_NOTICES.md          Dependency/artwork attribution
plugin.json                    Plugin and source identity
.github/workflows/release.yml   Build and publish this plugin from a source commit
```

Each release includes the DLL ZIP, SHA-256 checksums, `release.json` with its source commit, and a complete source workspace ZIP. The source commit in the release is authoritative; documentation on master may describe later changes.

## Publishing

Bump only `plugins/ssh-machines/Cargo.toml` in the source workspace, keep its runtime version and dependency metadata in sync, test, commit and push. Run **Actions → Publish plugin release** here with the full 40-character source commit SHA. The workflow builds only this plugin and publishes its version using this repository's own GitHub Actions token. No cross-repository token or token for end users is required.

This plugin has its own version history; its version does not need to match other plugins.

## 0.2.0 integration update

Connections Manager 0.8.0 and gateway 0.2.0 can reuse saved, verified machines for fixed diagnostics and individually approved service restarts. No arbitrary agent shell or per-machine executable is introduced.

See the [Windows setup and upgrade runbook](https://github.com/GoblinRules/ecpa-plugins/blob/master/runtime/mcp-gateway/HOST-READINESS.md) for runtime identity, side-by-side upgrades and pending central-host acceptance checks.

## 0.2.1 login and sidebar update

Optional **Remember key on this device** reuses the suite management key on the same
browser origin. **Lock & forget** clears the SSH tab key and shared saved key.
Browser storage is not encrypted; use it only on a trusted device. Automatic unlock
only reads the catalogue. SSH private keys remain with OpenSSH.

The display name is now **SSH and Machines**, avoiding escaped ampersands in ECPA's
sidebar. The plugin ID and existing machine profiles are unchanged.
