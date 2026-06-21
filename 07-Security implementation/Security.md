# Security, Monitoring, Backup, and Disaster Recovery Implementation

## Overview

As part of the **Contoso Manufacturing Azure Migration Project**, the security, monitoring, backup, and disaster recovery components were designed to protect organizational resources, improve visibility across the environment, and ensure business continuity.

The project scenario requires:

- Multi-layered security controls
- Centralized monitoring and logging
- Threat detection
- Least privilege access
- Daily backups
- Geo-redundant disaster recovery
- Recovery Point Objective (RPO): 4 Hours
- Recovery Time Objective (RTO): 8 Hours

The implementation followed Microsoft's recommended deployment sequence by first establishing security controls, followed by monitoring, backup, and disaster recovery services.

> **Important Disclaimer**
>
> This project was completed using an Azure Free Trial subscription.
>
> Due to licensing restrictions and subscription limitations, the following enterprise services could not be fully implemented:
>
> - Microsoft Defender for Cloud
> - Microsoft Sentinel
> - Log Analytics Workspace
> - Centralized Logging
> - Advanced RBAC Configuration
> - Customer Managed Encryption
> - Vulnerability Assessment
> - Virtual Machine Scanning
> - SQL Database Threat Detection
> - Update Management and Patch Management
> - Azure Firewall
> - Recovery Services Vault
> - Azure Backup
> - Geo-Redundant Backup Configuration
>
> Where implementation was not possible, the intended production architecture and deployment methodology have been documented to demonstrate how these services would be configured in a real-world enterprise environment.

---

# Implementation Sequence

The security and disaster recovery architecture would be implemented in the following order:

1. Role-Based Access Control (RBAC)
2. Data Encryption
3. Microsoft Defender for Cloud
4. Microsoft Sentinel
5. Centralized Logging
6. Vulnerability Assessment
7. Patch Management
8. Azure Firewall
9. Recovery Services Vault
10. Azure Backup
11. Geo-Redundant Backup Strategy
12. Disaster Recovery Validation

---

# Role-Based Access Control (RBAC)

## Objective

Implement least-privilege access across Azure resources.

### Why This Benefits Contoso Manufacturing

RBAC ensures that users only receive permissions necessary to perform their job responsibilities.

Examples:

| Department | Access |
|------------|---------|
| Finance | Finance Resources |
| HR | HR Resources |
| IT | Administrative Resources |

This reduces:

- Unauthorized access
- Insider threats
- Accidental resource modification

### Production Configuration

1. Navigate to Azure Portal.
2. Open Subscription or Resource Group.
3. Select **Access Control (IAM)**.
4. Click **Add Role Assignment**.
5. Select Role:
   - Reader
   - Contributor
   - Owner
   - Custom Roles
6. Assign users or security groups.

### Security Groups Previously Created

- Finance
- HR
- IT

These groups would be assigned permissions rather than assigning permissions directly to users.

---

# Data Encryption

## Objective

Protect sensitive business data.

### Why This Benefits Contoso Manufacturing

The organization stores:

- ERP Data
- Employee Data
- Financial Records
- Customer Information

Encryption protects data from unauthorized access.

### Production Configuration

Azure automatically provides:

- Encryption at Rest
- Encryption in Transit

Additional enterprise configuration:

1. Navigate to resource.
2. Open Encryption settings.
3. Configure:
   - Microsoft Managed Keys
   - Customer Managed Keys (Key Vault)

### Benefits

- Regulatory compliance
- Improved security
- Reduced risk of data exposure

---

# Microsoft Defender for Cloud

## Objective

Provide continuous security assessment and threat detection.

### Why This Benefits Contoso Manufacturing

Defender for Cloud would monitor:

- Storage Accounts
- SQL Databases
- Virtual Machines
- Networking Resources

### Production Configuration

1. Navigate to Microsoft Defender for Cloud.
2. Enable Defender Plans.
3. Select workloads:
   - Servers
   - SQL Databases
   - Storage Accounts
4. Review security recommendations.
5. Configure alerts.

### Benefits

- Threat detection
- Security posture management
- Compliance monitoring

### Free Trial Limitation

Microsoft Defender for Cloud was not enabled due to subscription limitations.

---

# Microsoft Sentinel

## Objective

Provide centralized Security Information and Event Management (SIEM).

### Why This Benefits Contoso Manufacturing

Sentinel would collect security logs from:

- Azure Resources
- Microsoft Entra ID
- SQL Databases
- Storage Accounts
- Network Resources

### Production Configuration

1. Create Log Analytics Workspace.
2. Open Microsoft Sentinel.
3. Select **Create Sentinel Instance**.
4. Connect Log Analytics Workspace.
5. Configure Data Connectors.
6. Create Detection Rules.
7. Configure Incident Response.

### Benefits

- Security event correlation
- Automated threat detection
- Centralized monitoring

### Free Trial Limitation

Microsoft Sentinel could not be deployed.

---

# Centralized Logging

## Objective

Collect logs from all Azure resources.

### Why This Benefits Contoso Manufacturing

Provides visibility into:

- User activity
- Security events
- Database activity
- Storage access
- Resource performance

### Production Configuration

1. Create Log Analytics Workspace.
2. Enable Diagnostic Settings.
3. Connect:
   - SQL Database
   - Storage Account
   - App Service
   - Networking Resources
4. Configure retention policies.

### Benefits

- Centralized troubleshooting
- Operational monitoring
- Security investigations

### Free Trial Limitation

Log Analytics Workspace was not deployed.

---

# Vulnerability Assessment and Scanning

## Objective

Identify security weaknesses before exploitation.

### Why This Benefits Contoso Manufacturing

Provides visibility into:

- Missing patches
- Security vulnerabilities
- Misconfigurations

### Production Configuration

#### Virtual Machines

1. Enable Defender for Servers.
2. Enable Vulnerability Assessment.
3. Review recommendations.
4. Remediate findings.

#### SQL Database

1. Open SQL Database.
2. Enable Microsoft Defender for SQL.
3. Enable Vulnerability Assessment.
4. Review reports.
5. Remediate issues.

### Free Trial Limitation

Scanning and vulnerability assessment could not be enabled.

---

# Patch Management

## Objective

Maintain system security and compliance.

### Why This Benefits Contoso Manufacturing

Patch Management reduces risk from:

- Known vulnerabilities
- Malware
- Ransomware

### Production Configuration

1. Create Azure Automation Account.
2. Enable Update Management.
3. Register Virtual Machines.
4. Configure maintenance schedules.
5. Review compliance reports.

### Benefits

- Improved security
- Reduced downtime
- Consistent patching

### Free Trial Limitation

Patch Management was not configured.

---

# Azure Firewall

## Objective

Control network traffic entering and leaving Azure.

### Why This Benefits Contoso Manufacturing

Provides:

- Centralized traffic inspection
- Threat filtering
- Network segmentation

### Production Configuration

1. Deploy Azure Firewall.
2. Create dedicated firewall subnet.
3. Configure routing.
4. Create:
   - Application Rules
   - Network Rules
   - NAT Rules
5. Validate traffic flow.

### Benefits

- Enhanced network security
- Traffic visibility
- Threat prevention

### Free Trial Limitation

Azure Firewall was not deployed.

---

# Recovery Services Vault

## Objective

Provide centralized backup management.

### Why This Benefits Contoso Manufacturing

Required to protect:

- Azure Files
- Virtual Machines
- Databases

### Production Configuration

1. Create Recovery Services Vault.
2. Configure backup policies.
3. Register workloads.
4. Schedule backups.

### Free Trial Limitation

Recovery Services Vault was not deployed.

---

# Azure Backup

## Objective

Protect business-critical workloads.

### Production Configuration

1. Open Recovery Services Vault.
2. Select Backup.
3. Choose workload type.
4. Configure backup schedule:

```text
Daily Backup
Retention: 30 Days
```

### Monthly Retention

```text
Monthly Backup
Retention: 1 Year
```

### Benefits

- Data protection
- Compliance
- Recovery capabilities

### Free Trial Limitation

Azure Backup could not be configured.

---

# Geo-Redundant Backup Strategy

## Objective

Meet disaster recovery requirements.

### Business Requirement

| Requirement | Target |
|------------|---------|
| RPO | 4 Hours |
| RTO | 8 Hours |

### Production Configuration

1. Configure Geo-Redundant Storage (GRS).
2. Enable cross-region replication.
3. Configure backup replication.
4. Validate restore capabilities.

### Benefits

- Regional disaster protection
- Business continuity
- Improved resilience

### Free Trial Limitation

Geo-redundant backup configuration could not be implemented.

---

# Disaster Recovery Testing

## Objective

Validate recovery procedures.

### Production Configuration

1. Perform test restores.
2. Validate backup integrity.
3. Test recovery process.
4. Measure:
   - Recovery Point Objective
   - Recovery Time Objective
5. Document findings.

### Expected Outcome

| Metric | Requirement |
|----------|------------|
| RPO | 4 Hours |
| RTO | 8 Hours |

---

# Production Security Architecture

```text
Microsoft Entra ID
        │
        ▼
Role-Based Access Control
        │
        ▼
Microsoft Defender for Cloud
        │
        ▼
Microsoft Sentinel
        │
        ▼
Log Analytics Workspace
        │
        ▼
Threat Detection & Monitoring
        │
        ▼
Azure Backup + Recovery Services Vault
        │
        ▼
Geo-Redundant Disaster Recovery
```

---

# Conclusion

The Security, Monitoring, Backup, and Disaster Recovery phase represents a critical component of the Contoso Manufacturing Azure Migration Project. Although Azure Free Trial limitations prevented the deployment of Microsoft Defender for Cloud, Microsoft Sentinel, Azure Backup, Recovery Services Vault, Azure Firewall, centralized logging, vulnerability assessment, and patch management, the complete production architecture and implementation methodology have been documented.

These services would significantly improve the organization's security posture, operational visibility, compliance readiness, and disaster recovery capabilities while supporting the project's requirements for business continuity, threat detection, centralized monitoring, and data protection.
