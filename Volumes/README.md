# Kubernetes volumes vs persistent volumes

Volumes ≠ Persistent Volumes

Volumes and Persistent Volumes are related, but very different!

Volumes:

- appear in Pod specifications
- do not exist as API resources (cannot do kubectl get volumes)

Persistent Volumes:

- are API resources (can do kubectl get persistentvolumes)

- correspond to concrete volumes (e.g. on a SAN, EBS, etc.)

- cannot be associated with a Pod directly (they need a Persistent Volume Claim)
