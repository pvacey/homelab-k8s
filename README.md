# Homelab Kubernetes

GitOps-managed Kubernetes cluster using Flux.

## Architecture

This repo uses Flux for GitOps. Changes pushed to Git are automatically applied to the cluster.

```
Git Push → Flux detects change → Deploys to cluster
```

### CI/CD Flow

1. Push to monitored git branch → Tekton webhook triggered
2. Tekton builds image with Kaniko → pushes to Zot registry
3. Flux detects new image → updates deployment YAML → applies to cluster

## Apps

| App | Description |
|-----|-------------|
| **tekton** | CI/CD pipelines for automated container builds |
| **bingo** | Playing card bingo web app |
| **paseo-dev** | Remote dev environment with Paseo + Opencode |
| **annoying-noises** | Discord bot for Dota sound effects |
| **pondering-orb** | Full stack web application |
| **zot** | Local container registry |
| **cloudflared** | Cloudflare tunnel ingress |

## Directory Structure

```
.
├── apps/              # Application manifests
│   ├── tekton/        # CI/CD system
│   ├── bingo/         # App: bingo
│   ├── paseo-dev/     # Paseo + Opencode dev environment
│   ├── annoying-noises/
│   ├── pondering-orb/
│   ├── zot/           # Container registry
│   └── cloudflared/
└── clusters/
    └── primary/       # Cluster configuration
```

