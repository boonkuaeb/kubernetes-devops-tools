# Start minikube
```
minikube start --cpus 4 --memory 12288

```

# Check minikube ip
```
minikube ip
```
# Open minikube dashboard
```
minikube dashbord
```


# Create NFS server ( optional )

```
kubectl apply -f nfs-deployment/nfs-definition.yml
```

# Create namespace for `devops-tools`
```
kubectl create namespace devops-tools
```

# Create `PersistentVolume` for jenkins

please update your nfs information on line` server: 10.104.80.107 `

```
kubectl apply -f pv/jenkins-pv.yml
```

# Create `PersistentVolumeClaim` for jenkins
 We decide to set jenkins Claim in `devops-tools` namespace
```
kubectl apply -f pvc/jenkins-pvc.yml -n devops-tools
```

# Deploy jenkins-service to `devops-tools` namespace

```
kubectl apply -f deployment/jenkins-definition.yml -n devops-tools
```


# Check port 
```
kubectl get svc -n devops-tools
```


# Run all service 
please update your nfs information on line` server: 10.104.80.107 `

```
kubectl apply -f pv/

kubectl apply -f pvc/ -n devops-tools

kubectl apply -f deployment/ -n devops-tools
``` 
