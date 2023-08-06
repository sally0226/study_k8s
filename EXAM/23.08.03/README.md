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
kubectl get deployments daisy-deployment -n exam-daisy -o=custom-columns='DEPLOYMENT:metadata.name','CONTAINER_IMAGE:spec.template.spec.containers[*].image','READY_REPLICAS:spec.replicas','NAMESPACE:metadata.namespace'
```

`-o=custom-output='<header>:<json-path-expr>'`

# Exam 5
- 
```shell
kubectl create deployment nginx-deployment --image=nginx:1.16 --replicas=1 --namespace=exam-daisy
# deployment.apps/nginx-deployment created

kubectl describe deployment --namespace=exam-daisy nginx-deployment

kubectl set image deployment --namespace=exam-daisy nginx-deployment nginx=n
ginx:1.17 --record
# deployment.apps/nginx-deployment image updated
```

`--record` 옵션을 사용하면 변경사항을 annotation에 기록할 수 있다. (그치만 deprecated... 예정)

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