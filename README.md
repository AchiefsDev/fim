# FIM — File Integrity Monitoring

[![Chat - Join us on Slack](https://img.shields.io/badge/Slack-join%20us%20-blue?logo=slack)](https://join.slack.com/t/filemonitor/shared_invite/zt-1au9t0hf4-yOsW6D3pGPqzzYsAJt9Dvg)
[![License](https://img.shields.io/github/license/Achiefs/fim)](https://github.com/Achiefs/fim/blob/main/LICENSE)
[![Build](https://img.shields.io/badge/version-0.6.4-059669?logo=rust&logoColor=white)](https://www.rust-lang.org)
[![Coverage](https://coveralls.io/repos/github/Achiefs/fim/badge.svg)](https://coveralls.io/github/Achiefs/fim)
[![Docs](https://img.shields.io/badge/Web-Docs-brightgreen)](https://documentation.achiefs.com/)
[![Platform](https://img.shields.io/badge/platform-Linux%20|%20macOS%20|%20Windows-lightgrey)](https://github.com/Achiefs/fim)

---

**FIM** is a high-performance **File Integrity Monitoring** tool written in Rust. It runs silently in the background, watching your files and alerting you the instant anything changes — creating a complete, searchable history of every modification.

Think of it as a **24/7 security camera for your filesystem**. If someone modifies a config file, drops a malicious script, or accidentally deletes something important, FIM catches it all.

---

## Why FIM?

| | Traditional tools (e.g. OSSEC) | **FIM** |
|---|---|---|
| **Language** | C / legacy stacks | **Rust** — memory safe & blazing fast |
| **Resource usage** | High overhead | Minimal footprint |
| **Integration** | Limited | **ElasticSearch, OpenSearch, Wazuh** |
| **Modern audit** | Basic logging | Full **auditd** event data — who, what, how |

---

## ⚡ Quick Start

### Install

Download the latest release package for your platform from the [Releases page](https://github.com/Achiefs/fim/releases).

| Platform | Package | Install command |
|---|---|---|
| **Debian / Ubuntu** | `.deb` | `dpkg -i fim*.deb` |
| **CentOS / RHEL** | `.rpm` | `yum install fim-*.rpm` |
| **Windows** | `.msi` | `.\fim-VERSION-x64.msi /q` |
| **macOS** | `.pkg` | `sudo installer -pkg fim*.pkg -target /` |

### Start FIM

| Platform | Command |
|---|---|
| **Linux** (systemd) | `systemctl start fim` |
| **Windows** | `NET START FimService` |
| **macOS** (launchd) | `sudo launchctl load -w /Library/LaunchDaemons/com.Achiefs.fim.launchd.plist` |

### Verify

After starting FIM, it begins monitoring immediately. Check for events:

- **Linux:** `cat /var/lib/fim/events.json`
- **Logs:** `cat /var/log/fim/fim.log`
- **Test:** `touch /etc/fake_file.txt` and check the events file — then `rm /etc/fake_file.txt`

For full setup instructions, see the [Installation guide](https://documentation.achiefs.com/docs/installation-guide.html).

---

## 🔒 Features

### Continuous Monitoring
- **File watcher** — detects any action on watched files: read, write, create, delete, rename, move.
- **Real-time alerting** — events are emitted instantly. No polling delays.
- **Recursive scanning** — monitors entire directories with a single rule.

### Deep Visibility
- **Content & metadata changes** — detects modifications to file content, attributes, ownership, and permissions.
- **Extended audit data** — when the Linux **auditd** daemon is available, FIM captures the full chain: which user, which process, and which command triggered the change.
- **Historical storage** — every event is stored, giving you a complete timeline you can query at any time.

### Seamless Integration
- **Native indexers** — ships with built-in ingesters for **ElasticSearch**, **OpenSearch**, and **Wazuh**. Your events are search-ready out of the box.
- **Extensible architecture** — add custom integrations by implementing the ingester interface.

### Built on Rust
- **Fast** — zero-cost abstractions and no garbage collection.
- **Safe** — memory safety guaranteed by the Rust compiler.
- **Reliable** — developed with a strict TDD methodology and comprehensive test suite.

### Cross-Platform
- **Linux**, **macOS**, and **Windows** — one tool, every environment.

---

## 📖 Documentation

| Resource | Link |
|---|---|
| Getting Started | https://documentation.achiefs.com/#how-to-install-fim |
| Configuration Guide | https://documentation.achiefs.com/docs/configuration-file.html |
| Development Setup | https://documentation.achiefs.com/docs/development.html |
| Full Docs | https://documentation.achiefs.com/ |

---

## 🧱 Configuration

Sample configuration files for all platforms are included in the `config/` directory:

```
config/
├── index_template.json    # Search index template
├── linux/                 # Linux examples
├── macos/                 # macOS examples
└── windows/               # Windows examples
```

Customize paths, watch rules, and indexer targets to match your environment.

---

## 🤝 Contribute

We welcome feedback and contributions!

- **Issues** — open a [GitHub issue](https://github.com/Achiefs/fim/issues) for bugs or feature requests.
- **Email** — reach us at [support@achiefs.com](mailto:support@achiefs.com).
- **Slack** — join our [Slack workspace](https://join.slack.com/t/filemonitor/shared_invite/zt-1au9t0hf4-yOsW6D3pGPqzzYsAJt9Dvg) for real-time discussion.
- **Development** — see the [Development guide](https://documentation.achiefs.com/docs/development.html) to build from source.

---

## 📄 License

This project is distributed under the terms of the [MIT License](https://github.com/Achiefs/fim/blob/main/LICENSE).
