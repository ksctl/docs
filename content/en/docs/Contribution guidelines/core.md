---
title: Contribution Guidelines for Core
description: How to contribute to the ksctl
---

{{% pageinfo %}}
Repository: kubesimplify/ksctl
{{% /pageinfo %}}


## Test out both All Mock and Unit tests
```bash
make test
```

## Test out both All Unit tests
```bash
make unit_test_api
```

## Test out both All Mock tests
```bash
make mock_test
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
