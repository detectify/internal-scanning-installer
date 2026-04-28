# Detectify Internal Scanner — Packaged Installer

Single-script installer for the [Detectify Internal Scanner](https://detectify.com). Deploys and manages a fully functional scanner on a single Linux host with no Kubernetes knowledge required.

The installer provisions a lightweight [k3s](https://k3s.io/) cluster, deploys all scanner components via Helm, and provides commands for status monitoring, log viewing, updates, credential rotation, and uninstallation.

## Requirements

- **OS:** Ubuntu 22.04+ or Debian 12+ (x86_64)
- **RAM:** 4 GB minimum, 8 GB recommended
- **Disk:** 20 GB free minimum, 50 GB recommended
- **Init system:** systemd
- **Network:** Outbound HTTPS to `registry.detectify.com`, `license.detectify.com`, `connector.detectify.com`
- **Dependencies:** `curl` or `wget`

## Quick Start

```bash
curl -sSL https://github.com/detectify/internal-scanning-installer/releases/latest/download/detectify-scanner -o detectify-scanner
chmod +x detectify-scanner
sudo ./detectify-scanner install
```

The installer walks you through entering your credentials (license key, connector API key, registry username, registry password), validates them, and deploys the scanner. The entire process takes about 5 minutes.

## Commands

All commands require `sudo`.

| Command | Description |
|---------|-------------|
| `install` | Install the scanner with interactive credential setup |
| `status` | Show health of all components, API reachability, and disk usage |
| `logs` | View logs (`-f` to follow, add component name to filter) |
| `restart` | Restart all or a single component |
| `update` | Pull latest images and redeploy |
| `reconfigure` | Change credentials without reinstalling |
| `preflight` | Run system checks without installing |
| `uninstall` | Remove everything (requires confirmation) |

## Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `SCANNER_IMAGE_TAG` | `stable` | Container image tag to deploy |
| `CHART_VERSION` | `1.3.0` | Helm chart version to download |

```bash
sudo SCANNER_IMAGE_TAG=1.2.0 ./detectify-scanner install
```

## Documentation

Full documentation is available at [detectify.com/support](https://detectify.com/support):

- [Requirements](https://docs.detectify.com/internal-network-testing/deploy/packaged/requirements)
- [Getting Started](https://docs.detectify.com/internal-network-testing/deploy/packaged/getting-started)
- [Commands Reference](https://docs.detectify.com/internal-network-testing/deploy/packaged/commands)
- [Troubleshooting](https://docs.detectify.com/internal-network-testing/deploy/packaged/troubleshooting)

## Related

- [Helm Charts](https://github.com/detectify/helm-charts) — Deploy on any Kubernetes cluster
- [Terraform Module (AWS)](https://github.com/detectify/terraform-aws-internal-scanning) — Production-ready EKS deployment
