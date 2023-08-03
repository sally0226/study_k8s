# Exam 1
```shell
kubectl get node -o json > daisy/json-daisy.json
```

# Exam 2
```shell
kubectl create ns exam-daisy
```

# Exam 3
```shell
kubectl create deployment daisy-deployment --image=nginx --replicas=2 --namespace=exam-daisy
```

# Exam 4
```shell
```

# Exam 5
- 
```shell
kubectl create deployment nginx-deployment --image=nginx:1.16 --replicas=1 --namespace=exam-daisy
# deployment.apps/nginx-deployment created

kubectl describe deployment --namespace=exam-daisy nginx-deployment
# Name:                   nginx-deployment
# Namespace:              exam-daisy
# CreationTimestamp:      Thu, 03 Aug 2023 18:08:06 +0900
# Labels:                 app=nginx-deployment
# Annotations:            deployment.kubernetes.io/revision: 1
# Selector:               app=nginx-deployment
# Replicas:               1 desired | 1 updated | 1 total | 1 available | 0 unavailable
# StrategyType:           RollingUpdate
# MinReadySeconds:        0
# RollingUpdateStrategy:  25% max unavailable, 25% max surge
# Pod Template:
#   Labels:  app=nginx-deployment
#   Containers:
#    nginx:
#     Image:        nginx:1.16
#     Port:         <none>
#     Host Port:    <none>
#     Environment:  <none>
#     Mounts:       <none>
#   Volumes:        <none>
# Conditions:
#   Type           Status  Reason
#   ----           ------  ------
#   Available      True    MinimumReplicasAvailable
#   Progressing    True    NewReplicaSetAvailable
# OldReplicaSets:  <none>
# NewReplicaSet:   nginx-deployment-66fff56987 (1/1 replicas created)
# Events:
#   Type    Reason             Age   From                   Message
#   ----    ------             ----  ----                   -------
#   Normal  ScalingReplicaSet  97s   deployment-controller  Scaled up replica set nginx-deployment-66fff56987 to 1

kubectl set image deployment --namespace=exam-daisy nginx-deployment nginx=n
ginx:1.17
# deployment.apps/nginx-deployment image updated

kubectl describe deployment --namespace=exam-daisy nginx-deployment
# Name:                   nginx-deployment
# Namespace:              exam-daisy
# CreationTimestamp:      Thu, 03 Aug 2023 18:08:06 +0900
# Labels:                 app=nginx-deployment
# Annotations:            deployment.kubernetes.io/revision: 2
# Selector:               app=nginx-deployment
# Replicas:               1 desired | 1 updated | 1 total | 1 available | 0 unavailable
# StrategyType:           RollingUpdate
# MinReadySeconds:        0
# RollingUpdateStrategy:  25% max unavailable, 25% max surge
# Pod Template:
#   Labels:  app=nginx-deployment
#   Containers:
#    nginx:
#     Image:        nginx:1.17
#     Port:         <none>
#     Host Port:    <none>
#     Environment:  <none>
#     Mounts:       <none>
#   Volumes:        <none>
# Conditions:
#   Type           Status  Reason
#   ----           ------  ------
#   Available      True    MinimumReplicasAvailable
#   Progressing    True    NewReplicaSetAvailable
# OldReplicaSets:  <none>
# NewReplicaSet:   nginx-deployment-7445c994b8 (1/1 replicas created)
# Events:
#   Type    Reason             Age    From                   Message
#   ----    ------             ----   ----                   -------
#   Normal  ScalingReplicaSet  4m27s  deployment-controller  Scaled up replica set nginx-deployment-66fff56987 to 1
#   Normal  ScalingReplicaSet  5s     deployment-controller  Scaled up replica set nginx-deployment-7445c994b8 to 1
#   Normal  ScalingReplicaSet  3s     deployment-controller  Scaled down replica set nginx-deployment-66fff56987 to 0 from 1
```

# Exam 6
```shell
kubectl create -f exam_6.yaml 
# service/web-application created

kubectl get service web-application
# NAME              TYPE       CLUSTER-IP    EXTERNAL-IP   PORT(S)          AGE
# web-application   NodePort   10.36.9.130   <none>        8080:30089/TCP   47s

```

# Exam 7
```shell
kubectl expose service web-application --type=LoadBalancer --name=daisy-service
# service/daisy-service exposed

kubectl get service 
# NAME                     TYPE           CLUSTER-IP    EXTERNAL-IP    PORT(S)           AGE
# daisy-service            LoadBalancer   10.36.2.227   35.226.80.1    8080:31206/TCP    59s
```

# Exam 8
```shell
kubectl create -f exam_8.yaml 
# deployment.apps/daisy-deployment created

kubectl scale deployment/daisy-deployment --replicas=1
# deployment.apps/daisy-deployment scaled

kubectl create configmap daisy-exam8-config --from-literal=hello=world --from-literal=drink=good --from-literal=happy=work
# configmap/daisy-exam8-config created


```

# Exam 9
```shell
```