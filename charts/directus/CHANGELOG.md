# Change Log

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/)

## [1.0.0] - 2024-07-31

**Breaking change**

Reworked environment variable setting and injection.

### Added

- Move sensetive values to the `secret` k8s resource
- Move not-sensetive variables to the `configmap` k8s resource
- Inject variables from `configmap` and `secrets` to the application pods
