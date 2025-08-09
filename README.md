# Observability GitOps with Argo CD

This repository is a GitOps scaffold to deploy an observability stack and a sample app via Argo CD using an App-of-Apps pattern.

Components:
- Argo CD (bootstrap manifests)
- Traefik (ingress controller)
- VictoriaMetrics (metrics storage)
- VictoriaLogs (logs storage)
- OpenTelemetry Collector (telemetry pipeline)
- Jaeger Operator (installs CRDs and manages Jaeger)
- Jaeger (all-in-one, in-memory storage)
- Sample App (Kustomize-based demo app)

## Structure
- `infra/argocd/`: Argo CD installation and the root ApplicationSet (app-of-apps)
- `apps/*`: Kustomize overlays and/or Helm chart references for each component
- `clusters/`: Per-cluster root applications for multi-cluster GitOps

## Quick start
1. Install Argo CD in your cluster.
2. Apply `infra/argocd/bootstrap.yaml` to install Argo CD + the root Application.
3. Access Argo CD UI and sync the root app.

## Requirements
- Kubernetes 1.24+
- kubectl
- Argo CD

## Notes
- All apps are configured using either Kustomize or Helm with "sourceRef" pointing to public charts.
- Adjust values in each `values.yaml` as needed for your environment.
