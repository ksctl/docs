---
title: Getting Started with Ksctl CLI
date: 2017-01-05
description: >
  A short lead description about this content page. It can be **bold** or _italic_ and can be split over multiple paragraphs.
---

# Installation

Lets begin with installation of the tools
their are various method

## Single command method

{{% alert title="Install" %}}Steps to Install Ksctl cli tool{{% /alert %}}

{{< tabpane text=true >}}
  {{% tab header="**Operating System**:" disabled=true /%}}
  {{% tab header="Linux" %}}
```bash
curl -sfL https://raw.githubusercontent.com/ksctl/cli/main/scripts/install.sh | python3 -
```
  {{% /tab %}}
  {{% tab header="MacOS" %}}
```bash
curl -sfL https://raw.githubusercontent.com/ksctl/cli/main/scripts/install.sh | python3 -
```
  {{% /tab %}}
  {{% tab header="Windows" lang="sw" %}}
```ps1
iwr -useb https://raw.githubusercontent.com/ksctl/cli/main/install.ps1 | iex
```
  {{% /tab %}}
{{< /tabpane >}}


{{% alert title="Uninstall" %}}Steps to Uninstall Ksctl cli tool{{% /alert %}}

{{< tabpane text=true >}}
  {{% tab header="**Operating System**:" disabled=true /%}}
  {{% tab header="Linux" %}}
```bash
bash <(curl -s https://raw.githubusercontent.com/ksctl/cli/main/scripts/uninstall.sh)
```
  {{% /tab %}}
  {{% tab header="MacOS" %}}
```bash
zsh <(curl -s https://raw.githubusercontent.com/ksctl/cli/main/scripts/uninstall.sh)
```
  {{% /tab %}}
  {{% tab header="Windows" lang="sw" %}}
```ps1
iwr -useb https://raw.githubusercontent.com/ksctl/cli/main/scripts/uninstall.ps1 | iex
```
  {{% /tab %}}
{{< /tabpane >}}


## From Source Code

{{% alert color= "warning" title="Caution!" %}}Under-Development binaries{{% /alert %}}
{{% alert title="Note" %}}The Binaries to testing ksctl cli is available in ksctl/cli repo{{% /alert %}}

{{< tabpane text=true >}}
  {{% tab header="**Operating System**:" disabled=true /%}}
  {{% tab header="Linux/MacOS" %}}
```bash
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


#### [Azure Cluster](/docs/cloud-providers/azure/)
#### [Civo Cluster](/docs/cloud-providers/civo/)

