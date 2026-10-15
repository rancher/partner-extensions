# Epinio Rancher Extension

The Epinio Extension brings the developer-friendly application platform [Epinio](https://epinio.io/) directly into Rancher, providing a unified interface for installing, managing, and operating Epinio across your fleet of Kubernetes clusters. Push source code or container images to a cluster and let Epinio handle the rest — all from within Rancher.

Key Features of the Current Release:

1. **Multi-Instance Management:** Discover and manage multiple Epinio instances across your downstream Rancher clusters from a single pane of glass. Switch between environments, monitor instance health, and view per-cluster details without leaving Rancher.
2. **One-Click Epinio Installer:** Deploy Epinio onto any Rancher-managed cluster through a guided installer that handles Helm chart deployment, ingress configuration, and required dependencies — no CLI setup or manual values files needed.
3. **Full Epinio UI Integration:** Use Epinio natively inside Rancher — manage applications, namespaces, configurations, services, and routes, stage from source via Cloud Native Buildpacks, and inspect deployment logs without context-switching to a separate dashboard.

## Prerequisites

1. Ensure you have access to an admin user.
2. Downstream clusters must meet Epinio's [system requirements](https://docs.epinio.io/installation/requirements) (cert-manager, an ingress controller, and S3-compatible storage for staging).

## Support

For support, please open an issue in this repository or visit the [Epinio community](https://github.com/epinio/epinio/discussions).

## GitHub Repository

<https://github.com/epinio/ui>
