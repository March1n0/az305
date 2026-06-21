# Website Migration and Hosting Implementation

## Overview

As part of the **Contoso Manufacturing Azure Migration Project**, a cloud-based web hosting solution was implemented to support the organization's public-facing corporate website.

The project scenario required a highly available web application platform capable of supporting approximately **5,000 daily visitors**, HTTPS connectivity, maintenance without downtime, scalability, and backup capabilities.

The implementation followed Microsoft's recommended deployment sequence by first deploying an App Service Plan, followed by the Web App, HTTPS configuration, and then documenting the production features that could not be implemented due to Azure Free Trial limitations.

> **Important Disclaimer**
>
> This project was completed using an Azure Free Trial subscription.
>
> Due to service limitations and available credits, several enterprise features could not be fully implemented, including:
>
> - SSL Certificate Binding
> - Deployment Slots
> - Autoscaling
> - Website Backups
>
> Where implementation was not possible, the intended production configuration has been documented to demonstrate how the solution would be deployed in an enterprise environment.

---

# Implementation Sequence

The web hosting infrastructure was deployed in the following order:

1. App Service Plan
2. Web App
3. HTTPS Configuration
4. SSL Certificate Configuration (Production Design)
5. Deployment Slots (Production Design)
6. Autoscaling (Production Design)
7. Website Backup Configuration (Production Design)

---

# App Service Plan Deployment

## Objective

Deploy the underlying compute resources required to host the corporate website.

### Implemented Configuration

An Azure App Service Plan was successfully deployed.

### Purpose

The App Service Plan provides:

- Compute resources
- Hosting infrastructure
- Scalability options
- Web application management

### Deployment Steps

1. Navigate to **App Service Plans**.
2. Select **Create**.
3. Configure:
   - Subscription
   - Resource Group
   - App Service Plan Name
   - Region
4. Select pricing tier supported by the subscription.
5. Review configuration.
6. Deploy App Service Plan.

> Screenshots included within this repository demonstrate successful App Service Plan deployment.

---

# Web App Deployment

## Objective

Deploy the public-facing website platform.

### Implemented Configuration

An Azure Web App was successfully deployed.

### Configuration

| Setting | Configuration |
|----------|---------------|
| Operating System | Windows |
| Runtime Stack | Windows |
| Hosting Plan | Azure App Service Plan |
| HTTPS | Enabled |

### Purpose

The Web App provides:

- Public website hosting
- Managed platform services
- Simplified administration
- Secure internet access

### Deployment Steps

1. Navigate to **App Services**.
2. Select **Create Web App**.
3. Configure:
   - Web App Name
   - Subscription
   - Resource Group
   - Publish Method
   - Runtime Stack: Windows
   - Region
   - App Service Plan
4. Review configuration.
5. Deploy Web App.

> Screenshots included within this repository demonstrate successful Web App deployment.

---

# HTTPS Configuration

## Objective

Secure website communication using HTTPS.

### Implemented Configuration

HTTPS was successfully enabled for the Web App.

### Purpose

HTTPS provides:

- Encrypted communication
- Data integrity
- Secure client-server communication
- Industry-standard web security

### Configuration Steps

1. Open Web App.
2. Navigate to **TLS/SSL Settings**.
3. Enable HTTPS Only.
4. Save configuration.
5. Verify secure connectivity.

### Business Requirement Supported

- HTTPS required for public-facing website.
- Improved security posture.

> Screenshots included within this repository demonstrate HTTPS configuration.

---

# SSL Certificate Configuration

## Objective

Provide trusted certificate-based encryption.

### Free Trial Limitation

SSL Certificate binding was not configured due to Azure Free Trial limitations.

### Production Configuration

1. Purchase or import SSL Certificate.
2. Navigate to **TLS/SSL Settings**.
3. Upload certificate.
4. Create custom domain binding.
5. Associate certificate with domain.
6. Validate secure access.

### Business Requirement Supported

- Trusted HTTPS connections.
- Improved website security.
- Professional production deployment.

---

# Deployment Slots

## Objective

Enable website updates without downtime.

### Free Trial Limitation

Deployment Slots were not available within the selected App Service Plan tier.

### Production Configuration

1. Upgrade App Service Plan.
2. Navigate to **Deployment Slots**.
3. Create:
   - Production Slot
   - Staging Slot
4. Deploy updates to staging environment.
5. Perform validation testing.
6. Swap staging into production.

### Benefits

- Zero downtime deployments.
- Safer production releases.
- Simplified rollback process.

### Business Requirement Supported

- Website remains available during maintenance.

---

# Autoscaling Configuration

## Objective

Automatically scale resources based on demand.

### Free Trial Limitation

Autoscaling was not available within the App Service Plan tier used for this project.

### Production Configuration

1. Open App Service Plan.
2. Navigate to **Scale Out (App Service Plan)**.
3. Enable Autoscale.
4. Configure rules:

Example:

- CPU > 70% → Add Instance
- CPU < 30% → Remove Instance

### Benefits

- Supports increased website traffic.
- Optimizes resource utilization.
- Reduces operational costs.

### Business Requirement Supported

- Scalability.
- 5,000 daily visitors.
- Improved performance.

---

# Website Backup Configuration

## Objective

Protect website data and configuration.

### Free Trial Limitation

Website backups were not available within the selected subscription and pricing tier.

### Production Configuration

1. Open Web App.
2. Navigate to **Backups**.
3. Configure Storage Account.
4. Enable automated backups.
5. Configure:
   - Daily backup schedule
   - Retention policy
6. Validate backup completion.

### Backup Strategy

| Backup Type | Retention |
|-------------|------------|
| Daily Backup | 30 Days |
| Monthly Backup | 1 Year |

### Business Requirement Supported

- Disaster Recovery.
- Business Continuity.
- Data Protection.

---

# Production Architecture

```text
Internet Users
       │
       ▼
Azure Web App
       │
       ▼
App Service Plan
       │
       ├── HTTPS Enabled
       ├── SSL Certificate
       ├── Deployment Slots
       ├── Autoscaling
       └── Website Backups
```

---

# Conclusion

The Website Migration phase of the Contoso Manufacturing Azure Migration Project was successfully implemented through the deployment of an Azure App Service Plan and Azure Web App running on the Windows runtime stack with HTTPS enabled.

While Azure Free Trial limitations prevented the implementation of SSL Certificate binding, Deployment Slots, Autoscaling, and Website Backups, the complete production architecture and deployment methodology have been documented to demonstrate how these enterprise features would be configured in a real-world environment.

Screenshots included throughout this repository provide evidence of the successful deployment and configuration of the App Service Plan, Web App, and HTTPS settings.
