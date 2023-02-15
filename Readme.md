# Gitops

## Install operator
```shell
oc apply -f subscription.yaml
```

## Get the admin password
```shell
oc get secret -n openshift-gitops openshift-gitops-cluster -ojsonpath="{.data.admin\.password}" | base64 -d
```

## Get the console link
```shell
oc get route openshift-gitops-server -n openshift-gitops -ojsonpath="{.status.ingress[0].host}"
```

## Resources

https://github.com/redhat-developer-demos/openshift-gitops-examples
