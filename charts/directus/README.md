# Directus Helm Chart

Installs [Directus](https://directus.io/), the open data platform for headless content management via Helm Chart.

## Install
To install Directus

```
$ git clone git@github.com:directus/directus.git
$ cd charts/directus

$ helm dep up
$ helm install directus .
```

## Uninstall
To uninstall and delete Directus Helm release

```
$ helm delete directus 
```

## Configuration

| Parameter                    | Description                                                                                                                           | Default Value             |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| `replicaCount`               | Number of replicas                                                                                                                    | 1                         |
| `image.repository`           | Image name                                                                                                                            | `directus/directus`       |
| `image.pullPolicy`           | Image pull policy                                                                                                                     | `IfNotPresent`            |
| `image.pullSecrets`          | Image pull secrets                                                                                                                    | `{}`                      |
| `nameOverride`               | Replaces the name of the chart                                                                                                        | --                        |
| `fullnameOverride`           | Replaces the fully qualified app name                                                                                                 | --                        |
| `serviceAccount.create`      | Create service account                                                                                                                | `true`                    |
| `serviceAccount.annotations` | ServiceAccount annotations                                                                                                            | `{}`                      |
| `serviceAccount.name`        | Service account name to use, when empty will be set to created account if serviceAccount.create is set else to default                | ``                        |
| `podAnnotations`             | Pod annotations                                                                                                                       | `{}`                      |
| `podSecurityContext`         | Pod securityContext                                                                                                                   | `{}`                      |
| `securityContext`            | Deployment securityContext                                                                                                            | `{}`                      |
| `service.type`               | Kubernetes service type                                                                                                               | `ClusterIP`               |
| `service.port`               | Kubernetes port where service is exposed                                                                                              | `80`                      |
| `ingress.enabled`            | Enables Ingress                                                                                                                       | `false`                   |
| `ingress.annotations`        | Ingress annotations                                                                                                                   | `{}`                      |
| `ingress.hosts`              | Ingress extra paths to prepend to every host configuration                                                                            | `["chart-example.local"]` |
| `ingress.tls`                | Ingress TLS configuration                                                                                                             | `[]`                      |
| `resources`                  | CPU/Memory resource requests/limits                                                                                                   | `{}`                      |
| `autoscaling.enabled`        | Enables Autoscaling                                                                                                                   | `false`                   |
| `autoscaling.minReplicas`    | Set minimum number of replicas. Only applies when `autoscaling.enabled` is `true`.                                                    | `1`                       |
| `autoscaling.maxReplicas`    | Set maximum number of replicas Only applies when `autoscaling.enabled` is `true`.                                                     | `100`                     |
| `nodeSelector`               | Node labels for pod assignment                                                                                                        | `{}`                      |
| `tolerations`                | List of node taints to tolerate                                                                                                       | `[]`                      |
| `affinity`                   | Node/Pod affinities                                                                                                                   | `{}`                      |
| `extraEnvVars`               | Adds extra environment variables.  Refer to [Directus Docs](https://docs.directus.io/configuration/config-options/) for more details. | `{}`                      |

## To Do

1. Test on a couple of clusters
2. Add a values.production.yaml file that deploys an HA setup
3. Publish chart
