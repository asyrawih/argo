# Kubernetes Project with Kustomize

This project contains Kubernetes manifests and Kustomize configurations for deploying to different environments: staging, test, and production.

## Project Structure

```
kustomize/
├── base/              # Base Kubernetes manifests
├── overlays/          # Environment-specific overlays
│   ├── staging/
│   ├── test/
│   └── production/
└── README.md
```

## Usage

To build and deploy to a specific environment:

```bash
# Build kustomize for environment
kustomize build overlays/<environment>

# Deploy to environment
kubectl apply -k overlays/<environment>
```

Where <environment> can be one of: staging, test, or production
