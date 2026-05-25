# Argo CD Apps of Apps

This repository stores Argo CD application definitions and environment-specific Helm values for the `nodeapp` chart.

## Layout

```text
.
├── argocd-apps/
│   └── applicationset.yaml
├── development/
│   └── values.yaml
└── production/
    └── values.yaml
```

## Bootstrap

Apply the ApplicationSet once to the cluster where Argo CD is installed:

```sh
kubectl apply -f argocd-apps/applicationset.yaml
```

The ApplicationSet creates one Argo CD Application per environment:

- `nodeapp-development` deploys to `nodeapp-development`
- `nodeapp-production` deploys to `nodeapp-production`

The Helm chart is loaded from `https://github.com/sajilpb/Helm.git` at `charts/nodeapp`, and values are loaded from this repository under `<environment>/values.yaml`.
