# Networking and Database Implementation

## Overview

As part of the **Contoso Manufacturing Azure Migration Project**, the networking and database foundation was deployed to support secure communication between Azure resources and to provide a managed database platform for the organization's ERP application.

The implementation followed Microsoft's recommended deployment sequence by establishing networking components before securing database connectivity through Private Endpoints and Network Security Groups (NSGs).

> **Important Disclaimer**
>
> This project was completed using an Azure Free Trial subscription.
>
> Due to service limitations and available credits, several enterprise features could not be fully implemented, including:
>
> - Azure SQL Managed Instance
> - Geo-Replication
> - Azure Backup configuration
> - Log Analytics Workspace
> - Microsoft Defender for Cloud
> - Full subnet segmentation outlined in the production design
>
> Where implementation was not possible, the intended production configuration has been documented to demonstrate how the solution would be deployed in an enterprise environment.

---

# Implementation Sequence

The networking and database infrastructure was deployed in the following order:

1. Virtual Network (VNet)
2. Subnet Configuration
3. Network Security Group (NSG)
4. Azure SQL Database
5. Private Endpoint
6. Production Security and Monitoring Design

---

# Virtual Network Deployment

## Objective

Establish a secure network boundary for Azure resources.

### Implemented Configuration

A Virtual Network (VNet) was successfully deployed.

### Production Design Requirement

Address Space:

```text
10.10.0.0/16
```

### Purpose

The VNet provides:

- Resource isolation
- Secure communication between Azure services
- Network segmentation
- Foundation for Private Endpoints and future VPN connectivity

### Deployment Steps

1. Navigate to Azure Portal.
2. Select **Virtual Networks**.
3. Click **Create**.
4. Configure:
   - Resource Group
   - Virtual Network Name
   - Region
   - Address Space: 10.10.0.0/16
5. Review configuration.
6. Deploy the Virtual Network.

> Screenshots included within this repository demonstrate successful VNet deployment.

---

# Subnet Configuration

## Objective

Segment workloads into dedicated network boundaries.

### Implemented Configuration

A subnet was successfully created within the VNet.

### Production Design Requirement

The project scenario specifies the following subnet architecture:

```text
VNet: 10.10.0.0/16

Web Subnet         10.10.1.0/24
App Subnet         10.10.2.0/24
Database Subnet    10.10.3.0/24
Management Subnet  10.10.4.0/24
```

### Free Trial Project Scope

Due to the project being a proof-of-concept implementation, only the required subnet configuration for testing connectivity was deployed.

### Production Implementation Steps

1. Open Virtual Network.
2. Select **Subnets**.
3. Create:
   - Web Subnet
   - App Subnet
   - Database Subnet
   - Management Subnet
4. Validate address ranges.
5. Apply security controls.

---

# Network Security Group (NSG)

## Objective

Control inbound and outbound traffic to Azure resources.

### Implemented Configuration

A Network Security Group (NSG) was successfully created.

### Purpose

The NSG provides:

- Traffic filtering
- Access control
- Security boundary enforcement
- Least privilege networking

### Deployment Steps

1. Navigate to **Network Security Groups**.
2. Click **Create**.
3. Configure:
   - Name
   - Resource Group
   - Region
4. Deploy NSG.
5. Associate NSG with subnet.
6. Create inbound and outbound security rules.

### Example Production Rules

| Priority | Rule | Action |
|-----------|--------|---------|
| 100 | Allow HTTPS (443) | Allow |
| 110 | Allow SQL (1433) | Allow |
| 120 | Allow Management Access | Allow |
| 4096 | Deny All Remaining Traffic | Deny |

> Screenshots included within this repository demonstrate NSG deployment and configuration.

---

# Azure SQL Database Deployment

## Objective

Provide a managed database platform for the ERP application.

### Implemented Configuration

An Azure SQL Database was successfully deployed.

### Production Design Requirement

The project scenario specifies:

- Azure SQL Managed Instance
- 500 GB Database
- Automatic Backups
- Geo-Replication
- Private Endpoint Access

### Free Trial Limitation

Azure SQL Managed Instance was not deployed due to cost and subscription limitations.

Azure SQL Database was deployed instead to demonstrate database provisioning and connectivity.

### Deployment Steps

1. Navigate to **SQL Databases**.
2. Select **Create**.
3. Configure:
   - Database Name
   - SQL Server
   - Authentication Method
   - Compute Tier
4. Review configuration.
5. Deploy database.

### Business Requirement Supported

- ERP database hosting
- High availability architecture
- Managed database platform

> Screenshots included within this repository demonstrate successful Azure SQL Database deployment.

---

# Private Endpoint Configuration

## Objective

Secure database connectivity through private networking.

### Implemented Configuration

A Private Endpoint was successfully deployed and associated with the Azure SQL Database.

### Purpose

Private Endpoints:

- Eliminate public database exposure
- Keep traffic on Microsoft's backbone network
- Improve security posture
- Support Zero Trust architecture

### Deployment Steps

1. Open Azure SQL Database.
2. Select **Networking**.
3. Create **Private Endpoint**.
4. Select:
   - Target SQL Database
   - Virtual Network
   - Subnet
5. Enable Private DNS integration.
6. Validate connectivity.

### Expected Outcome

Database traffic remains private and inaccessible from the public internet.

> Screenshots included within this repository demonstrate successful Private Endpoint deployment.

---

# Production Features Not Implemented

## Geo-Replication

### Reason

Not available within project constraints.

### Production Configuration

1. Open SQL Database.
2. Select **Geo-Replication**.
3. Choose secondary Azure region.
4. Configure failover group.
5. Validate replication status.

### Business Requirement Supported

- Disaster Recovery
- 99.9% Availability
- Business Continuity

---

## Azure Backup

### Reason

Not configured within Free Trial environment.

### Production Configuration

1. Create Recovery Services Vault.
2. Configure backup policy.
3. Schedule daily backups.
4. Configure:
   - 30-day retention
   - Monthly retention for 1 year

### Business Requirement Supported

- Data Protection
- Compliance
- Disaster Recovery

---

## Log Analytics Workspace

### Reason

Not deployed within project scope.

### Production Configuration

1. Create Log Analytics Workspace.
2. Connect:
   - SQL Database
   - Storage Accounts
   - Virtual Machines
   - Networking Resources
3. Enable diagnostic logging.

### Business Requirement Supported

- Centralized Monitoring
- Operational Visibility

---

## Microsoft Defender for Cloud

### Reason

Not enabled due to subscription limitations.

### Production Configuration

1. Enable Microsoft Defender for Cloud.
2. Configure workload protections.
3. Review recommendations.
4. Enable threat detection policies.

### Business Requirement Supported

- Threat Detection
- Security Posture Management
- Compliance Monitoring

---

# Conclusion

The networking and database foundation for the Contoso Manufacturing migration project was successfully implemented through the deployment of a Virtual Network, subnet architecture, Network Security Group, Azure SQL Database, and Private Endpoint connectivity.

While Azure Free Trial limitations prevented the deployment of Azure SQL Managed Instance, Geo-Replication, Azure Backup, Log Analytics Workspace, and Microsoft Defender for Cloud, the complete production architecture and implementation methodology have been documented to demonstrate how these enterprise services would be configured in a real-world deployment.

Screenshots included throughout this repository provide evidence of the successful deployment and configuration of the implemented Azure resources.
