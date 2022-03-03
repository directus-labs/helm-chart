# Directus Helm Chart

Installs [Directus](https://directus.io/), the open data platform for headless content management via Helm Chart.

## Install
To install Directus, use the following commands.

1. Add Directus Helm repository:

    ```sh
    helm repo add directus https://directus-community.github.io/helm-chart/
    helm repo update
    ```

2. Install Helm Chart with `directus-release` release name:
    ```sh
    helm install directus-release directus/directus
    ```

## Uninstall
To uninstall and delete Directus Helm release:

```sh
helm delete directus-release 
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
| `mariadb.enabled`            | Deploys MariaDB server                                                                                                                | `true`                    |
| `redis.enabled`              | Deploys Redis server                                                                                                                  | `true`                    |

### External Database

If you want to use an external DB, you need to disable MariaDB by adding `mariadb.enabled: false` and add the necessary Environment Variables according to [Directus Documentation](https://docs.directus.io/configuration/config-options/#database).

These variables can be added by using the following values:

```
extraEnvVars:
  - name: DB_CLIENT
    value: mysql
  ...

```

### External File Storage

By default, Directus stores the uploaded files on the container disk.  Thus the data will be lost when the pod is restarted.  You need to configure Directus to use an external storage adapter such as S3, Google Storage and Azure.  This can be done by adding the necessary Environment Variables as documented in [Directus Documentation](https://docs.directus.io/configuration/config-options/#file-storage).

These variables can be added by using the following values:

```
extraEnvVars:
  - name: STORAGE_LOCATIONS
    value: amazon
  - name: STORAGE_AMAZON_DRIVER
    value: s3
  ...

```

## To Do

1. Test on a couple of clusters
2. Add a values.production.yaml file that deploys an HA setup
