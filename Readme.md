# Helm Template 001

This is a generic Helm chart template designed for deploying applications to Kubernetes. It includes standard resources like Deployments, Services, and Ingress.

## Prerequisites

- Kubernetes 1.16+
- Helm 3.0+

## Installing the Chart

To install the chart with the release name `my-release`:

1. Add the repository:
    ```bash
    helm repo add helm-template-001 https://code360Pro.github.io/helm-template-001
    helm repo update
    ```

2. Install the chart:
    ```bash
    helm install my-release helm-template-001/helm-template-001
    ```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
helm delete my-release
```

## Configuration

The following table lists the configurable parameters of the helm-template-001 chart and their default values.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `replicaCount` | int | `1` | Number of replicas to deploy |
| `image.repository` | string | `"nginx"` | Image repository |
| `image.tag` | string | `""` | Image tag (defaults to appVersion) |
| `image.pullPolicy` | string | `"IfNotPresent"` | Image pull policy |
| `serviceAccount.create` | bool | `true` | Specifies whether a service account should be created |
| `serviceAccount.name` | string | `""` | The name of the service account to use |
| `application.port` | int | `8080` | The container port for the application |
| `service.type` | string | `"ClusterIP"` | Kubernetes Service type |
| `service.port` | int | `80` | Kubernetes Service port |
| `ingress.enabled` | bool | `false` | Enable Ingress resource |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example:

```bash
helm install my-release helm-template-001/helm-template-001 --set replicaCount=2
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example:

```bash
helm install my-release helm-template-001/helm-template-001 -f values.yaml
```

## Development

This chart is configured to automatically publish releases to GitHub Pages using GitHub Actions.

1.  Bump the version in `Chart.yaml`.
2.  Push changes to the `main` branch.
3.  The GitHub Action will package the chart and update the `gh-pages` branch.
