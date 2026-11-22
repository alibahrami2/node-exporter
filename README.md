# Automated Prometheus Node Exporter Deployment with Ansible

A modular, idempotent **Ansible Role** designed to deploy and configure **Prometheus Node Exporter** across Linux environments (AlmaLinux, RHEL, Ubuntu, and Debian).

## Features
- **Multi-Environment & Multi-Architecture Support:** Runs seamlessly on RHEL-based and Debian-based distributions across `amd64` (`x86_64`) and `arm64` (`aarch64`) architectures.
- **Air-Gapped & Internal Mirror Ready:** Supports direct downloads from GitHub, internal artifact repositories (e.g., Nexus, Harbor), or local tarball distribution for offline servers.
- **Security Hardening:** Runs under a dedicated unprivileged system user (`node_exporter` with `/usr/sbin/nologin`) and applies `systemd` sandboxing (`NoNewPrivileges`, `ProtectSystem=strict`, `ProtectHome`).
- **Optional Firewall Management:** Automatically restricts port `9100` access to the Prometheus server IP on `firewalld` and `UFW` when enabled.
- **Idempotent Execution:** Checks the installed binary version prior to downloading or restarting services.

---

## Project Structure
```text
ansible-node-exporter/
├── inventory/
│   ├── prod.ini              # Production host definitions
│   └── stage.ini             # Staging host definitions
├── roles/
│   └── node_exporter/
│       ├── defaults/main.yml # Default variables (version, ports, URLs)
│       ├── handlers/main.yml # Service restart handlers
│       ├── tasks/main.yml    # Installation and configuration tasks
│       └── templates/        # systemd unit template
└── deploy_node_exporter.yml  # Main entry-point playbook
