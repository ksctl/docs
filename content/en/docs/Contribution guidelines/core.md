---
title: Contribution Guidelines for Core
description: How to contribute to the ksctl
---

{{% pageinfo %}}
Repository: ksctl/ksctl
{{% /pageinfo %}}

## Test out both all Unit tests
```bash
make unit_test
```

## Test out both all integeration_test
```bash
make integration_test
```

## Test out both unit tests and integeration tests
```bash
make test_all
```

## for E2E tests on local
set the required token as ENV vars

For cloud provider specific e2e tests
### token for Azure
```shell
export AZURE_SUBSCRIPTION_ID=""
export AZURE_TENANT_ID=""
export AZURE_CLIENT_ID=""
export AZURE_CLIENT_SECRET=""
```

### token for AWS
```shell
export AWS_ACCESS_KEY_ID=""
export AWS_SECRET_ACCESS_KEY=""
```

### token for Mongodb as storage
```shell
export MONGODB_SRV=<true|false> # boolean
export MONGODB_HOST=""
export MONGODB_PORT=""
export MONGODB_USER=""
export MONGODB_PASS=""
```

```shell
cd test/e2e

# then the syntax for running
go run . -op create -file azure/create.json

# for operations you can refer file test/e2e/consts.go
```
