# Ganesha NFS provisioner service for Kubernetes on Wodby

Provide Ganesha NFS provisioner storage to Kubernetes applications managed by
Wodby.

This repository defines the Wodby service manifests and operational
configuration for Ganesha NFS provisioner.

- [Browse Wodby services](https://wodby.com/services)
- [Wodby service documentation](https://wodby.com/docs/2.0/services/)
- [Service manifest reference](https://wodby.com/docs/2.0/services/template/)

## Wodby stacks using this service

- [Drupal application stack](https://github.com/wodby/stack-drupal)
- [Laravel application stack](https://github.com/wodby/stack-laravel)
- [WordPress application stack](https://github.com/wodby/stack-wordpress)

## Service overview

| Property | Manifest configuration |
| --- | --- |
| Service name | `nfs-provisioner` |
| Type | Storage service |
| Versions | `6.5` by default; also available: `4` |
| Workloads | `main` (StatefulSet), primary; fixed replica count |
| Containers | `nfs` using `devxygmbh/nfs-server-provisioner` |
| Endpoints | `nfs`: TCP 2049 (main), UDP 2049, TCP 32803, UDP 32803, TCP 20048, UDP 20048, TCP 875, UDP 875, TCP 111, UDP 111, TCP 662, UDP 662 |
| Volumes | Data |
| Helm | chart `oci://registry-1.docker.io/wodby/nfs-provisioner`; version `0.3.2` |
| Operations | 1 import workflows, 1 backup workflows |

## Use this service

Use this service through [Drupal application stack](https://github.com/wodby/stack-drupal), [Laravel application stack](https://github.com/wodby/stack-laravel),
[WordPress application stack](https://github.com/wodby/stack-wordpress), or reference `nfs-provisioner` from a custom Wodby stack.

A service is a reusable component and does not deploy by itself. The stack
defines its links, settings, versions, resources, and relationship to the rest
of the application.

## Maintain a custom version

1. Fork this repository.
2. Edit the service manifest and referenced files.
3. Import the repository as a [Git-backed service](https://wodby.com/docs/2.0/services/create/#create-a-git-backed-service).
4. Reference the service from a stack manifest.

Keep service, workload, container, endpoint, link, volume, config, and
derivative names stable unless dependent stacks and app-level overrides are
updated at the same time.

Validate the manifests with:

```bash
wodby service validate-manifest service.yml --org <org-id>
```

See the [service manifest reference](https://wodby.com/docs/2.0/services/template/) and the [managed services index](https://github.com/wodby/services).
