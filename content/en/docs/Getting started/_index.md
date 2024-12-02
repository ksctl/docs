---
title: Getting Started
description: What does your user need to know to try your project?
categories: [Examples, Placeholders]
tags: [test, docs]
weight: 2
---

{{% pageinfo %}}
Getting Started Documentation
{{% /pageinfo %}}

# Installation & Uninstallation Instructions

## Ksctl CLI
Lets begin with installation of the tools
their are various method

### Single command method

{{% alert title="Install" %}}Steps to Install Ksctl cli tool{{% /alert %}}

```shell
curl -sfL https://get.ksctl.com | python3 -
```

{{% alert title="Uninstall" %}}Steps to Uninstall Ksctl cli tool{{% /alert %}}

{{< tabpane text=true >}}
  {{% tab header="**Operating System**:" disabled=true /%}}
  {{% tab header="Linux" %}}
```shell
bash <(curl -s https://raw.githubusercontent.com/ksctl/cli/main/scripts/uninstall.sh)
```
  {{% /tab %}}
  {{% tab header="MacOS" %}}
```shell
zsh <(curl -s https://raw.githubusercontent.com/ksctl/cli/main/scripts/uninstall.sh)
```
  {{% /tab %}}
{{< /tabpane >}}


### From Source Code

{{% alert color= "warning" title="Caution!" %}}Under-Development binaries{{% /alert %}}
{{% alert title="Note" %}}The Binaries to testing ksctl cli is available in ksctl/cli repo{{% /alert %}}

{{< tabpane text=true >}}
  {{% tab header="**Operating System**:" disabled=true /%}}
  {{% tab header="Linux/MacOS" %}}
```shell
make install_linux

# macOS on M1
make install_macos

# macOS on INTEL
make install_macos_intel

# For uninstalling
make uninstall
```
  {{% /tab %}}
{{< /tabpane >}}


{{% alert color="info" title="How to start with cli" %}}

[Here is the CLI references](https://docs.ksctl.com/docs/develop/reference/)
{{% /alert %}}
