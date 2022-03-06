## Introuction
<img width="456" alt="image" src="https://user-images.githubusercontent.com/96011359/156687262-5eabfd2e-949c-4048-b48d-5a11f63f5568.png">
Deployment 处于 master 节点上，通过发布 Deployment，master 节点会选择合适的 worker 节点创建 Container（即图中的正方体），Container 会被包含在 Pod （即蓝色圆圈）里。


## Command
```shell
# log into the container
kubectl exec -ti $POD_NAME -- bash

# find the service port
kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}'
```
