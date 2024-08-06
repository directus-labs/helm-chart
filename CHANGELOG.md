# Change Log

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/)

## STAGED

### Added

- Options to add extra volume mount to the deployment (e.g. mount config maps/secrets as volume)

## [[directus-1.0.0]](https://github.com/directus-labs/helm-chart/releases/tag/directus-1.0.0) - 2024-07-31

**Breaking change**

Reworked environment variable setting and injection.

### Added

- Move sensetive values to the `secret` k8s resource
- Move not-sensetive variables to the `configmap` k8s resource
- Inject variables from `configmap` and `secrets` to the application pods

[Link to the list with all changes included in the release](https://github.com/directus-labs/helm-chart/compare/directus-0.4.0...directus-1.0.0)

