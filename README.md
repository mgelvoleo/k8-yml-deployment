# k8-yml-deployment
This the yml version of deployment 

## Make a deployment.yml open editor paste the yml

### Step 1: lunch your favaorite editory and create the following or paste the yml below
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: k8-web-hello
spec:
  selector:
    matchLabels:
      app: k8-web-hello
  template:
    metadata:
      labels:
        app: k8-web-hello
    spec:
      containers:
      - name: k8-web-hello
        image: mgelvoleo/kube101
        resources:
          limits:
            memory: "128Mi"
            cpu: "250m"
        ports:
        - containerPort: 5000

```

### Step 2: Save the file and type the command to execute the yml

```
Shell Command

$ kubectl apply -f deployment.yml
```

### Step 3: Check the deployment

```
Shell Command

$ kubectl get deploy
$ kubectl get pods
```

### Step 4: Update the deployment.yml by adding the replicas by 4 and save afterward

```
Editor

apiVersion: apps/v1
kind: Deployment
metadata:
  name: k8-web-hello
spec:
  replicas: 4
  selector:
    matchLabels:
      app: k8-web-hello
  template:
    metadata:
      labels:
        app: k8-web-hello
    spec:
      containers:
      - name: k8-web-hello
        image: mgelvoleo/kube101
        resources:
          limits:
            memory: "128Mi"
            cpu: "250m"
        ports:
        - containerPort: 5000

```

### Step 5: Reapply the change by applying the command below

```
Shell Command

$ kubectl apply -f deployment.yml

```
### Step 6: Check the replicas that create

```
Shell command
$ kubectl get pods
```

### Step 7: Create the service you can paste the yml format and the value given

```
Editor

apiVersion: v1
kind: Service
metadata:
  name: k8-web-hello
spec:
  type: LoadBalancer
  selector:
    app: k8-web-hello
  ports:
  - port: 5050
    targetPort: 5000


```

### Step 8: Apply the service.yml

```
Shell Command

$ kubectl apply -f service.yml
```


### Step 9: View the created services
```
Shell Command

$ kubectl get svc
```


### Step 10: Lunch the newly expose port of the service

```
Shell Command

$ minikube service k8-web-hello

```
