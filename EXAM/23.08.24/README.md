# EXAM2 (23.08.24)

1. Create an nginx pod and set an env value as 'var1=val1'. Check the env value existence within the pod. 

```
kubectl create -f p1.yaml
kubectl exec nginx  nginx -- env
```

2. Create an nginx pod and exec into containers and verify that main.txt exist.

```
kubectl exec nginx -- sudo echo 'hello' >> /main.txt
kubectl exec nginx -- ls
```

3. Create a Pod with main container busybox and which executes this "while true; do echo `Hi I am from Main container' >> /var/log/index.html; sleep 5; done" and with sidecar container with nginx image which exposes on port 80. Use emptyDir Volume and mount this volume on path /var/log for busybox and on path /usr/share/nginx/html for nginx container. Verify both containers are running.

```
kubectl create -f p3.yaml
```

4. Check logs of each container that "busyboxpod-{1,2,3}"

```
kubectl logs p5-daisy busybox1
kubectl logs p5-daisy busybox2
kubectl logs p5-daisy busybox3
```

5. Create a Pod with three busy box containers with commands "ls; sleep 3600;", "echo Hello World; sleep 3600;" and "echo this is the third container; sleep 3600" respectively and check the status

```
kubectl create -f p5.yaml
```

6. Create a redis pod, and have it use a non-persistent storage Note: In exam, you will have access to kubernetes.io site, Refer : https://kubernetes.io/docs/tasks/configure-pod-container/configurevolume-storage/

7. Change the Image version back to 1.17.1 for the pod you just updated and observe the changes

8. Change the Image version to 1.15-alpine for the pod you just created and verify the image version is updated.

9. Create the nginx pod with version 1.17.4 and expose it on port 80

10. Create a redis pod and expose it on port 6379

11. Delete the pod without any delay (force delete)

12. List "nginx-dev" and "nginx-prod" pod and delete those pods

13. List all the pods showing name and namespace with a json path expression

```
kubectl get po -o custom-columns=NAME:.metadata.name,NAMESPACE:.metadata.namespace
```

14. List all the pods sorted by created timestamp

```
kubectl get pod --sort-by=.metadata.creationTimestamp
```

15. List all the pods sorted by name

```
kubectl get pod --sort-by=.metadata.name
```