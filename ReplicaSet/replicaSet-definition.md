# ReplicaSet DEFINITION FILE .yml .yaml

apiVersion: apps/v1

kind: ReplicaSet

metadata:

name: frontend

labels:

    app: guestbook

    tier: frontend

spec:

# modify replicas according to your case

replicas: 3

selector:

    matchLabels:

# selects pods with the same label

      tier: frontend

template:

    metadata:

      labels:

# these labels will be applied to the pods created by the ReplicaSet

        tier: frontend

    spec:

      containers:

      - name: php-redis

        image: gcr.io/google_samples/gb-frontend:v3
