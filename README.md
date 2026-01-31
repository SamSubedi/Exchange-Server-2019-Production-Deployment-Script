# Exchange-Server-2019-Production-Deployment-Script
Exchange 2019 Production Deployment Script

Fully automated, enterprise-grade PowerShell script to deploy Exchange Server 2019 (Mailbox Role) on Windows Server 2016–2025

Overview

This script is designed for large organizations and provides a production-ready, fully automated deployment of Exchange Server 2019 CU15, including:

Active Directory & Schema validation

TLS 1.2 / TLS 1.3 configuration based on server version

Automatic installation of prerequisites (Windows Features, Visual C++ runtimes)

Performance optimization (High-Performance power plan, pagefile settings)

Automatic download and silent installation of Exchange 2019

Detailed logging for auditing and troubleshooting

⚠️ Note: This script installs the Mailbox Role only. Edge Transport or hybrid configurations require separate setup.

Supported Operating Systems
Operating System	TLS Support	Notes
Windows Server 2016	TLS 1.2	TLS 1.3 not supported
Windows Server 2019	TLS 1.2	TLS 1.3 not supported
Windows Server 2022	TLS 1.2 + TLS 1.3	Fully supported
Windows Server 2025	TLS 1.2 + TLS 1.3	Fully supported
Pre-Deployment Checklist
Task	Required	Notes
Server domain-joined	✅	Exchange cannot install on a workgroup
AD Schema updated for Exchange 2019	✅	Schema version ≥ 88
Sufficient CPU, RAM, and Disk	✅	Script sets pagefile automatically
Backup of server and AD	✅	Always recommended before production deployment
Network prerequisites	✅	DNS, firewall, and required ports configured
Dedicated server for Mailbox role	✅	Avoid conflicts with other roles
Lab testing (optional but recommended)	✅	Verify script in non-production environment
Features

Active Directory & Schema Validation

Checks domain join and AD Schema version

Prevents deployment on unsupported environments

Prerequisite Installation

Installs all required Windows Features for Mailbox Role

Installs Visual C++ 2013 & 2015–2022 runtimes automatically

Performance Optimization

Sets High-Performance power plan

Configures pagefile = RAM + 10MB (max 32GB)

TLS & Security Configuration

Enables TLS 1.2 on all supported OS

Enables TLS 1.3 on Windows Server 2022/2025

Disables legacy protocols: TLS 1.0, TLS 1.1, SSL 3.0

Exchange Installation

Downloads Exchange 2019 CU15 ISO if missing

Mounts ISO and installs Mailbox Role silently

Target path: E:\Exchange (configurable)

Logs installation details for auditing

Production Logging

Creates timestamped log file in the script directory

Captures all actions for troubleshooting

Usage

Copy the script to the target server.

Run PowerShell as Administrator.

Execute the script:

.\Exchange2019-ProdDeploy.ps1


Follow any prompts (most steps are automated).

Check the log file in the script directory for detailed status.

Recommended Deployment Flow

Verify domain join and AD Schema readiness.

Run script on a dedicated server for Mailbox Role.

Confirm prerequisites, TLS, and performance settings applied.

Exchange installation completes silently to E:\Exchange.

Post-installation:

Configure mailbox databases and DAGs (if applicable)

Configure certificates and SMTP connectors

Apply Exchange updates as needed

Verify logs for errors

Best Practices for Large Organizations

Test the script in a lab environment first.

Always run on dedicated Mailbox servers.

Ensure firewalls, DNS, and backups are properly configured.

Plan mailbox storage and DAG topology before deployment.

Use log files to verify all steps completed successfully.

Maintain the script and ISO for future CU updates.

Disclaimer

This script is provided as-is. While it is designed for production, administrators are responsible for verifying:

AD readiness

Hardware resources

Backups

Compliance with organizational policies
