# Upgrading

## Upgrading to Directus 12 (chart 2.1.0)

Chart `2.1.0` bumps the bundled Directus app version from `11.x` to **12.0.2**. Directus 12
is a major release with several behavior changes that can affect a self-hosted Kubernetes
deployment. Read the official
[Directus 12 breaking changes](https://directus.com/docs/releases/breaking-changes/version-12)
in full; the items below are the ones most likely to bite a chart user.

### Health-check endpoint now requires authentication

In v12 the `/server/health` endpoint returns `403 FORBIDDEN` to unauthenticated requests
(see [directus/directus#27160](https://github.com/directus/directus/pull/27160)). The public,
no-auth liveness endpoint is `/server/ping`, which returns `pong`.

- **The chart's own probes are unaffected** — the `livenessProbe`/`readinessProbe` defaults
  hit `/` (a redirect, which counts as success), not `/server/health`.
- **If you front the service with a load balancer or ingress whose health check targets
  `/server/health`** (e.g. an AWS ALB `healthcheck-path` annotation), switch it to
  `/server/ping`, or it will mark targets unhealthy after the upgrade.

You can also disable the health endpoint entirely (`HEALTHCHECK_ENABLED=false`) or scope its
checks (`HEALTHCHECK_SERVICES`) via `extraEnvVars` if you don't use it.

### `IP_TRUST_PROXY` default changed from `true` to `false`

Directus 12 ships `IP_TRUST_PROXY=false` by default. When this chart's ingress is enabled
with `enableTLS: true`, `PUBLIC_URL` is `https://…` and Directus expects requests to be
secure. Behind a TLS-terminating proxy/load balancer the backend hop is plain HTTP, and
Directus relies on the proxy's `X-Forwarded-Proto` header to know the original request was
HTTPS. With `IP_TRUST_PROXY=false` that header is no longer trusted, and API requests can be
rejected.

If you run behind a trusted reverse proxy or load balancer, restore the old behavior with
`extraEnvVars`:

```yaml
extraEnvVars:
  - name: IP_TRUST_PROXY
    value: "true"
```

`IP_TRUST_PROXY` maps to the Express `trust proxy` setting, so you can also scope it to a
hop count or a CIDR instead of a blanket `true`.

### License enforcement (SSO and other features)

Directus 12 enforces licensing. SSO and some other features now require a valid license, with
a 30-day grace period on upgrades. If your deployment configures SSO providers (e.g.
`AUTH_PROVIDERS`), make sure you have an appropriate license or those logins will stop working
after the grace period.
