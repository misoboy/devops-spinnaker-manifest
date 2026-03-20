# devops-spinnaker-manifest

> Kubernetes manifest samples for [Spinnaker](https://spinnaker.io) CD pipeline deployments.

[![Kubernetes](https://img.shields.io/badge/Kubernetes-manifest-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io)
[![Spinnaker](https://img.shields.io/badge/Spinnaker-CD-blue)](https://spinnaker.io)

## Overview

This repository contains Kubernetes manifest files designed to be used as deployment targets in a Spinnaker Continuous Delivery pipeline. The manifests demonstrate Spinnaker-specific annotations for traffic management and version history.

## Manifest Files

| File | Description |
|------|-------------|
| `spinnaker-sample-deploy.yaml` | ReplicaSet with Spinnaker traffic and version annotations |
| `spinnaker-sample-service.yaml` | Kubernetes Service for the sample app |
| `spinnaker-sample-ingress.yaml` | Ingress resource for external access |
| `spinnaker-sample-vs.yaml` | VirtualService (Istio) for traffic management |

## Key Spinnaker Annotations

```yaml
annotations:
  strategy.spinnaker.io/max-version-history: "3"   # Keep last 3 versions
  traffic.spinnaker.io/load-balancers: "[\"service sample-backend-api-service\"]"
```

## Usage

1. Deploy via Spinnaker pipeline pointing to this repository
2. Or apply directly with kubectl:

```bash
kubectl apply -f spinnaker-sample-deploy.yaml
kubectl apply -f spinnaker-sample-service.yaml
kubectl apply -f spinnaker-sample-ingress.yaml
```

## Related

- [devops-spinnaker-sample-app](https://github.com/misoboy/devops-spinnaker-sample-app) — The Spring Boot application deployed by these manifests

## License

MIT
