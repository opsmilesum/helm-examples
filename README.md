## Target
- [ ] How to use helm to download images?
- [x] Release Management.
- [ ] Common template writing.
- [x] File structure.
- [x] Component Archicture.
- [x] Publish and Download Chart to/from Repo.

# helm-examples

## Architecture
![image](https://user-images.githubusercontent.com/96011359/156500515-c38fbfe8-4621-4277-8516-956e38739259.png)

## The target of Helm
1. Wrap the K8s application.
2. Release management.
3. dependecny checking.

Helm can install local or remote charts. When the chart is installed in Kubernetes, a release will be created. Every time the configuration of the chart is updated and helm upgrade is executed, the version number of the release will increase by 1

## Helm Chart
1. Bundle of YAML files.
2. Push Helm Chart to Helm Repository.
3. Downloading and use existing Charts.

### File Structure
<img width="280" alt="image" src="https://user-images.githubusercontent.com/96011359/156502509-3c2ffe4d-061f-4c7f-833e-e7377e8ca933.png">
* Chart.yaml: meta data of chart, name, version, etc.
* Values.yaml: values for the template files.
* Charts: chart dependencies.
* Templates: the actual template files.


### Template Engine
#### Template Yaml config

<img width="621" alt="image" src="https://user-images.githubusercontent.com/96011359/156502196-c07018a8-8b77-4fc4-8160-1ee5fc5eddc3.png">

Template strings will be replaced by the `Values.yaml` during building.

### Release Management
#### Helm V2
Tiller has too much power inside of k8s cluster -> sucurity issue.
<img width="1192" alt="image" src="https://user-images.githubusercontent.com/96011359/156503537-b3743bb5-b7d5-4b24-80c1-74ba22c6abef.png">

### Repository
Publish Chart to Repo.
```shell
helm package mychart/
helm repo index --url https://opsmilesum.github.io/helm-examples/ .
git commit -a -m "xxx"
// Re-deploy the github page. 
```

Read Chart from Repo.
```shell
helm repo add myrepo https://opsmilesum.github.io/helm-examples/
helm repo list
helm search repo mychart
```
