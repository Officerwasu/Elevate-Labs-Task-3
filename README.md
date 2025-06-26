# Elevate Labs Cyber Security Internship - Task 3: Basic Vulnerability Scan

## Objective
The objective of this task was to perform a basic vulnerability scan on my personal computer using free tools to identify common vulnerabilities.

## Tools Used
* **Greenbone Community Edition (OpenVAS)**: A free and open-source vulnerability scanner, as recommended by the task.

## Task Steps & Process


### 1. Install OpenVAS or Nessus Essentials.
* I chose to install Greenbone Community Edition (OpenVAS) on my Kali Linux system.
* The installation process involved using `sudo apt install openvas`, which informed that `gvm` would be installed instead of `openvas`.
* Dependencies such as `gvm`, `greenbone-feed-sync`, `greenbone-security-assistant`, `gsad`, and `gvm-tools` were installed.
* Following the installation, `sudo gvm-setup` was executed to configure the Greenbone environment, including starting the PostgreSQL service.
* Screenshots of the installation process are included in the `screenshots/` directory.

### 2. Set up scan target as your local machine IP or localhost.
* After accessing the Greenbone Security Assistant (GSA) web interface (typically at `https://192.168.0.1`), I navigated to the "Tasks" section.
* A "New Task" was created, named "My pc scan".
* The scan target was explicitly set to `localhost`.
* A screenshot illustrating the task creation and target setup is provided.

### Vulnerability scanning.
* Once the new task was configured, the scan was initiated from the Greenbone web interface.
* The scan's progress could be monitored in the "Reports" section.
* The scan ran for a period of time, and its completion was confirmed by checking the status in the "Reports" section.
* The report indicated a status of "Done" and provided a summary of findings.

### Vulnerabilities and severity.
* Upon completion, the generated report provided an overview of vulnerabilities by severity class (High, Medium, Low) and CVSS scores.
* A detailed list of vulnerabilities was reviewed, showing the name, associated CVEs, host IP, severity, EPSS score, location (port/protocol), and creation time.


### Document the most critical vulnerabilities.

Based on the scan results, the following are the most critical and notable vulnerabilities identified:

* **High Severity (CVSS 7.5):**
    * **SSL/TLS: Report Vulnerable Cipher Suites for HTTPS**: This indicates that the system is supporting weak cryptographic cipher suites over HTTPS. Associated CVEs include CVE-2016-2183, CVE-2016-6329, and CVE-2020-12872.
        * **Proposed Mitigation**: Configure web servers and applications to disable weak cipher suites and use only strong, modern ciphers (e.g., AES-256 GCM, ECDHE) with forward secrecy.

* **Medium Severity:**
    * **SSL/TLS: Deprecated SSLv2 and SSLv3 Protocol Detection**: The scan detected the use of outdated and insecure SSLv2 and SSLv3 protocols, making the system vulnerable to attacks like POODLE. Associated CVEs: CVE-2016-0800, CVE-2014-3566.
        * **Proposed Mitigation**: Disable SSLv2 and SSLv3 protocols entirely in server configurations (e.g., Apache, Nginx, etc.).
    * **SSL/TLS: Report Weak Cipher Suites**: Similar to the high severity finding, this points to the use of cipher suites known to be weak. Associated CVEs: CVE-2013-2566, CVE-2015-2808, CVE-2015-4000.
        * **Proposed Mitigation**: Regularly update server configurations to remove weak cipher suites and prioritize strong, industry-standard ciphers.
    * **Weak Key Exchange (KEX) Algorithm(s) Supported (SSH)**: The SSH service on the system is supporting insecure key exchange algorithms.
        * **Proposed Mitigation**: Configure the SSH server (`sshd_config`) to disable weak KEX algorithms and enable only strong, modern ones.
    * **SSL/TLS: Deprecated TLSv1.0 and TLSv1.1 Protocol Detection**: The system is still using older versions of TLS (1.0 and 1.1) which have known vulnerabilities. Associated CVEs: CVE-2011-3389, CVE-2015-0204.
        * **Proposed Mitigation**: Disable TLSv1.0 and TLSv1.1 protocols and ensure only TLSv1.2 or TLSv1.3 are enabled.
    * **Boa Webserver Terminal Escape Sequence in Logs Command Injection Vulnerability (CVE-2009-4496)**: This indicates a potential command injection vulnerability in the Boa web server related to how it handles terminal escape sequences in logs.
        * **Proposed Mitigation**: If the Boa webserver is in use, update it to the latest patched version. If not needed, disable or remove it.

### Take screenshots of the scan results.
Screenshots documenting the entire process, from installation to the final scan results, are included in the `screenshots/` directory within this repository.

* ![Greenbone (OpenVAS) Installation and Setup](https://github.com/user-attachments/assets/558f9922-c832-4a21-88f7-d6354fcadbfe)
* ![Greenbone Dashboards - Initial View](https://github.com/user-attachments/assets/6857e851-4280-4f81-9f86-714e237a526a)
* ![Creating a New Scan Task](https://github.com/user-attachments/assets/b109caeb-196a-4f84-80f9-7cccf520fe54)
* ![Scan Reports Overview](https://github.com/user-attachments/assets/7fed5a64-0044-4ffa-8051-3f624e9c7eac)
* ![Detailed Vulnerability List](https://github.com/user-attachments/assets/f8b509a4-ec3f-4194-ab7c-ec0e9a5d034d)

## Outcome
This task provided valuable introductory vulnerability assessment experience and enhanced my understanding of common PC risks and the use of security tools like OpenVAS/Greenbone.

## Key Concepts Explored
* Vulnerability scanning
* Risk assessment
* CVSS (Common Vulnerability Scoring System)
* Remediation
* Security tools
