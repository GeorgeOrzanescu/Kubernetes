## Kubernetes network policy lets administrators and developers enforce which network traffic is allowed using rules.

- using network policies, administrators can restrict network traffic to a specific set of pods.
- network policies can be used map out the flow of traffic in a network.

# Network policie definition file

apiVersion: networking.k8s.io/v1

kind: NetworkPolicy

metadata:

name: test-network-policy

namespace: default

spec:

podSelector:

    matchLabels:

      role: db

policyTypes:

    - Ingress

    - Egress

ingress:

    - from:

        - ipBlock:

            cidr: 172.17.0.0/16

            except:

              - 172.17.1.0/24

        - namespaceSelector:

            matchLabels:

              project: myproject

        - podSelector:

            matchLabels:

              role: frontend

      ports:

        - protocol: TCP

          port: 6379

egress:

    - to:

        - ipBlock:

            cidr: 10.0.0.0/24

      ports:

        - protocol: TCP

          port: 5978
