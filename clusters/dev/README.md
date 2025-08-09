# Cluster dev

This kustomization aggregates Applications and namespaces for the dev cluster.

Apply from Argo CD root Application, or directly using kustomize/kubectl if needed.

Local build note: this package references resources outside this folder (sibling apps/ packages). The kustomize CLI requires a relaxed load restrictor for that. Use:

1) Preview manifests

	kustomize build --load-restrictor LoadRestrictionsNone .

2) Apply manifests

	kustomize build --load-restrictor LoadRestrictionsNone . | kubectl apply -f -

Argo CD uses a relaxed loader by default, so no change is needed there.
