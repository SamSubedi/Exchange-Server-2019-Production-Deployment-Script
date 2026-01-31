# Exchange Server 2019 Production Deployment Script
# Fully automated, enterprise-grade PowerShell script to deploy Exchange Server 2019 (Mailbox Role) on Windows Server 2016, 2022 and 2025.
# This script is designed for large organizations and provides a production-ready, fully automated deployment of Exchange Server 2019 CU15. It handles everything from initial server checks to installing prerequisites, configuring security, and silently installing Exchange, ensuring a smooth production deployment.


# The script automates the following key tasks:

- Validates Active Directory and schema readiness.

- Installs all Windows prerequisites required for Exchange 2019 Mailbox Role.

- Configures TLS 1.2 or 1.3 depending on server OS.

- Applies performance optimizations including high-performance power plan and pagefile configuration.

- Automatically downloads Exchange 2019 CU15 ISO and installs it silently.

- Generates detailed log files for auditing and troubleshooting.

⚠️ Note: This script installs only the Mailbox Role. Edge Transport or hybrid configurations must be set up separately.



# Supported Operating Systems: The script supports the following Windows Server versions:

- Windows Server 2016: TLS 1.2 only (TLS 1.3 not supported)

- Windows Server 2019: TLS 1.2 only (TLS 1.3 not supported)

- Windows Server 2022: TLS 1.2 + TLS 1.3 fully supported

- Windows Server 2025: TLS 1.2 + TLS 1.3 fully supported


# Pre-Deployment Checklist
# Before running the script, ensure the following:

- The server is domain-joined; Exchange cannot install on a workgroup.

- Active Directory Schema is updated for Exchange 2019 (schema version ≥ 88).

- Server hardware meets requirements (CPU, RAM, Disk). The script sets pagefile automatically.

- A full backup of the server and AD is available.

- Network prerequisites such as DNS, firewall, and required ports are configured.

- The server is dedicated to the Mailbox Role to avoid conflicts.

- Optional but recommended: test the script in a lab environment before production deployment.



# Key Features:

- Active Directory & Schema Validation: Ensures the server is domain-joined and schema supports Exchange 2019.

- Prerequisite Installation: Installs required Windows Features and Visual C++ runtimes automatically.

- Performance Optimization: Sets high-performance power plan and configures pagefile = RAM + 10MB (max 32GB).

- TLS & Security: Enables TLS 1.2 for all OS, TLS 1.3 for 2022/2025, disables legacy protocols (TLS 1.0, TLS 1.1, SSL 3.0), and enforces strong .NET cryptography.

- Exchange Installation: Downloads Exchange 2019 CU15 ISO if missing, mounts it, installs the Mailbox Role silently, and logs every step. Target path: E:\Exchange (configurable).

- Production Logging: Creates timestamped log files in the script directory for auditing and troubleshooting.



# Usage Instructions:

- Copy the script to the target server.

- Run PowerShell as Administrator.

- Execute the script: .\Exchange2019-ProdDeploy.ps1

- Follow any prompts (most steps are automated).

- After completion, check the log file in the script directory for detailed status.



# Recommended Deployment Flow:

- Verify the server is domain-joined and AD Schema is updated.

- Run the script on a dedicated Mailbox server.

- Confirm all prerequisites, TLS, and performance settings are applied successfully.

- Exchange installation completes silently to E:\Exchange.



# After installation:

- Configure mailbox databases and DAGs if applicable.

- Configure certificates and SMTP connectors.

- Apply latest Exchange updates as needed.

- Verify the logs for any errors or warnings.

- Best Practices for Large Organizations

- Test the script in a lab environment before production deployment.

- Run only on dedicated Mailbox servers to avoid role conflicts.

- Ensure firewalls, DNS, and backups are properly configured.

- Plan mailbox storage and DAG topology before deployment.

- Use log files to verify all steps completed successfully.

- Maintain the script and Exchange ISO for future CU updates.


# Disclaimer:
# This script is provided as-is. While it is designed for production environments, administrators are responsible for verifying:

- Active Directory readiness

- Hardware resources

- Backups

- Compliance with organizational policies
