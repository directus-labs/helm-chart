# directus

![Version: 1.0.3](https://img.shields.io/badge/Version-1.0.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 11.1.1](https://img.shields.io/badge/AppVersion-11.1.1-informational?style=flat-square)

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
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| extraEnvVars | list | `[]` |  |
| extraVolumeMounts | list | `[]` |  |
| extraVolumes | list | `[]` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"directus/directus"` |  |
| image.tag | string | `"11.1.1"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` |  |
| ingress.className | string | `""` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| ingress.tls | list | `[]` |  |
| livenessProbe.enabled | bool | `true` |  |
| livenessProbe.httpGet.path | string | `"/"` |  |
| livenessProbe.httpGet.port | string | `"http"` |  |
| mariadb.auth.createSecrets | bool | `true` |  |
| mariadb.auth.database | string | `"directus"` |  |
| mariadb.auth.existingSecret | string | `"directus-secret"` |  |
| mariadb.auth.username | string | `"directus"` |  |
| mariadb.enableInstallation | bool | `true` |  |
| mariadb.mariadbURL | string | `""` |  |
| nameOverride | string | `""` |  |
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
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| sidecar.command[0] | string | `"/bin/sh"` |  |
| sidecar.command[1] | string | `"-c"` |  |
| sidecar.command[2] | string | `"sleep 3600;"` |  |
| sidecar.enabled | bool | `false` |  |
| sidecar.pullPolicy | string | `"Always"` |  |
| sidecar.repository | string | `"busybox"` |  |
| sidecar.securityContext | object | `{}` |  |
| sidecar.tag | string | `"latest"` |  |
| startupProbe.enabled | bool | `false` |  |
| startupProbe.httpGet.path | string | `"/"` |  |
| startupProbe.httpGet.port | string | `"http"` |  |
| tolerations | list | `[]` |  |

