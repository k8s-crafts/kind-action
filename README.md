# Kind Action

[![](https://github.com/k8s-crafts/kind-action/workflows/Test/badge.svg?branch=main)](https://github.com/k8s-crafts/kind-action/actions)

A GitHub Action for Kubernetes IN Docker - local clusters for testing Kubernetes using [kubernetes-sigs/kind](https://kind.sigs.k8s.io/).

## Usage

### Pre-requisites

Create a workflow YAML file in your `.github/workflows` directory. An [example workflow](#example-workflow) is available below.
For more information, reference the GitHub Help Documentation for [Creating a workflow file](https://help.github.com/en/articles/configuring-a-workflow#creating-a-workflow-file).

### Inputs

For more information on inputs, see the [API Documentation](https://developer.github.com/v3/repos/releases/#input)

- `version`: The kind version to use (default: `v0.21.0`)
- `config`: The path to the kind config file
- `node_image`: The Docker image for the cluster nodes
- `cluster_name`: The name of the cluster to create (default: `chart-testing`)
- `wait`: The duration to wait for the control plane to become ready (default: `60s`)
- `verbosity`: info log verbosity, higher value produces more output
- `kubectl_version`: The kubectl version to use (default: `v1.28.6`)
- `install_only`: Skips cluster creation, only install kind (default: `false`)
- `ignore_failed_clean`: Whether to ignore the post delete cluster action failing (default: `false`)

### Example Workflow

Create a workflow (eg: `.github/workflows/create-cluster.yaml`):

```yaml
name: Create Cluster

on: pull_request

jobs:
  create-cluster:
    runs-on: ubuntu-latest
    steps:
      - name: Create k8s Kind Cluster
        uses: k8s-crafts/kind-action@v1
```

This uses [@k8s-crafts/kind-action](https://github.com/k8s-crafts/kind-action) GitHub Action to spin up a [kind](https://kind.sigs.k8s.io/) Kubernetes cluster on every Pull Request.

## Code of conduct

Participation is governed by the [Code of Conduct](CODE_OF_CONDUCT.md).

## Credits

This action is based on [@helm/kind-action](https://github.com/helm/kind-action), maintained by the Helm community.
