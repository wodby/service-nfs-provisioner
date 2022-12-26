# NFS Ganesha service

## Update

- remove volume and volume mount from statefulset
- make sure `StatefulSet` and not `Deployment`
- replace `app` label with `name`
- update names to `{{.Name}}` for namespace-wide entities and to `{{.Namespace}}-{{.Name}}` for cluster-wide entities
