# helm-examples

## Architecture
![image](https://user-images.githubusercontent.com/96011359/156500515-c38fbfe8-4621-4277-8516-956e38739259.png)

The target of Helm
1. Wrap the K8s application.
2. Release management.
3. dependecny checking.

Helm can install local or remote charts. When the chart is installed in Kubernetes, a release will be created. Every time the configuration of the chart is updated and helm upgrade is executed, the version number of the release will increase by 1
