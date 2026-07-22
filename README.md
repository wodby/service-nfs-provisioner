# Ganesha NFS provisioner service for Wodby

Use Ganesha NFS provisioner as a reusable component in applications managed by
Wodby. This repository contains the service manifests and referenced files used
by the public Ganesha NFS provisioner service in the Wodby catalog.

- [Ganesha NFS provisioner service in the Wodby catalog](https://wodby.com/services/nfs-provisioner)
- [Wodby service documentation](https://wodby.com/docs/2.0/services/)
- [Service manifest reference](https://wodby.com/docs/2.0/services/template/)

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

A service is a reusable component and does not deploy by itself. Add the public
catalog service to a stack, configure its required links and settings, publish
the stack, and then create or upgrade an app instance.

To maintain your own version of this service:

1. Fork this repository.
2. Edit the service manifest and any files it references.
3. Import the repository as a
   [Git-backed service](https://wodby.com/docs/2.0/services/create/#create-a-git-backed-service).
4. Reference `nfs-provisioner` from your stack manifest.

Wodby imports the manifest and referenced files from the selected Git branch or
tag and creates a new service revision when the Git-backed service is updated.

## Customize the service

Common changes include adjusting versions, images, Helm chart settings, build
inputs, environment variables, links, storage, resources, and operational
workflows supported by the manifest.

Keep service, workload, container, endpoint, link, volume, config, and
derivative names stable unless dependent stacks and app-level overrides are
updated at the same time. These names are part of the contract consumed by
downstream manifests.

Validate customized manifests with the Wodby CLI before importing them:

```bash
wodby service validate-manifest service.yml --org <org-id>
```

See the [service manifest reference](https://wodby.com/docs/2.0/services/template/)
for every supported field and the [managed services
index](https://github.com/wodby/services) for more service examples.
