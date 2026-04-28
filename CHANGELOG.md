# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2026-04-25

### Added

- Single-script installer for Detectify Internal Scanner on Ubuntu/Debian hosts
- Interactive credential collection with real-time validation against registry and license servers
- Pre-flight checks: architecture, RAM, disk, systemd, network connectivity, CIDR conflicts, security frameworks
- Automated k3s provisioning (v1.31.6) with private registry authentication
- Helm chart deployment via k3s HelmChart CRD
- Pod readiness polling with configurable timeout
- Scanner API verification on NodePort 30000
- `install` command with idempotency guard (detects existing installation)
- `status` command showing k3s health, pod status, API reachability, and disk usage
- `logs` command with `-f` (follow) flag and per-component filtering
- `restart` command with optional single-component restart and rollout wait
- `update` command that pulls latest images and shows before/after comparison
- `reconfigure` command for credential rotation without reinstall
- `preflight` command for standalone system verification
- `uninstall` command with type-to-confirm safety prompt
- Two-tier thresholds: hard minimums (4 GB RAM, 20 GB disk) and soft recommendations (8 GB, 50 GB)
- Distro-aware package install suggestions (apt, dnf, zypper)
- SELinux, AppArmor, firewalld, UFW, and nftables detection
- CIDR conflict detection with automatic alternative selection
- Registry credential retry (up to 3 attempts)
- TTY-aware colored output with graceful fallback for non-interactive shells
- Environment variable overrides: `SCANNER_IMAGE_TAG`, `CHART_VERSION`

### Security

- Single-quoted YAML output to prevent injection in registry credentials
- Array-based k3s arguments to prevent shell injection
- Quoted credential values in config files
- No use of `eval` for user-supplied input

[Unreleased]: https://github.com/detectify/internal-scanning-installer/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/detectify/internal-scanning-installer/releases/tag/v1.0.0
