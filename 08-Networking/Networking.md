# Networking Implementation (Azure Virtual Network Architecture)

## Overview

As part of the **Contoso Manufacturing Azure Migration Project**, the networking layer was designed and partially implemented to establish a secure, segmented, and scalable cloud network environment.

The implementation focuses on enabling secure communication between workloads, restricting unauthorized access, and ensuring private connectivity to Azure PaaS services.

> **Important Disclaimer**  
>
> This project was completed using an Azure Free Trial subscription.  
>
> Due to subscription limitations, the **Azure VPN Gateway could not be deployed**.  
> However, core networking components including Virtual Networks, Subnets, Network Security Groups (NSGs), Azure Bastion, Private Endpoints, Private DNS, and Network Monitoring were implemented or designed as part of the production architecture.

---

# Implementation Sequence

The networking architecture was designed and implemented in the following order:

1. Virtual Network (VNet)  
2. Subnet Configuration  
3. Network Security Groups (NSGs)  
4. Azure Bastion Host  
5. Private Endpoints  
6. Private DNS Zones  
7. Network Monitoring & Diagnostics  
8. VPN Gateway (Design Only – Not Implemented)

---

# Virtual Network (VNet)

## Objective

Establish a secure and isolated network boundary for all Azure resources.

### Implemented Configuration

A Virtual Network was successfully created to support all workloads within the Contoso Manufacturing environment.

### Address Space (Design Requirement)

```text
10.10.0.0/16
```

### Purpose

The VNet provides:

- Network isolation for Azure resources  
- Secure communication between services  
- Foundation for subnet segmentation  
- Support for Private Endpoints and hybrid connectivity  

### Deployment Steps

1. Navigate to Azure Portal  
2. Select **Virtual Networks**  
3. Click **Create**  
4. Configure:
   - Resource Group  
   - Region  
   - Address Space: 10.10.0.0/16  
5. Deploy Virtual Network  

---

# Subnet Configuration

## Objective

Segment the virtual network into logical workload boundaries.

### Implemented Configuration

Subnets were created within the Virtual Network for structured workload isolation.

### Production Design Subnets

```text
Web Subnet         10.10.1.0/24  
App Subnet         10.10.2.0/24  
Database Subnet    10.10.3.0/24  
Management Subnet  10.10.4.0/24  
```

### Purpose

Subnet segmentation enables:

- Workload isolation  
- Controlled traffic flow  
- Security boundary enforcement  
- Scalable network architecture  

---

# Network Security Groups (NSGs)

## Objective

Control inbound and outbound traffic to Azure resources.

### Implemented Configuration

Network Security Groups were deployed and associated with subnets.

### Purpose

NSGs provide:

- Traffic filtering at subnet level  
- Least privilege access control  
- Protection against unauthorized access  
- Network segmentation enforcement  

### Example Rules

| Priority | Rule | Action |
|----------|------|--------|
| 100 | Allow HTTPS (443) | Allow |
| 110 | Allow SQL (1433) | Allow |
| 120 | Allow Bastion Access | Allow |
| 4096 | Deny All Traffic | Deny |

---

# Azure Bastion

## Objective

Provide secure administrative access to virtual machines without exposing public IP addresses.

### Implemented Configuration

Azure Bastion was successfully configured.

### Benefits

- Secure RDP/SSH via Azure Portal  
- No public IP requirement  
- Reduced attack surface  
- Centralized administrative access  

---

# Private Endpoints

## Objective

Secure access to Azure PaaS services using private IP addresses.

### Implemented Configuration

Private Endpoints were configured for secure connectivity to services such as Azure SQL and Storage.

### Purpose

- Eliminates public internet exposure  
- Keeps traffic on Microsoft backbone network  
- Enhances Zero Trust security model  

---

# Private DNS Zones

## Objective

Enable secure and accurate name resolution for Private Endpoint resources.

### Purpose

Private DNS ensures:

- Resolution of private IP addresses  
- Elimination of public endpoint resolution  
- Seamless Private Endpoint connectivity  

### Production DNS Zones

```text
privatelink.database.windows.net  
privatelink.file.core.windows.net  
privatelink.azurewebsites.net  
```

### Implementation Steps

1. Create Private DNS Zone  
2. Link DNS Zone to Virtual Network  
3. Configure automatic resolution  
4. Validate using nslookup  

---

# Network Monitoring & Diagnostics

## Objective

Provide full visibility into network traffic, performance, and security events.

### Purpose

Network monitoring enables:

- Traffic analysis  
- Security auditing  
- Connectivity troubleshooting  
- Performance optimization  

### Production Tools

#### Azure Network Watcher
- Connection Monitor  
- Topology view  
- Packet capture  
- IP flow verification  

#### NSG Flow Logs
- Allowed/denied traffic logging  
- Integration with Log Analytics  

#### Azure Monitor
- Metrics collection  
- Alerting for anomalies  
- Diagnostic logging  

---

# Azure VPN Gateway (Not Implemented)

## Objective

Enable secure hybrid connectivity between on-premises and Azure.

### Free Trial Limitation

Azure VPN Gateway could not be deployed due to subscription restrictions.

---

## Production Design

### Step 1 – Gateway Subnet

```text
GatewaySubnet
```

### Deploy VPN Gateway

- Route-based VPN
- Public IP assignment
- High availability SKU

### Configure Site-to-Site VPN

- On-premises gateway IP
- Shared key configuration
- IPsec/IKE tunnel establishment

### Validate Connectivity

- Test hybrid connectivity
- Verify secure routing between environments  

---

# Networking Architecture (Final Design View)

```text
On-Premises Network
        │
        │ (VPN Gateway – Not Implemented)
        ▼
Azure VPN Gateway (Design Only)
        │
        ▼
Virtual Network (10.10.0.0/16)
        │
 ┌────────┼───────────┬────────────┐
 ▼        ▼           ▼            ▼
Web     App Tier   Database    Management
Subnet   Subnet     Subnet      Subnet
        │
        ▼
NSGs + Private Endpoints + Private DNS
        │
        ▼
Azure PaaS Services (SQL, Storage, App Services)
        │
        ▼
Network Monitoring (Azure Monitor / Network Watcher)
```

---

# Conclusion

The networking layer for the Contoso Manufacturing Azure Migration Project was successfully designed and partially implemented using Azure Virtual Networks, subnets, Network Security Groups, Azure Bastion, Private Endpoints, Private DNS zones, and Network Monitoring services.

Although Azure VPN Gateway could not be deployed due to Azure Free Trial limitations, the full enterprise architecture has been documented to demonstrate how secure hybrid connectivity, centralized monitoring, and private DNS resolution would be implemented in a production environment.

This design follows Azure best practices for **Zero Trust networking, secure connectivity, and enterprise-grade segmentation**.
