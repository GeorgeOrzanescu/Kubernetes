
# POD DEFINITION FILE .yml .yaml

apiVersion: v1

kind: Pod

metadata:

&ensp;name: nginx

spec:

  containers:

  - name: nginx

    image: nginx:1.14.2

    ports:

    - containerPort: 80
