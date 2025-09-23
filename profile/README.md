# PolicyStack

> **Simplifying OpenShift policy management through GitOps and modular configuration**

## What is PolicyStack?

PolicyStack is an open-source framework that makes it easy to manage configuration across multiple OpenShift clusters. Think of it as a flexible, reusable library of best practices that you can apply consistently across your entire infrastructure.

## The Challenge PolicyStack Solves

Managing configurations across multiple OpenShift clusters is complex:
- **Different environments** need different settings (development vs. production)
- **Compliance requirements** vary by region, industry, or team
- **Manual configuration** leads to drift and inconsistencies
- **Security policies** are hard to enforce uniformly
- **Documentation** often falls out of sync with actual configurations

PolicyStack solves these challenges by providing a structured, GitOps-driven approach to policy management.

## How It Works

PolicyStack uses a simple but powerful model:

### 1. **Policy Elements** 
Think of these as building blocks - each element is a collection of related policies packaged as a Helm chart. Examples might include:
- Security baseline configurations
- Compliance scanning setups
- Resource management policies
- Operator installations
- Certificate management rules

### 2. **The Stack**
Your "stack" is the collection of elements you choose to deploy. Like building with LEGO blocks, you can:
- Enable or disable individual elements
- Customize each element's configuration
- Apply different stacks to different clusters

### 3. **Hierarchical Configuration**
PolicyStack's real power comes from its layered configuration approach:
```
Global Settings → Environment Settings → Datacenter Settings → Cluster-Specific Settings
```
This means you can set defaults once and only override what's different, reducing repetition and errors.

## Repositories

### 📦 **PolicyStack** (Main Repository)
The core implementation containing:
- **Pre-built policy elements** ready to use
- **Tools and utilities** for creating new elements and generating documentation
- **GitOps configurations** for automated deployment
- **Example configurations** to get you started

### 📊 **PolicyStack-chart** 
The Helm chart library containing:
- **policy-library chart**: The foundational chart that makes PolicyStack elements work
- **Additional utility charts**: Supporting charts for specific use cases - PENDING

### 💻 **cli**
The cli implementation of PolicyStack that allows for searching, installing, and scaffolding elements.

### 🏬 **marketplace**
Marketplace for PolicyStack configurations.
- **Searchable**: Allows for easily searchable configurations through a compiled index.
- **Version control**: Creates separate version instances for upgradability.
- **Upgrade paths**: Upgrades between versions are seamless due to recommended pathing.

## Key Benefits

✅ **Consistency**: Apply the same security and configurations everywhere  
✅ **Flexibility**: Customize policies for specific clusters without duplicating work  
✅ **Automation**: Deploy and update policies automatically through GitOps  
✅ **Documentation**: Auto-generated, always up-to-date documentation from your configurations  
✅ **Version Control**: All changes tracked in Git for full auditability  
✅ **Reusability**: Share policy elements across teams and organizations  

## Architecture Overview

```
┌─────────────────────────────────────┐
│         Git Repository               │
│  (Your PolicyStack Configuration)    │
└────────────┬────────────────────────┘
             │
             ▼
┌─────────────────────────────────────┐
│    ArgoCD ApplicationSets           │
│  (Monitors Git for changes)         │
└────────────┬────────────────────────┘
             │
             ▼
┌─────────────────────────────────────┐
│    ACM Hub Cluster                  │
│  (Creates and manages policies)     │
└────────────┬────────────────────────┘
             │
             ▼
┌─────────────────────────────────────┐
│    Managed Clusters                 │
│  (Receive and enforce policies)     │
└─────────────────────────────────────┘
```

## Example Use Cases

### 🔒 **Security Hardening**
Deploy a consistent security baseline across all clusters, with stricter controls in production environments.

### 📋 **Compliance Management**
Automatically enforce and document compliance with regulatory standards, generating audit reports on demand.

### 🚀 **Operator Lifecycle**
Manage operator installations and updates across clusters, ensuring consistent versions and configurations.

### 🔧 **Resource Management**
Enforce resource quotas and limits to prevent resource exhaustion and ensure fair usage.

### 🎯 **Environment-Specific Configuration**
Apply different policies to development, staging, and production clusters while maintaining a single source of truth.

## Documentation

Every PolicyStack element can include inline documentation that's automatically extracted to create comprehensive, always-current documentation. This means your policies are self-documenting, making it easy for teams to understand what's deployed and why.

## Why PolicyStack?

PolicyStack is different. It's:
- **Open Source**: No vendor lock-in
- **GitOps Native**: Fits naturally into modern workflows
- **Modular**: Use what you need, ignore what you don't
- **Documented**: Self-documenting by design

## Next Steps

Ready to get started? Check out:
1. [PolicyStack Repository](https://github.com/PolicyStack/PolicyStack) - The main implementation
2. [PolicyStack-Charts Repository](https://github.com/PolicyStack/PolicyStack-charts) - The Helm charts
3. [Quick Start Guide](https://github.com/PolicyStack/PolicyStack#installation) - Step-by-step installation
