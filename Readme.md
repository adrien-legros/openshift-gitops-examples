# Gitops

## Deploy

```shell
oc apply -f ./argocd/kustomize-applicationset.yaml
```

## Get route

```shell
for ns in $(oc get ns | grep alegros-bgd | awk '{print $1}'); do oc get route bgd -n $ns -ojsonpath='{.status.ingress[0].host}'; echo; done
```

## Delete one root, see remediation on argocd

```shell
oc -n alegros-bgd-prod delete route bgd
```

## ArgoCD

### Get the admin password
```shell
oc get secret -n openshift-gitops openshift-gitops-cluster -ojsonpath="{.data.admin\.password}" | base64 -d
```

### Get the console link
```shell
oc get route openshift-gitops-server -n openshift-gitops -ojsonpath="{.status.ingress[0].host}"
```

## Install operator
```shell
oc apply -f ./operator/subscription.yaml
```

## Resources

https://github.com/redhat-developer-demos/openshift-gitops-examples
