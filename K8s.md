## Introuction
<img width="456" alt="image" src="https://user-images.githubusercontent.com/96011359/156687262-5eabfd2e-949c-4048-b48d-5a11f63f5568.png">
Deployment 处于 master 节点上，通过发布 Deployment，master 节点会选择合适的 worker 节点创建 Container（即图中的正方体），Container 会被包含在 Pod （即蓝色圆圈）里。


## Command
### Debug
```shell
# log into the container
kubectl exec -ti $POD_NAME -- bash
```

### Deploy 
```shell
# get Deploy
kubectl get deplo

# Delete Deploy
kubectl delete deploy <deploy-name>
```

### Service
```shell
# Expose the Service
kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080

# Query Service 
kubectl get services

# Delete Service
kubectl delete service -l app=kubernetes-bootcamp

# find the service port
kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}'
```

> Attention! Node is used in the K8s cluster while NodePort is used in the Node.
> For example: 
<img width="843" alt="image" src="https://user-images.githubusercontent.com/96011359/156923977-7a5a384c-2053-4cf5-b462-74c233b49ace.png">
 


### Label
```shell
# Set label for a pod
kubectl label pods kubernetes-bootcamp-57978f5f5d-5qq62  mylabel=12345

# Query label for a pod
get pods -l mylabel=12345
```
