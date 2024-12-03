---
title: Contribution Guidelines for Core
description: How to contribute to the ksctl
---

{{% pageinfo %}}
Repository: ksctl/ksctl
{{% /pageinfo %}}

## Project structure

### pkg/

It contains the importable functionality of ksctl

* *Controllers* (as this will be the only way to interact with the ksctlcore  
* *Utility* functions with *consts* and *errors*  
* *Logger*  
* *Types*

### internal/

It contains the *cloudProvider*, *K8sDistro*, *StorageDriver* specific implementations

### test/

It contains the e2e and e2e test helper code and also the mock test files  



## Test out both All Mock and Unit tests and lints
```bash
make test
```

## Test out both All Unit tests
```bash
make unit_test_all
```

## Test out both All Mock tests
```bash
make mock_all
```

## for E2E tests on local
set the required token as ENV vars
then
```bash
cd test/e2e

# then the syntax for running
go run . -op create -file azure/create.json

# for operations you can refer file test/e2e/consts.go
```
