# Repository & Patch Management

## Purpose

A centralized package repository provides a controlled source for operating-system packages and updates.

Instead of each server independently retrieving packages from external sources, the infrastructure uses a centralized package management server.

## Repository Workflow

```text id="5xq3nk"
OS Vendor Sources
       |
       v
  Repositor.io
       |
       v
Central Package Management Server
       |
       +------------------+------------------+
       |                  |                  |
       v                  v                  v
     RHEL             AlmaLinux           Ubuntu
       |                  |                  |
       +------------------+------------------+
                          |
                          v
                    Target Servers
```

## Repositor.io

**Repositor.io** is used as the open-source repository management component for downloading and maintaining operating-system packages and updates from supported vendor sources.

The centralized repository provides a consistent package source for servers during patching activities.

## Supported Platforms

The patching workflow supports:

* RHEL
* AlmaLinux
* Ubuntu

The appropriate repository and package source is selected based on the operating system of the target server.

## Patch Management Flow

```text id="z7k1pd"
Identify Server
      |
      v
Identify Operating System
      |
      v
Select Appropriate Repository
      |
      v
Apply Available Updates
      |
      v
Reboot if Required
      |
      v
Validate Server
```

## Benefits

* Centralized package management.
* Consistent update sources.
* Reduced dependency on individual servers accessing external repositories.
* Better control over patch distribution.
* Supports multiple Linux distributions.
* Simplifies enterprise patch operations.
* Provides a foundation for repeatable and automated patching.

## Architecture Principle

A centralized repository separates **package acquisition and management** from **patch execution**. This allows the patching automation to focus on safely applying approved updates to target servers while maintaining a consistent package source.
