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

{{< tabpane text=true >}}
  {{% tab header="**Operating System**:" disabled=true /%}}
  {{% tab header="Linux" %}}
```shell
curl -sfL https://get.ksctl.com/install/linux | python3 -
```
  {{% /tab %}}
  {{% tab header="MacOS" %}}
```shell
curl -sfL https://get.ksctl.com/install/macos | python3 -
```
  {{% /tab %}}
  {{% tab header="Windows" lang="sw" %}}
```ps1
iwr -useb https://get.ksctl.com/install/windows | iex
```
  {{% /tab %}}
{{< /tabpane >}}


{{% alert title="Uninstall" %}}Steps to Uninstall Ksctl cli tool{{% /alert %}}

{{< tabpane text=true >}}
  {{% tab header="**Operating System**:" disabled=true /%}}
  {{% tab header="Linux" %}}
```shell
bash <(curl -s https://get.ksctl.com/uninstall/linux)
```
  {{% /tab %}}
  {{% tab header="MacOS" %}}
```shell
zsh <(curl -s https://get.ksctl.com/uninstall/macos)
```
  {{% /tab %}}
  {{% tab header="Windows" lang="sw" %}}
```ps1
iwr -useb https://get.ksctl.com/uninstall/windows | iex
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

  {{% tab header="Windows" lang="sw" %}}
```ps1
./builder.ps1

# for uninstalling
./uninstall.ps1
```
  {{% /tab %}}
{{< /tabpane >}}


{{< alert color="success" title="Demo for the ksctl installation" >}}
  <!-- <iframe width="560" height="315" src="https://www.youtube.com/embed/iYwE3h0p7Zs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> -->
  <video width="360" height="202" controls>
  <source src="/videos/ksctl-install.mp4" type="video/mp4" />
    Your browser does not support the video tag.
  </video>
{{< /alert >}}
