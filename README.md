# Sample manifests for deploying pgweb on Kubernetes

## Prerequisites

* kubectl: v1.14+

## How to deploy

This sample uses **kustomize** to deploy manifests to kubernetes cluster. [kustomize.io](https://kustomize.io/)

* Clone this repo
* cd into checkout dir
* execute `kubectl kustomize .` to build a kustomized manifest.  
  If you want to check generated yaml, just pipe stdout to the file.  
  `kubectl kustomize . > output.yaml`
* execute `kubectl apply -k .` to deploy resources into the target cluster.

## To expose service port

### By Service type

* You need to change `pgweb/service.yaml` to access pgweb page.  
* Default service type is `ClusterIP`, so you need to change type to `NodePort` or `LoadBalancer`

### By Ingress

If you can use ingress, just create a manifest of ingress, then add ingress.yaml to kustomization.yaml as an item of resources.

## Make overlays

If you want to use this repo as a base, create your repo as overlays, and import this sample repo.
