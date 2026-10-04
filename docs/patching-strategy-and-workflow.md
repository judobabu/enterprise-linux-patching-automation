# Patching Strategy & Workflow

## Purpose

Regular OS patching is a critical infrastructure activity used to address security vulnerabilities, operating-system bugs, stability issues and vendor-provided fixes.

The goal is to provide a consistent and controlled patching process while minimizing disruption to application workloads.

## Patching Strategy

The environment follows a two-week patching cycle:

```text id="8m4pqa"
Week 1
Sub-Production
     |
     v
Patch → Reboot if Required → Validate

Week 2
Production
     |
     v
Patch → Reboot if Required → Validate
```

Sub-production systems are patched first so that potential issues can be identified before the production patch cycle.

## High-Level Workflow

```text id="q3n7cv"
Discover Servers
      |
      v
Select Server(s)
      |
      v
Initiate Patching
      |
      v
Determine OS / Repository
      |
      v
Apply Available Updates
      |
      v
Reboot if Required
      |
      v
Post-Patch Validation
      |
      v
Notify Server Owner
```

## Server Owner Experience

The patching process is designed to be self-service:

* Server owner accesses the IT Portal.
* Available servers are discovered.
* Server owner selects the required server.
* Patching is initiated.
* Automation performs the patching workflow.
* Server is rebooted when required.
* Validation is performed.
* Completion status is communicated to the server owner.

## Patch Sources

The centralized package management server provides controlled update sources for the supported operating systems.

The repository workflow retrieves packages and updates from OS vendor sources and makes them available to the infrastructure through the centralized repository.

## Operational Principles

* Patch systems on a predictable schedule.
* Patch sub-production before production.
* Use controlled package sources.
* Minimize manual intervention.
* Reboot only when required.
* Validate after patching.
* Notify owners of completion.
* Escalate failures through the operations process.

## Architecture Principle

Patching should be treated as a repeatable infrastructure lifecycle rather than a manual server-by-server activity. Automation provides consistency, visibility and controlled execution across the Linux environment.
