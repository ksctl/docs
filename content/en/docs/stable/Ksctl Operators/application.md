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
| Argo-CD | standard | CI/CD | standard-argocd | [Link](#argo-cd) |
| Argo-Rollouts | standard | CI/CD | standard-argorollouts | [Link](#argo-rollouts) |
| Istio | standard | Service Mesh | standard-istio | [Link](#istio) |
| Cilium | standard | - | cilium | [Link](#cilium) |
| Flannel | standard | - | flannel | [Link](#flannel) |
| Kube-Prometheus | standard | Monitoring | standard-kubeprometheus | [Link](#kube-prometheus) |
| SpinKube | production | Wasm | production-spinkube | [Link](#spinkube) |
| WasmEdge and Wasmtime | production | Wasm | production-kwasm | [Link](#kwasm) |


{{% alert title="Note on wasm category apps" color="info" %}}
Only one of the app under the category `wasm` can be installed at a time we you might need to uninstall one to get another running

also the current implementation of the wasm catorgoty apps annotate all the nodes with kwasm as true
{{% /alert %}}


{{% alert title="Components in Stack" color="info" %}}
All the stack are a collection of components so when you are overriding the stack values you need to tell which component it belongs to and then specifiy the value in a `map[string]any` format
{{% /alert %}}

#### **Argo-CD**
**How to use it (Basic Usage)**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: argocd
spec:
	stacks:
	- stackId: standard-argocd
		appType: app
```


**Overrides available**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: argocd
spec:
	stacks:
	- stackId: standard-argocd
		appType: app
		overrides:
			argocd:
				version: <string> # version of the argocd
				noUI: <bool> # to disable the UI
				namespace: <string> # namespace to install argocd
				namespaceInstall: <bool> # to install namespace specific argocd
```

#### **Argo-Rollouts**

**How to use it (Basic Usage)**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: argorollouts
spec:
	stacks:
	- stackId: standard-argorollouts
		appType: app
```

**Overrides available**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: argorollouts
spec:
	stacks:
	- stackId: standard-argorollouts
		appType: app
		overrides:
			argorollouts:
				version: <string> # version of the argorollouts
				namespace: <string> # namespace to install argocd
				namespaceInstall: <bool> # to install namespace specific argocd
```

#### **Istio**

**How to use it (Basic Usage)**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: istio
spec:
	stacks:
	- stackId: standard-istio
		appType: app
```

**Overrides available**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: istio
spec:
	stacks:
	- stackId: standard-istio
		appType: app
		overrides:
			istio:
				version: <string> # version of the istio
				helmBaseChartOverridings: <map[string]any> # helm chart overridings, istio/base
				helmIstiodChartOverridings: <map[string]any> # helm chart overridings, istio/istiod
```

#### **Cilium**

Currently we cannot install via the ksctl crd as cni are needed to be installed when configuring otherwise it will cause network issues

still we have cilium can be installed and only configuration available are `version`, we are working towards how can we allow users to specify the overridings in the cluster creation

anyways here is how it is done

> we can consider using a file spec instead of cmd parameter, until that is done you have to wait

**How to use it (Basic Usage)**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: cilium
spec:
	stacks:
	- stackId: cilium
		appType: app
```

**Overrides available**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: cilium
spec:
	stacks:
	- stackId: cilium
		appType: app
		overrides:
			cilium:
				version: <string> # version of the cilium
				ciliumChartOverridings: <map[string]any> # helm chart overridings, cilium
```

#### **Flannel**

Currently we cannot install via the ksctl crd as cni are needed to be installed when configuring otherwise it will cause network issues

still we have flannel can be installed and only configuration available are `version`, we are working towards how can we allow users to specify the overridings in the cluster creation

> we can consider using a file spec instead of cmd parameter, until that is done you have to wait

**How to use it (Basic Usage)**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: flannel
spec:
	stacks:
	- stackId: flannel
		appType: cni
```

**Overrides available**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: flannel
spec:
	stacks:
	- stackId: flannel
		appType: cni
		overrides:
			flannel:
				version: <string> # version of the flannel
```

#### **Kube-Prometheus**

**How to use it (Basic Usage)**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: monitoring
spec:
	stacks:
	- stackId: standard-kubeprometheus
		appType: app
```

**Overrides available**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: monitoring
spec:
	stacks:
	- stackId: standard-kubeprometheus
		appType: app
		overrides:
			kube-prometheus:
				version: <string> # version of the kube-prometheus
				helmKubePromChartOverridings: <map[string]any> # helm chart overridings, kube-prometheus
```


#### **SpinKube**

**How to use it (Basic Usage)**

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


**Overrides available**
```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: wasm-spinkube
spec:
	stacks:
	- stackId: production-wasmedge-kwasm
		appType: app
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


#### **Kwasm**

**How to use it (Basic Usage)**

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
	name: wasm-kwasm
spec:
	stacks:
	- stackId: production-kwasm
		appType: app
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
