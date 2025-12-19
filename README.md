# GitHub Actions Workflows

[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?logo=github-actions&logoColor=white)](https://github.com/features/actions)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Reusable GitHub Actions workflows for CI/CD pipelines. Includes workflows for Docker, Kubernetes, Terraform, and multi-language builds.

## Available Workflows

| Workflow | Description |
|----------|-------------|
| docker-build-push.yml | Build and push Docker images |
| terraform-plan-apply.yml | Terraform plan and apply |
| kubernetes-deploy.yml | Deploy to Kubernetes with Helm |
| node-ci.yml | Node.js CI with testing |
| python-ci.yml | Python CI with testing |
| java-ci.yml | Java/Maven CI with testing |
| security-scan.yml | Security scanning pipeline |

## Usage

### Copy Workflows

Copy the desired workflow files to your repository's `.github/workflows/` directory.

### Reusable Workflows

Use reusable workflows with `workflow_call`:

```yaml
name: CI/CD Pipeline
on:
  push:
    branches: [main]

jobs:
  build:
    uses: ashwathstephen/github-actions-workflows/.github/workflows/docker-build-push.yml@main
    with:
      image-name: my-app
      dockerfile: Dockerfile
    secrets:
      registry-username: ${{ secrets.DOCKER_USERNAME }}
      registry-password: ${{ secrets.DOCKER_PASSWORD }}
```

## Workflow Examples

### Docker Build and Push

```yaml
uses: ./.github/workflows/docker-build-push.yml
with:
  image-name: my-app
  registry: ghcr.io
  push: true
```

### Terraform Plan/Apply

```yaml
uses: ./.github/workflows/terraform-plan-apply.yml
with:
  working-directory: ./infrastructure
  environment: production
```

### Kubernetes Deploy

```yaml
uses: ./.github/workflows/kubernetes-deploy.yml
with:
  cluster-name: production
  namespace: my-app
  helm-chart: ./charts/my-app
```

## Author

Ashwath Abraham Stephen
Senior DevOps Engineer | [LinkedIn](https://linkedin.com/in/ashwathstephen) | [GitHub](https://github.com/ashwathstephen)

## License

MIT License - see [LICENSE](LICENSE) for details.

