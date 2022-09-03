```
Deploy a pod named nginx-448839 using the nginx:alpine image.
Once done, click on the Next Question button in the top right corner of this panel. You may navigate back and forth freely between all questions. Once done with all questions, click on End Exam. Your work will be validated at the end and score shown. Good Luck!
Name: nginx-448839
Image: nginx:alpine
```
    > k run nginx-448839 --image=nginx:alpine
```
Create a namespace named apx-z993845
```
    > k create namespace apx-z993845
```
Deploy a messaging pod using the redis:alpine image with the labels set to tier=msg.
```
    > k run messaging --image=redis:alpine
    > kubectl label pods messaging tier=msg

```
A replicaset rs-d33393 is created. However the pods are not coming up. Identify and fix the issue.
Once fixed, ensure the ReplicaSet has 4 Ready replicas.
• Replicas: 4
```
    > k get replicasets.apps rs-d33393 -o yaml > replica.yaml
    > fix image on template
    >  k delete replicasets.apps rs-d33393
    >  k apply -f replica.yaml 
```
Create a service messaging-service to expose the redis deployment in the marketing namespace within the cluster on port 6379.
Use imperative commands
• Service: messaging-service
• Port: 6379
• Use the right type of Service
Use the right labels
```
    > k expose deployment redis --port=6379 --name messaging-service -n marketing
```
Update the environment variable on the pod webapp-color to use a green background.
• Pod Name: webapp-color
• Label Name: webapp-color
Env: APP_COLOR=green
```
    > k get pod webapp-color -o yaml > pod.yaml
    > edit template
```
Create a new ConfigMap named cm-3392845. Use the spec given on the below.
• ConfigName Name: cm-3392845
• Data: DB_NAME=SQL3322
• Data: DB_HOST=sql322.mycompany.com
• Data: DB_PORT=3306
```
    ```    
    apiVersion: v1
    kind: ConfigMap
    metadata:
      name: cm-3392845
    data:
     DB_NAME: "SQL3322"
     DB_HOST: "sql322.mycompany.com"
     DB_PORT: "3306"
    ```
```
Create a new Secret named db-secret-xxdf with the data given (on the below).
• Secret Name: db-secret-xxdf
• Secret 1: DB_Host=sql01
• Secret 2: DB_User=root
• Secret 3: DB_Password=password123
```
    > k create secret generic db-secret-xxdf  --from-literal=DB_Host=sql01 --from-literal=DB_User=root --from-literal=DB_Password=password123
```
Export the logs of the e-com-1123 pod to the file /opt/outputs/e-com-1123.logs
It is in a different namespace. Identify the namespace first.
```
    >  k get pods --all-namespaces | grep e-com-1123
    >  k -n e-commerce describe pod e-com-1123 
    >  k -n e-commerce logs  e-com-1123 > /opt/outputs/e-com-1123.logs

    


