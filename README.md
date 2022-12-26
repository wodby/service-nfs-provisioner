# NFS Ganesha service

## Update

- remove volume and volume mount from statefulset
- make sure `StatefulSet` and not `Deployment`
- replace `app` label with `name`
- update names to `{{.name}}` for namespace-wide entities and to `{{.namespace}}-{{.name}}` for cluster-wide entities
