# Enterprise Linux Patching & Vulnerability Remediation Automation

## Overview

Enterprise infrastructure requires regular OS patching to address security vulnerabilities, bugs, stability issues and vendor updates. This project presents a high-level approach for automating Linux patching across RHEL, AlmaLinux and Ubuntu environments.

The platform uses a self-service IT Portal where server owners can discover their systems and initiate patching without requiring manual intervention from the operations team. The automation uses a centralized package management server to provide controlled, OS-specific updates to target servers.

The solution replaced an earlier Automox-based patching approach with an internally managed automation workflow.

## High-Level Workflow

```text
Server Owner
     |
     v
IT Portal
     |
Discover / Select Server
     |
Initiate Patching
     |
     v
Centralized Package Repository
     |
OS-Specific Updates
     |
     v
Patch Server
     |
Reboot if Required
     |
Post-Patch Validation
     |
     +-------------------+
     |                   |
   SUCCESS             FAILURE
     |                   |
     v                   v
Owner Email        OPS Notification
                         |
                         v
                  Create Incident
```

## Patch Management Approach

Patching is performed on a controlled two-week cycle:

```text
Week 1  →  Sub-Production Servers
Week 2  →  Production Servers
```

This staged approach allows updates to be applied to non-production systems first, providing an opportunity to identify issues before the production patch cycle.

## Supported Operating Systems

* Red Hat Enterprise Linux (RHEL)
* AlmaLinux
* Ubuntu

## Centralized Package Management

The environment uses **Repositor.io** as an open-source package management solution to download operating-system packages and updates from supported vendor sources into a centralized package management server.

Servers consume updates from the controlled repository rather than individually retrieving packages from external sources.

## Self-Service Patching

The IT Portal provides a simple operational workflow:

1. Discover available servers.
2. Select the server or servers to patch.
3. Initiate the patching process.
4. Automation applies the appropriate updates.
5. Server is rebooted when required.
6. Post-patch validation is performed.
7. Server owner receives completion notification.

This reduces manual effort and provides a consistent patching process across the infrastructure.

## Failure Handling

Patching failures are treated as operational events rather than silently completing with an error.

When patching encounters an issue:

* OPS team receives an email notification.
* The failure is recorded for investigation.
* An incident is created for tracking and remediation.
* The server can be investigated and corrected before the next patch cycle.

## Architecture Highlights

* Self-service Linux patching through an IT Portal.
* Centralized and controlled package management.
* Automated patching across multiple Linux distributions.
* Biweekly patching with separate sub-production and production cycles.
* Automated reboot handling when required.
* Post-patch validation.
* Owner notification after successful completion.
* Automated OPS notification and incident creation for failures.
* Migration from an earlier Automox-based approach to internally managed automation.

## Architecture Perspective

This project represents a simplified, high-level enterprise approach to Linux patch management and vulnerability remediation. The focus is on automation, controlled patch distribution, operational consistency, staged deployment and failure handling rather than proprietary implementation details or production-specific configurations.
