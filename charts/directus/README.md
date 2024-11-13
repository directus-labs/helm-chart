# directus

![Version: 1.0.5](https://img.shields.io/badge/Version-1.0.5-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 11.2.1](https://img.shields.io/badge/AppVersion-11.2.1-informational?style=flat-square)

A Helm chart for installing Directus on Kubernetes.
Directus is a real-time API and App dashboard for managing SQL database content.

**Homepage:** <https://directus.io/>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| mikesindieiev | <sindieiev@protonmail.ch> | <https://github.com/directus-labs/helm-chart> |

## Source Code

* <https://github.com/directus-labs/helm-chart/tree/master/charts/directus>
* <https://github.com/directus/directus>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | mariadb | ~18.0.2 |
| https://charts.bitnami.com/bitnami | redis | ~19.6.4 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| adminEmail | string | `"admin@example.com"` |  |
| affinity | object | `{}` |  |
| attachExistingSecrets | list | `[]` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| extraEnvVars | list | `[]` |  |
| extraVolumeMounts | list | `[]` |  |
| extraVolumes | list | `[]` |  |
| fullnameOverride | string | `""` | Completely overrides Chart name |
| image.pullPolicy | string | `"IfNotPresent"` | Pull policy for docker image |
| image.repository | string | `"directus/directus"` | Directus image docker repository |
| image.tag | string | `"11.1.2"` | Overrides the image tag whose default is the chart appVersion. |
| imagePullSecrets | list | `[]` | Image Pull Secrets in k8s for docker image |
| ingress.annotations | object | `{}` | Ingress annotations. Usually used in cloud environments |
| ingress.className | string | `""` |  |
| ingress.enableTLS | bool | `true` | Enable TLS in PUBLIC_URL |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0] | object | `{"host":"chart-example.local","paths":[{"path":"/","pathType":"Prefix"}]}` | Hostname to expose. You should create CNAME DNS record with this hostname to redirect to ALB DNS name |
| ingress.tls | list | `[]` |  |
| livenessProbe.enabled | bool | `true` |  |
| livenessProbe.httpGet.path | string | `"/"` |  |
| livenessProbe.httpGet.port | string | `"http"` |  |
| mariadb.auth.createSecrets | bool | `true` | If you want to use your own mariadb secret, set `createSecrets` to false and update `mariadb.auth.existingSecret` field with the correct secret name |
| mariadb.auth.database | string | `"directus"` | Directus datatbase name |
| mariadb.auth.existingSecret | string | `"directus-secret"` | The secret has to contain the following keys `mariadb-root-password`, `mariadb-replication-password`, `mariadb-password`, `ADMIN_PASSWORD`, `KEY`, `SECRET` |
| mariadb.auth.username | string | `"directus"` | The user that is being used to connect to database |
| mariadb.enableInstallation | bool | `true` | The switch to switch off the installation of the mariadb, the rest of the settings are being used during the installation |
| mariadb.mariadbURL | string | `""` | The URL to the mariadb instance, otherwise leave it empty to use one that installed in the cluster |
| nameOverride | string | `""` | Helm name override in Chart.yaml. This name is being used for resource naming |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| readinessProbe.enabled | bool | `true` |  |
| readinessProbe.httpGet.path | string | `"/"` |  |
| readinessProbe.httpGet.port | string | `"http"` |  |
| redis.enabled | bool | `true` |  |
| redis.replica.replicaCount | int | `0` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| sidecar.command | list | `["/bin/sh","-c","sleep 3600;"]` | Command to run in sidecar docker image |
| sidecar.enabled | bool | `false` | Sidecars for Directus pod |
| sidecar.pullPolicy | string | `"Always"` |  |
| sidecar.repository | string | `"busybox"` |  |
| sidecar.securityContext | object | `{}` |  |
| sidecar.tag | string | `"latest"` |  |
| startupProbe.enabled | bool | `false` |  |
| startupProbe.httpGet.path | string | `"/"` |  |
| startupProbe.httpGet.port | string | `"http"` |  |
| tolerations | list | `[]` |  |

