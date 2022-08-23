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

### Update the deployment.yml by adding the replicas

```
Editor

apiVersion: apps/v1
kind: Deployment
metadata:
  name: k8-web-hello
spec:
  ####replicas: 1
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
