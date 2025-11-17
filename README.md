    #TASK-3 — Vulnerability Scan Using Nessus Essentials

Introduction:
This task involved performing a full vulnerability assessment using Nessus Essentials.
The installation, configuration, scanning, and analysis were carried out on a Kali Linux machine, which acted as both the scanner host and the scan target

      Step 1: Installation of Nessus Essentials (Linux)
1. Download Nessus:
Visited the official Tenable Nessus Essentials download page:
https://www.tenable.com/products/nessus/nessus-essentials
Registered using an email address and received the Activation Code.
Downloaded the Debian (.deb) package suitable for Kali Linux.

2. Install Nessus:
Navigated to the Downloads directory and installed the package:
cd Downloads
ls
sudo dpkg -i <nessus-package-name>.deb

Start & Enable Service:
sudo systemctl start nessusd.service
sudo systemctl enable nessusd.service

Access Nessus Web UI:
Opened a browser and accessed
https://localhost:8834
Selected Nessus Essentials, entered the activation code, created the Nessus user account, and waited for 20–45 minutes until all plugins were downloaded.

     Step 2: Identifying Local Machine IP
The IP address of the Linux machine was identified using:
ip addr show
IP ADDRESS:10.131.XX.XX
This address was used as the target for the vulnerability scan.
 
    Step 3: Creating & Running the Scan
1. Creating the Scan
Opened Scans → New Scan
Selected Basic Network Scan

Configured:
Name:Local Machine Vulnerability Scan

Target:10.131.x.x (local machine IP)

2. Launching the Scan
Saved the configuration.
Clicked Launch to start the scan.
The scan ran for 30–60 minutes, depending on system resources.

       Step 4: Reviewing Results

After completion, the report was reviewed based on:
Severity levels (Critical, High, Medium, Low, Info)
Plugin details
Impact descriptions
Recommended remediation
A total of 69 vulnerabilities were detected across multiple categories (Misc., Databases, Web Servers, General, Service Detection, etc.

    Step 5: Mitigation Research for Selected Vulnerabilities

Five vulnerabilities were selected and analyzed. Appropriate, simple mitigation steps were researched as follows:

1. Python Brotli ≤ 1.1.0 DoS
Issue: Malformed Brotli input can cause denial-of-service crashes.
Fix: Update Brotli package to the latest secure version.
Mitigation: Avoid using outdated compression libraries.

2. PostgreSQL Multiple Issues
Issue: Outdated PostgreSQL instance with multiple security flaws.
Fix: Upgrade PostgreSQL to the newest stable version.
Mitigation: Restrict network access; enforce strong authentication policies.

3. Ruby REXML DoS
Issue: XML parsing vulnerability causing high CPU usage.
Fix: Update Ruby REXML to the patched version.
Mitigation: Avoid processing untrusted XML.

4. SSL/TLS Multiple Issues
Issue: Weak encryption protocols and deprecated cipher suites enabled.
Fix: Disable TLS 1.0/1.1, remove weak ciphers, enforce strong TLS 1.2/1.3.
Mitigation: Use industry-recommended cryptographic configurations.

5. SSH Multiple Issues
Issue: Weak SSH configuration and outdated settings.
Fix: Disable root login, disable obsolete ciphers/MACs, enforce key-based authentication.
Mitigation: Restrict SSH to trusted networks only.

       Step 6: Documentation
All procedures, screenshots, and vulnerability data were organized and uploaded to the repository in a separate folder for reference.

Conclusion

This task successfully demonstrated the process of installing, configuring, and running a vulnerability scan using Nessus Essentials.
Critical and high-risk vulnerabilities were identified and appropriate mitigation steps were researched.
The findings provide a strong foundation for improving system security and understanding real-world vulnerability assessment workflows.
