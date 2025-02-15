---
title: Ksctl Stack
description: Documentation on ksctl stack controller
categories: [Examples, Placeholders]
tags: [docs]
---

{{% pageinfo %}}
It helps in deploying stack using crd to help manage with installation, upgrades, downgrades, uninstallaztion. from one version to another and provide a single place of truth where to look for which applications are installed
{{% /pageinfo %}}

## How to Install?

> ksctl/kcm is a pre-requisite for this to work

```yaml
apiVersion: manage.ksctl.com/v1
kind: ClusterAddon
metadata:
  labels:
    app.kubernetes.io/name: kcm
  name: ksctl-stack
spec:
  addons:
  - name: stack
```

## Types

### Stack

For defining a hetrogenous components we came up with a stack which contains `M` number of components which are different applications with their versions


{{% alert title="Info" color="info" %}}
this is current available on all clusters created from `ksctl@v2.0.0` and utilizes `ka@v0.2.0`
{{% /alert %}}

{{% alert title="Note" color="info" %}}
It has a dependency on `kcm` as it helps in managing its lifecycle
{{% /alert %}}

{{% alert title="About Lifecycle of application stack" color="info" %}}
once you have `kubectl apply` the stack it will start deploying the applications in the stack.

If you want to upgrade the applications in the stack you can edit the stack and change the version of the application and apply the stack.
{{% /alert %}}


### Supported Apps and CNI
| Name | Type | More Info |
|- | - | - |
| GitOps | standard | [Link](#GitOps-Standard) |
| Monitoring | lite | [Link](#Monitoring-Lite) |
| Service Mesh | standard | [Link](#Service-Mesh-Standard) |
| SpinKube | standard | [Link](#Wasm-Spinkube-standard) |
| Kwasm | plus | [Link](#Wasm-Kwasm-plus) |


{{% alert title="Note on wasm category apps" color="info" %}}
Only one of the app under the category `Kwasm`, `SpinKube` can be installed at a time we you might need to uninstall one to get another running

also the current implementation of the wasm catorgoty apps annotate all the nodes with kwasm as true
{{% /alert %}}


{{% alert title="Components in Stack" color="info" %}}
All the stack are a collection of components so when you are overriding the stack values you need to tell which component it belongs to and then specifiy the value in a `map[string]any` format
{{% /alert %}}

#### **GitOps-Standard**
**How to use it (Basic Usage)**

```yaml
apiVersion: app.ksctl.com/v1
kind: Stack
metadata:
  labels:
    app.kubernetes.io/name: ka
  name: gitops
spec:
  stackName: "gitops-standard"
```


**Overrides available**

```yaml
apiVersion: app.ksctl.com/v1
kind: Stack
metadata:
  labels:
    app.kubernetes.io/name: ka
  name: gitops
spec:
  stackName: "gitops-standard"
  disableComponents: <list[str]> # list of components to disable accepeted values are argocd, argorollouts
  overrides:
    argocd:
      version: <string> # version of the argocd
      noUI: <bool> # to disable the UI
      namespace: <string> # namespace to install argocd
      namespaceInstall: <bool> # to install namespace specific argocd
    argorollouts:
      version: <string> # version of the argorollouts
      namespace: <string> # namespace to install argrollouts
      namespaceInstall: <bool> # to install namespace specific argorollouts
```

#### **Monitoring-Lite**

**How to use it (Basic Usage)**

```yaml
apiVersion: app.ksctl.com/v1
kind: Stack
metadata:
  labels:
    app.kubernetes.io/name: ka
  name: monitoring
spec:
  stackName: "monitoring-lite"
```


**Overrides available**

```yaml
apiVersion: app.ksctl.com/v1
kind: Stack
metadata:
  labels:
    app.kubernetes.io/name: ka
  name: monitoring
spec:
  stackName: "monitoring-lite"
  disableComponents: <list[str]> # list of components to disable accepeted values are kube-prometheus
  overrides:
    kube-prometheus:
      version: <string> # version of the kube-prometheus
      helmKubePromChartOverridings: <map[string]any> # helm chart overridings, kube-prometheus
```

#### **Service-Mesh-Standard**

**How to use it (Basic Usage)**

```yaml
apiVersion: app.ksctl.com/v1
kind: Stack
metadata:
  labels:
    app.kubernetes.io/name: ka
  name: mesh
spec:
  stackName: "mesh-standard"
```

**Overrides available**

```yaml
apiVersion: app.ksctl.com/v1
kind: Stack
metadata:
  labels:
    app.kubernetes.io/name: ka
  name: mesh
spec:
  stackName: "mesh-standard"
  disableComponents: <list[str]> # list of components to disable accepeted values are istio
  overrides:
    istio:
      version: <string> # version of the istio
      helmBaseChartOverridings: <map[string]any> # helm chart overridings, istio/base
      helmIstiodChartOverridings: <map[string]any> # helm chart overridings, istio/istiod
```

#### **Wasm Spinkube-standard**

**How to use it (Basic Usage)**

```yaml
apiVersion: app.ksctl.com/v1
kind: Stack
metadata:
  labels:
    app.kubernetes.io/name: ka
  name: spinkube
spec:
  stackName: "wasm/spinkube-standard"
```

**Demo app**
```shell
kubectl apply -f https://raw.githubusercontent.com/spinkube/spin-operator/main/config/samples/simple.yaml
kubectl port-forward svc/simple-spinapp 8083:80
curl localhost:8083/hello
```


**Overrides available**
```yaml
apiVersion: app.ksctl.com/v1
kind: Stack
metadata:
  labels:
    app.kubernetes.io/name: ka
  name: spinkube
spec:
  stackName: "wasm/spinkube-standard"
  disableComponents: <list[str]> # list of components to disable accepeted values are spinkube-operator, spinkube-operator-shim-executor, spinkube-operator-crd, cert-manager, kwasm-operator, spinkube-operator-runtime-class
  overrides:
    spinkube-operator:
      version: <string> # version of the spinkube-operator-shim-executor are same for shim-execuator, runtime-class, shim-executor-crd, spinkube-operator
      helmOperatorChartOverridings: <map[string]any> # helm chart overridings, spinkube-operator

    spinkube-operator-shim-executor:
      version: <string> # version of the spinkube-operator-shim-executor are same for shim-execuator, runtime-class, shim-executor-crd, spinkube-operator

    spinkube-operator-runtime-class:
      version: <string> # version of the spinkube-operator-shim-executor are same for shim-execuator, runtime-class, shim-executor-crd, spinkube-operator

    spinkube-operator-crd:
      version: <string> # version of the spinkube-operator-shim-executor are same for shim-execuator, runtime-class, shim-executor-crd, spinkube-operator

    cert-manager:
      version: <string>
      certmanagerChartOverridings: <map[string]any> # helm chart overridings, cert-manager

    kwasm-operator:
      version: <string>
      kwasmOperatorChartOverridings: <map[string]any> # helm chart overridings, kwasm/kwasm-operator
```


#### **Wasm Kwasm-plus**

**How to use it (Basic Usage)**

```yaml
apiVersion: app.ksctl.com/v1
kind: Stack
metadata:
  labels:
    app.kubernetes.io/name: ka
  name: kwasm
spec:
  stackName: "wasm/kwasm-plus"
```

**Demo app(wasmedge)**
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

**Demo app(wasmtime)**
```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: nice
  namespace: default
  labels:
    app: nice
spec:
  template:
    metadata:
      name: nice
      labels:
        app: nice
    spec:
      runtimeClassName: wasmtime
      containers:
      - name: nice
        image: "meteatamel/hello-wasm:0.1"
      restartPolicy: OnFailure
```

```shell
#### For wasmedge
# once up and running
kubectl port-forward svc/nice 8080:8080

# then you can curl the service
curl localhost:8080
```

```shell
#### For wasmtime
# just check the logs
```

**Overrides available**
```yaml
apiVersion: app.ksctl.com/v1
kind: Stack
metadata:
  labels:
    app.kubernetes.io/name: ka
  name: kwasm
spec:
  stackName: "wasm/kwasm-plus"
  disableComponents: <list[str]> # list of components to disable accepeted values are kwasm-operator
  overrides:
    kwasm-operator:
      version: <string>
      kwasmOperatorChartOverridings: <map[string]any> # helm chart overridings, kwasm/kwasm-operator
```

