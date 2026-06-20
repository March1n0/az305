# Storage Implementation – Azure Files Foundation

## Overview

As part of the **Contoso Manufacturing Azure Migration Project**, the storage layer was designed and implemented to support the migration of company data from on-premises file servers to Azure. This aligns with the business requirement to modernize infrastructure, improve scalability, and provide highly available cloud-based storage for both office and remote workers.

> **Important Disclaimer**
>
> This project was completed using an Azure Free Trial subscription. While a Storage Account was successfully deployed and configured, the full production implementation of Azure Files, Azure File Sync, large-scale data migration (10 TB), and enterprise backup configurations could not be fully demonstrated due to free-tier limitations and the absence of an on-premises environment.

---

# Storage Account Deployment

## Objective

The first step in implementing the storage solution was to deploy an Azure Storage Account that would serve as the foundation for Azure Files and future storage services.

## Storage Configuration Implemented

| Setting | Configuration |
|----------|---------------|
| Region | South Africa North |
| Performance Tier | Standard |
| Redundancy | Geo-Redundant Storage (GRS) |
| Storage Type | General Purpose v2 |
| Access Tier | Hot (Default) |

---

## Why South Africa North?

The **South Africa North** Azure region was selected because:

- It is geographically closest to the company's Head Office in Cape Town.
- Provides lower network latency.
- Meets local data residency requirements.
- Supports business continuity and disaster recovery objectives.

---

## Why Standard Performance?

The **Standard Performance Tier** was selected because it:

- Provides a cost-effective storage solution.
- Supports file shares, blobs, queues, and tables.
- Meets the requirements of typical enterprise file storage workloads.
- Is suitable for the organization's planned 10 TB file migration.

In a production environment, Premium storage would only be considered if extremely high-performance workloads required low-latency access.

---

## Why Geo-Redundant Storage (GRS)?

The project requirements include improved disaster recovery capabilities and data protection.

To support these objectives, **Geo-Redundant Storage (GRS)** was selected.

### Benefits of GRS

- Maintains multiple copies of data within the primary region.
- Replicates data to a secondary Azure region.
- Protects against regional outages.
- Improves business continuity.
- Supports the organization's disaster recovery strategy.

### Alignment with Business Requirements

GRS directly supports:

- Improved Disaster Recovery
- Increased Availability
- Data Durability
- Business Continuity Planning

---

## Implementation Sequence

The Storage Account was created following Microsoft's recommended deployment sequence.

### Navigate to Storage Accounts

1. Logged into Azure Portal.
2. Selected **Storage Accounts**.
3. Clicked **Create Storage Account**.

### Configure Basic Settings

Configured:

- Subscription
- Resource Group
- Storage Account Name
- Region: South Africa North

### Configure Performance

Selected:

- Standard Performance

### Configure Redundancy

Selected:

- Geo-Redundant Storage (GRS)

### Review and Deploy

1. Reviewed all settings.
2. Validated deployment configuration.
3. Created the Storage Account.
4. Verified successful deployment.
5. Captured screenshots as implementation evidence.

> Screenshots included in this repository demonstrate the successful creation and configuration of the Azure Storage Account.

---

## Intended Production Implementation

According to the Contoso Manufacturing design requirements, the deployed Storage Account would serve as the foundation for:

### Azure Files

- 10 TB cloud-based file storage
- Secure access for office users
- Secure access for remote users
- SMB file share support

### Azure File Sync

- Synchronization between on-premises file servers and Azure
- Hybrid storage architecture
- Reduced on-premises storage requirements

### Azure Backup

Backup configuration would include:

- Daily backups
- 30-day retention
- Monthly retention for 1 year

### Security Controls

Additional production configurations would include:

- Private Endpoints
- RBAC Access Control
- Storage Firewall Rules
- Microsoft Defender for Storage
- Monitoring via Azure Monitor

---

## Conclusion

The storage foundation for the Contoso Manufacturing migration project was successfully deployed through the creation of an Azure Storage Account in the **South Africa North** region using **Standard Performance** and **Geo-Redundant Storage (GRS)**. This configuration aligns with the organization's requirements for scalability, availability, and disaster recovery.

While Azure Free Trial limitations prevented full implementation of Azure Files migration and enterprise backup scenarios, the deployed storage architecture provides a realistic enterprise-ready foundation and demonstrates the approach that would be used in a production environment.
