
![image](https://user-images.githubusercontent.com/65309085/175805437-48f13148-8090-408e-9942-c1b6fc116e84.png)



# DEPLOYMENT DEFINITION FILE .yml .yaml

apiVersion: apps/v1

kind: Deployment

metadata:

name: nginx-deployment

labels:

    app: nginx

spec:

replicas: 3

selector:

    matchLabels:

      app: nginx

template:

    metadata:

      labels:

        app: nginx

    spec:

      containers:

      - name: nginx

        image: nginx:1.14.2

        ports:

        - containerPort: 80

A Deployment named nginx-deployment is created, indicated by the .metadata.name field.

The Deployment creates three replicated Pods, indicated by the .spec.replicas field.

The .spec.selector field defines how the Deployment finds which Pods to manage. In this case, you select a label that is defined in the Pod template (app: nginx). However, more sophisticated selection rules are possible, as long as the Pod template itself satisfies the rule.

The template field contains the following sub-fields:

The Pods are labeled app: nginxusing the .metadata.labels field.
The Pod template's specification, or .template.spec field, indicates that the Pods run one container, nginx, which runs the nginx Docker Hub image at version 1.14.2.
Create one container and name it nginx using the .spec.template.spec.containers[0].name field.
