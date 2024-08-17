---
title: Ksctl Application Controller
description: Documentation on ksctl application controller
categories: [Examples, Placeholders]
tags: [docs]
---

{{% pageinfo %}}
It helps in deploying applications using crd to help manage with installaztion, upgrades, downgrades, uninstallaztion. from one version to another and provide a single place of truth where to look for which applications are installed
{{% /pageinfo %}}

## Types

### Stack

For defining a hetrogenous components we came up with a stack which contains `M` number of components which are different applications with their versions


{{% alert title="Info" color="info" %}}
this is current available on all clusters created by `ksctl@v1.2.0`
{{% /alert %}}

{{% alert title="Note" color="info" %}}
It has a dependency on `ksctl agent`
{{% /alert %}}

{{% alert title="About Lifecycle of application stack" color="info" %}}
once you have `kubectl apply` the stack it will start deploying the applications in the stack, if you want to upgrade the applications in the stack you can edit the stack and change the version of the application and apply the stack again, it will uninstall the previous version and install the new version. Basically it performs reinstall of the stack which might cause downtime
{{% /alert %}}

### Supported Apps and CNI
| Name | Type | Category | Ksctl_Name | More Info |
|- | - | - | - | - |
| Argo-CD | standard | CI/CD | standard-argocd |
| Argo-Rollouts | standard | CI/CD | standard-argorollouts |
| Istio | standard | Service Mesh | standard-istio |
| Cilium | standard | - | cilium |
| Flannel | standard | - | flannel |
| Kube-Prometheus | standard | Monitoring | standard-kubeprometheus |
| SpinKube | production | Wasm | production-spinkube | [Link](#spinkube) |
| WasmEdge | production | Wasm | production-wasmedge-kwasm | [Link](#wasmedge) |


{{% alert title="Note on wasm category apps" color="info" %}}
Only one of the app under the category `wasm` can be installed at a time we you might need to uninstall one to get another running

also the current implementation of the wasm catorgoty apps annotate all the nodes with kwasm as true
{{% /alert %}}

need to add the overriding docs

##### **SpinKube**

**How to use it**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
  name: wasm-spinkube
spec:
  stacks:
  - stackId: production-spinkube
    appType: app
```

**Demo app**
```shell
kubectl apply -f https://raw.githubusercontent.com/spinkube/spin-operator/main/config/samples/simple.yaml
kubectl port-forward svc/simple-spinapp 8083:80
curl localhost:8083/hello
```


##### **WasmEdge**

**How to use it**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
  name: wasm-wasmedge
spec:
  stacks:
  - stackId: production-wasmedge-kwasm
    appType: app
```

**Demo app**
```yaml
---
apiVersion: v1
kind: Pod
metadata:
  name: "myapp"
  namespace: default
  labels:
    app: nice
spec:
  runtimeClassName: wasmedge
  containers:
  - name: myapp
    image: "docker.io/cr7258/wasm-demo-app:v1"
    ports:
    - containerPort: 8080
      name: http
  restartPolicy: Always
---
apiVersion: v1
kind: Service
metadata:
  name: nice
spec:
  selector:
    app: nice
  type: ClusterIP
  ports:
  - name: nice
    protocol: TCP
    port: 8080
    targetPort: 8080
```

```shell
# once up and running
kubectl port-forward svc/nice 8080:8080

# then you can curl the service
curl localhost:8080
```

**Overrides available**
```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
  name: wasm-wasmedge
spec:
  stacks:
  - stackId: production-wasmedge-kwasm
    appType: app
    overrides:
      kwasm-operator:
        version: <string>
        kwasmOperatorChartOverridings: <map[string]any> # helm chart overridings, kwasm/kwasm-operator
```

#### Example usage

Lets deploy `argocd@v2.9.X`, `kube-prometheus-stack@v55.X.Y`
```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
  name: monitoring-plus-gitops
spec:
  components:
    - appName: standard-argocd
      appType: app
      version: v2.9.12

    - appName: standard-kubeprometheus
      appType: app
      version: "55.0.0"
```

You can see once its deployed it fetch and deploys them

Lets try to upgrade them to their latest versions
```bash
kubeclt edit stack monitoring-plus-gitops
```

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
  name: monitoring-plus-gitops
spec:
  components:
    - appName: standard-argocd
      appType: app
      version: latest

    - appName: standard-kubeprometheus
      appType: app
      version: latest
```

once edited it will uninstall the previous install and reinstalls the latest deployments
