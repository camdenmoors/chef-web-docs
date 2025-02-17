+++
title = "Setup and Installation"
draft = false

[menu]
  [menu.desktop]
    title = "Install Workstation"
    identifier = "desktop/install/install.md Install Workstation"
    parent = "desktop/install"
    weight = 10
+++

Chef Workstation gives you everything you need to get started with Chef. Start scanning and configuring your environments today with Chef InSpec and chef-run. Chef Workstation runs on the computer you use everyday, whether it's Linux, macOS, or Windows.
Chef Workstation ships with Chef Infra Client, Chef InSpec, Chef CLI, Test Kitchen, Cookstyle, and several other useful Chef tools. With this collection of programs and tools, you can make sure your Chef Infra code does what you intended before you deploy it to environments used by others.

## Install Chef Workstation

[Download Chef Workstation](https://www.chef.io/downloads/tools/workstation) and run the installer on the developer machine. Once downloaded, run the installer, accept the default options and wait for it to complete.

Once the installation is complete, you can verify the installation by opening the command line and run:

```bash
chef --version
```

This should list out all the Chef tools that we installed in our system.

## Workstation Environment Setup

Create a `.chef` folder for storing your configuration and keys. Creating the `.chef` directory it in your "home" or "root" folder makes those settings globally available. Navigate to the root directory and create a `.chef` directory:

  For Powershell:

  1. To start Powershell from the Start Menu, click on **Start** and type **Powershell**.
  1. Right-click on **Windows Powershell** (not to be confused with **Windows Powershell ISE** which is a scripting environment) and click **Run as Administrator**.
  1. Then run the following commands one at a time.

  ```powershell
  Set-Location -Path C:\Users\<user_name>
  New-Item -Path . -Name ".chef" -ItemType "directory"
  ```

  For macOS:

  To start Terminal, open Launchpad and type **Terminal** in the search bar and then click on **Terminal**.

  ```bash
  cd ~
  mkdir .chef
  ```
