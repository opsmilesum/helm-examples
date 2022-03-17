## Overview
- [x] What is Helm?
- [x] Helm architecture.
- [ ] Helm chart structure.
- [ ] Helm chart example.
- [x] Release Management.
- [ ] Chart Repo.
- [ ] Team's practice.

### What is Helm?
Helm is the package manager of Kubernetes, just like apt-get/yum.
It provides below features:
* Application packaging
* Version management
* Dependency check
* Easy application distribution

## Helm Architecture
![image](https://user-images.githubusercontent.com/96011359/156500515-c38fbfe8-4621-4277-8516-956e38739259.png)
* Chart Repository: chart registry, used for downloading/publishing chart.
* Helm Client: a command-line client for end users: local chart development, Managing repositories, Managing releases, etc.
* Chart: a collection of files that describe a related set of Kubernetes resources.

## Helm Chart
1. Bundle of YAML files.
2. Push Helm Chart to Helm Repository.
3. Downloading and use existing Charts.

### File Structure
<img width="180" alt="image" src="https://user-images.githubusercontent.com/96011359/156502509-3c2ffe4d-061f-4c7f-833e-e7377e8ca933.png">
* Chart.yaml: meta data of chart, name, version, etc.
* Values.yaml: values for the template files.
* Charts: chart dependencies.
* Templates: the actual template files.


### Template Engine
#### Template Yaml config

<img width="621" alt="image" src="https://user-images.githubusercontent.com/96011359/156502196-c07018a8-8b77-4fc4-8160-1ee5fc5eddc3.png">

Template strings will be replaced by the `Values.yaml` during building.

### Release Management
Release is an instance of a chart running in a Kubernetes cluster. One chart can often be installed many times into the same cluster. And each time it is installed, a new release is created.
```shell
# Create a new release.
helm install <release-name> <chart>
helm install mychart-release mychart

# Create a new release.
helm upgrade <release> <chart>
helm upgrade mychart-release mychart

# List the release 
helm ls

# Show history for a release
helm history <release-name>
helm history mychart-release

# Rollback
helm rollback <release-name> <version-number>
helm rollback mychart-release 2
```


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

### Search and Install Chart from Repo.
Search
```shell
helm repo add myrepo https://opsmilesum.github.io/helm-examples/
helm repo list
helm search repo mychart
```

Install
```shell
helm search repo nginx
helm install --repo https://charts.bitnami.com/bitnami  mynginx nginx
kubectl get all
```


