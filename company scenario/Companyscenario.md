Company Name: Contoso Manufacturing

Industry: Manufacturing

Employees: 150

Locations:

1 Head Office (Cape Town)
50 Remote Workers
100 Office Workers

Current Environment:

On-Premises Active Directory
Windows File Server (10 TB data)
SQL Database Server
Public Website
Microsoft 365
VPN for remote users

Challenges:

Aging on-premises infrastructure
Limited disaster recovery capabilities
Increasing remote workforce
Need for improved security
High maintenance costs
Need for scalability
Business Requirements
Identity
Users must authenticate using a single identity.
Existing Active Directory must remain operational.
Enable Multi-Factor Authentication (MFA).
Enable Self-Service Password Reset (SSPR).
File Storage
Migrate 10 TB of files to Azure.
Allow secure access from office and remote workers.
Maintain file permissions.
Database
SQL database hosts ERP application.
Database size: 500 GB.
99.9% availability required.
Daily backups required.
Website
Public-facing corporate website.
Receives 5,000 visitors daily.
HTTPS required.
Must remain available during maintenance.
Networking
Secure connection between Azure and Head Office.
Remote workers require secure access.
Segregate workloads using subnets.
Security
MFA for all users.
Centralized logging.
Threat detection.
Least privilege access.
Disaster Recovery
Recovery Point Objective (RPO): 4 hours.
Recovery Time Objective (RTO): 8 hours.
Backup critical workloads.
