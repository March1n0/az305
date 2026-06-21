# Identity and Governance Implementation
### Overview

As part of the Contoso Manufacturing Azure Migration Project, the Identity and Governance components were implemented first to establish a secure and scalable foundation for the environment.

The implementation follows Microsoft's recommended cloud adoption approach, where governance and identity are configured before deploying workloads and services.

### Important Disclaimer

This project was completed using an Azure Free Trial subscription. Due to licensing and subscription limitations, some enterprise features such as Microsoft Entra ID Premium P1/P2 capabilities, Conditional Access, Self-Service Password Reset (SSPR), Multi-Factor Authentication (MFA) enforcement, and Hybrid Identity integration with on-premises Active Directory could not be fully implemented.

Where implementation was not possible, detailed design and deployment procedures have been provided to demonstrate how the solution would be configured in a production environment.

## Management Group Hierarchy
### Purpose

Management Groups provide governance and allow organizations to organize Azure subscriptions according to business units, departments, or environments.

For the Contoso Manufacturing scenario, five departmental Management Groups were created:

- Finance
- HR
- IT
- Operations
- Sales
### Why Management Groups Were Created First

Management Groups sit above subscriptions within Azure's hierarchy and allow administrators to:

Apply governance policies
Manage access centrally
Control resource organization
Simplify enterprise-scale administration
### Azure Hierarchy Implemented
```
Tenant Root Group
│
├── Finance
├── HR
├── IT
├── Operations
└── Sales
```
### Implementation Process
Logged into the Azure Portal.
Navigated to **Management Groups**.
Created each departmental Management Group individually.
Verified the hierarchy structure.
Captured screenshots as evidence of successful deployment.

Screenshots included within this repository demonstrate the Management Group hierarchy.

## Subscription Assignment
Purpose

Subscriptions provide a billing, access control, and resource boundary within Azure.

### Intended Production Design

Under normal enterprise conditions, each department would have its own subscription:
```
Finance Management Group
└── Finance Subscription

HR Management Group
└── HR Subscription

IT Management Group
└── IT Subscription

Operations Management Group
└── Operations Subscription

Sales Management Group
└── Sales Subscription
```
### Free Trial Limitation

The Azure Free Trial subscription only allowed the creation of a single subscription.

Therefore, only one subscription was available for use during the implementation.

#### Result

The subscription was positioned beneath the Management Group hierarchy for demonstration purposes.

This limitation does not affect the architectural design of the solution but restricts the ability to fully simulate a multi-subscription enterprise environment.

## Security Group Creation
### Purpose

Security Groups simplify access management by allowing permissions to be assigned to groups rather than individual users.

The following Security Groups were created:

- Finance
- HR
- IT
  
#### Implementation Process
1. Navigated to Microsoft Entra ID.
2. Selected **Groups**.
3. Created Security Groups.
4. Assigned appropriate group names.
5. Prepared groups for future role-based access assignments.
   
#### Intended Usage

These groups would be used to:

- Assign Azure RBAC permissions
- Apply Conditional Access Policies
- Scope MFA requirements
- Enable Self-Service Password Reset
- Delegate administrative responsibilities

## User Creation
### Scenario Requirement

The project scenario specifies:

- 150 employees
- 100 office workers
- 50 remote workers

Creating all 150 users manually would not provide additional architectural value within a lab environment.

Therefore, a representative sample was created to demonstrate the identity deployment process.

#### Users Created
**Internal Users**
- Adam
- Armand
- John
  
**Guest User**
- Marchino
#### Purpose of User Types
**Internal Users**

Internal users represent Contoso Manufacturing employees who would access:

- Microsoft 365
- Azure Resources
- File Shares
- Applications
  
**Guest User**

The guest account demonstrates Azure B2B collaboration capabilities and external identity access.

Examples include:

- Contractors
- Vendors
- Business Partners
#### User Creation Process
1. Navigated to Microsoft Entra ID.
2. Selected **Users**.
3. Chose **New User**.
4. Created internal member accounts.
5. Created guest account.
6. Verified successful account creation.
7. Captured screenshots for project evidence.

Screenshots included within this repository demonstrate user creation and account configuration.

## Multi-Factor Authentication (MFA)
### Business Requirement

The project requires:

- MFA for all users
- Improved security posture
- Protection against credential compromise
#### Intended Production Configuration

If licensing were available, MFA would be implemented as follows:

#### Configuration Steps
1. Purchase Microsoft Entra ID Premium P1 licensing.
2. Navigate to Microsoft Entra Admin Center.
3. Enable MFA registration.
4. Configure authentication methods:
-  Microsoft Authenticator
-  SMS
- Voice Call
5. Create a Conditional Access Policy.
6. Require MFA for all users.
#### Expected Result

All users would be required to provide:

- Password
- Secondary authentication factor

before accessing Azure resources.

**Limitation**

MFA enforcement through Conditional Access could not be implemented due to Azure Free Trial licensing limitations.

## Self-Service Password Reset (SSPR)
### Business Requirement

Users must be able to reset passwords without Help Desk intervention.

#### Intended Production Configuration
**Configuration Steps**
1. Navigate to Microsoft Entra ID.
2. Select Password Reset.
3. Enable SSPR for selected groups.
4. Configure authentication methods.
5. Require registration during sign-in.
6. Test password reset functionality.
#### Security Groups Used

The previously created Security Groups would be targeted:

- Finance
- HR
- IT

This allows password reset functionality to be enabled in a controlled and scalable manner.

**Limitation**

SSPR requires Microsoft Entra ID Premium licensing and therefore could not be fully implemented in the Azure Free Trial environment.

## Conditional Access Policies
### Business Requirement

Contoso Manufacturing requires:

- MFA enforcement
- Secure remote access
- Risk reduction
- Least privilege access
#### Intended Production Configuration
**Example Policy 1**

**Require MFA for All Users**

Assignments:

- Finance Group
- HR Group
- IT Group

Grant Controls:

- Require MFA

**Example Policy 2**

**Remote Worker Protection**

Assignments:

- Remote Users

Conditions:

- Any external network

Grant Controls:

- Require MFA
  
**Example Policy 3**

**Block Legacy Authentication**

Assignments:

- All Users

Action:

- Block Access
  
**Example Policy 4**

**Administrative Access Protection**

Assignments:

- IT Administrators

Grant Controls:

- Require MFA
- Require Compliant Device
  
**Limitation**

Conditional Access requires Microsoft Entra ID Premium P1 licensing and was therefore not available within the Azure Free Trial subscription.

## Hybrid Identity Integration
### Business Requirement

The project requires:

- Existing Active Directory remains operational.
- Single identity across cloud and on-premises resources.
#### Intended Production Configuration
**Components**
- On-Premises Active Directory
- Microsoft Entra Connect
- Microsoft Entra ID
  
**Configuration Process**
1. Deploy Domain Controller.
2. Install Microsoft Entra Connect.
3. Configure synchronization.
4. Verify user synchronization.
5. Enable Hybrid Identity.
   
**Expected Result**

Users would sign in with one identity for:

- Microsoft 365
- Azure Resources
- On-Premises Resources
- ERP Applications
  
**Limitation**

An on-premises Active Directory environment was not available within the project lab. Therefore, Microsoft Entra Connect and Hybrid Identity synchronization could not be demonstrated.

### Conclusion

The Identity and Governance phase successfully established the foundational Azure structure for the Contoso Manufacturing migration project. Management Groups, Security Groups, and user accounts were successfully deployed and configured according to the project requirements. While Azure Free Trial limitations prevented the implementation of enterprise features such as MFA, SSPR, Conditional Access, and Hybrid Identity, the architecture, implementation approach, and configuration methodology have been fully documented to demonstrate how these services would be deployed in a production enterprise environment. Screenshots included throughout this repository provide evidence of the Management Group hierarchy, subscription structure, security groups, and user account creation.
