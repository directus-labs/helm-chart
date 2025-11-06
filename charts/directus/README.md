# directus

![Version: 2.0.7](https://img.shields.io/badge/Version-2.0.7-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 11.13.0](https://img.shields.io/badge/AppVersion-11.13.0-informational?style=flat-square)

A Helm chart for installing Directus on Kubernetes.
Directus is a real-time API and App dashboard for managing SQL database content.

**Homepage:** <https://directus.io/>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| mykhailo-sindieiev | <mykhailo_sindieiev@owasp.org> | <https://github.com/directus-labs/helm-chart> |

## Source Code

* <https://github.com/directus-labs/helm-chart/tree/master/charts/directus>
* <https://github.com/directus/directus>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| oci://registry-1.docker.io/bitnamicharts | mysql | ~14.0.3 |
| oci://registry-1.docker.io/bitnamicharts | postgresql | ~16.7.27 |
| oci://registry-1.docker.io/bitnamicharts | redis | ~23.2.6 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| adminEmail | string | `"directus-admin@example.com"` |  |
| affinity | object | `{}` |  |
| applicationSecretName | string | `"directus-application-secret"` |  |
| attachExistingSecrets | list | `[]` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| createApplicationSecret | bool | `true` | This setting enables the creation of `ADMIN_PASSWORD`, `KEY`, and `SECRET` variables in k8s secrets. If it is set to false, you MUST set these variables manually via existing secret resource and set its name below. |
| createMysqlSecret | bool | `true` | Create MySQL secret in Directus chart If set to enable, mysql secret with values of `mysql-root-password`, `mysql-replication-password` and `mysql-password` variables will be created. Please consult the official bitnami mysql values file - https://github.com/bitnami/charts/blob/main/bitnami/mysql/values.yaml#L152. If set to false, you MUST create a secret resource in k8s for mysql installation and set the correct value to the `existingSecret` in the mysql settings section. |
| createPostgresqlSecret | bool | `false` | Create PostgreSQL secret in Directus chart If set to enable, postgresql secret with values of `postgres-password`, `password`, and `replication-password` variables will be created. Please consult the official bitnami postgres values file - https://github.com/bitnami/charts/blob/main/bitnami/postgresql/values.yaml#L164. If set to false, you MUST create a secret resource in k8s for postgresql installation and set the correct value to the `existingSecret` in the postgresql settings setion. |
| databaseEngine | string | `"mysql"` | Database engine. Could be set to one value from the following list: `mysql`, `postgresql`. Please disable installations for other database engines in this chart. Please note if you use mariadb server, set `databaseEngine` to `mysql` value. Details are here - https://directus.io/docs/configuration/database. |
| extraEnvVars | list | `[]` |  |
| extraVolumeMounts | list | `[]` |  |
| extraVolumes | list | `[]` |  |
| fullnameOverride | string | `""` | Completely overrides Chart name |
| image.pullPolicy | string | `"IfNotPresent"` | Pull policy for docker image |
| image.repository | string | `"directus/directus"` | Directus image docker repository |
| image.tag | string | `""` | Overrides the image tag whose default is the chart appVersion. |
| imagePullSecrets | list | `[]` | Image Pull Secrets in k8s for docker image |
| ingress.annotations | object | `{}` | Ingress annotations. Usually used in cloud environments |
| ingress.className | string | `""` |  |
| ingress.enableTLS | bool | `true` | Enable TLS in PUBLIC_URL |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0] | object | `{"host":"chart-example.local","paths":[{"path":"/","pathType":"Prefix"}]}` | Hostname to expose. You should create CNAME DNS record with this hostname to redirect to ALB DNS name |
| ingress.tls | list | `[]` |  |
| initContainers | list | `[]` | Init Containers for Directus pod |
| livenessProbe.enabled | bool | `true` |  |
| livenessProbe.httpGet.path | string | `"/"` |  |
| livenessProbe.httpGet.port | string | `"http"` |  |
| mysql.auth.database | string | `"directus_mysql"` |  |
| mysql.auth.existingSecret | string | `"directus-mysql-secret"` |  |
| mysql.auth.username | string | `"directus_mysql"` |  |
| mysql.enableInstallation | bool | `true` | The switch to switch off the installation of the mysql. The rest of the settings are being used during the installation and for DB connection. Link to the values.yaml file in bitnami repo - https://github.com/bitnami/charts/blob/main/bitnami/mysql/values.yaml |
| mysql.global | object | `{"security":{"allowInsecureImages":true}}` | Global security settings for mysql image. Set to true to allow insecure images from bitnamilegacy repository |
| mysql.image | object | `{"registry":"docker.io","repository":"bitnamilegacy/mysql","tag":"9.4.0-debian-12-r1"}` | MySQL image settings |
| mysql.mysqlPort | string | `""` |  |
| mysql.mysqlURL | string | `""` |  |
| nameOverride | string | `""` | Helm name override in Chart.yaml. This name is being used for resource naming |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| postgresql.auth.database | string | `"directus_postgres"` |  |
| postgresql.auth.existingSecret | string | `"directus-postgresql-secret"` |  |
| postgresql.auth.username | string | `"directus_postgres"` |  |
| postgresql.enableInstallation | bool | `false` | The switch to switch off the installation of the postgresql. The rest of the settings are being used during the installation and for DB connection. Link to the values.yaml file in bitnami repo - https://github.com/bitnami/charts/blob/main/bitnami/postgresql/values.yaml |
| postgresql.global | object | `{"security":{"allowInsecureImages":true}}` | Global security settings for postgresql image. Set to true to allow insecure images from bitnamilegacy repository |
| postgresql.image | object | `{"registry":"docker.io","repository":"bitnamilegacy/postgresql","tag":"17.6.0-debian-12-r4"}` | PostgreSQL image settings |
| postgresql.postgresqlPort | string | `""` |  |
| postgresql.postgresqlURL | string | `""` |  |
| readinessProbe.enabled | bool | `true` |  |
| readinessProbe.httpGet.path | string | `"/"` |  |
| readinessProbe.httpGet.port | string | `"http"` |  |
| redis.auth.existingSecret | string | `""` | Existing secret name with Redis password |
| redis.auth.existingSecretPasswordKey | string | `""` | The key in the secret with password |
| redis.enabled | bool | `true` | Switch to enable Redis |
| redis.global | object | `{"security":{"allowInsecureImages":true}}` | Global security settings for redis image. Set to true to allow insecure images from bitnamilegacy repository |
| redis.image | object | `{"registry":"docker.io","repository":"bitnamilegacy/redis","tag":"8.2.1-debian-12-r0"}` | Redis image settings |
| redis.replica.replicaCount | int | `0` | Amount of Redis replicas |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.annotations | object | `{}` | Service annotations. Usually used in cloud environments |
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
| sidecars | list | `[]` | Sidecars for Directus pod |
| startupProbe.enabled | bool | `false` |  |
| startupProbe.httpGet.path | string | `"/"` |  |
| startupProbe.httpGet.port | string | `"http"` |  |
| tolerations | list | `[]` |  |
| updateStrategy | object | `{"type":"RollingUpdate"}` | Or: updateStrategy:   type: Recreate |

