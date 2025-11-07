# Deploy Aerolab Cluster GitHub Action

This GitHub Action automatically **deploys a local Aerospike cluster** using **Aerolab** on the GitHub Actions runner.  
Useful for integration tests and CI pipelines.

---

## Features

- Installs Aerolab on the runner
- Deploys a Docker-backed Aerospike cluster
- Customizable **Aerospike version**, **node count**, and **cluster name**
- Outputs cluster info into the job summary
- Works on `ubuntu-latest` runners

---

## Inputs

| Name | Description | Default |
|------|-------------|---------|
| `aerospike_version` | Aerospike server version to deploy | `8.1.0.1` |
| `nodes` | Number of Aerospike nodes | `3` |
| `cluster_name` | Logical name for the cluster | `ce` |

All inputs are **optional**.

---

## 📌 Example Usage

Deploy a 3-node cluster using version `8.1.0.1`:

```yaml
name: Test with Aerolab Cluster

on: [push]

jobs:
  integration-tests:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Deploy Aerolab Cluster
        uses: gagan405/deploy-aerolab-cluster@v1
        with:
          aerospike_version: "8.1.0.1"
          nodes: 3
          cluster_name: "ci-test"

      - name: Run integration tests
        run: |
          # connect using localhost ports 3100, 3101, etc.
          go test ./...
```

Cluster info will appear in the GitHub Actions job summary.


# Disclaimer

This project is **not affiliated with, endorsed by, or supported by Aerospike Inc.**  
It is a community-driven tool intended to make Aerospike cluster testing easier in GitHub Actions.

For official Aerospike products, documentation, and support, please visit the [Aerospike website](https://www.aerospike.com/).


# License
MIT — free to use and modify.

