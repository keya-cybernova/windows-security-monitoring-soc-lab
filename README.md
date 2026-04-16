# Windows Security Monitoring & SOC Lab

## 🔍 Project Overview

This project focuses on enhancing Windows security through advanced log monitoring, audit policy configuration, and automated reporting in a simulated SOC (Security Operations Center) environment.

The objective was to detect unauthorized access attempts, monitor system activity, and generate real-time security insights using PowerShell automation and IIS-based reporting.

---

## 🎯 Objectives

* Monitor failed and successful login attempts
* Track command execution and system activity
* Automate log analysis and reporting
* Improve visibility into potential security threats

---

## 🛠️ Tools & Technologies

* Windows Server (Virtual Machine)
* Event Viewer
* Group Policy (Advanced Audit Policy Configuration)
* PowerShell
* IIS Web Server
* HTML Reporting

---

## ⚙️ Key Configurations

### 1. Advanced Audit Policy Configuration

* Enabled auditing for:

  * Logon/Logoff events
  * Account logon events
  * Process creation and termination
  * Object access and privilege usage

---

### 2. Logon Failure Analysis

* Monitored **Event ID 4625** (failed login attempts)
* Identified suspicious login behavior and potential intrusion attempts
* Analyzed timestamps, usernames, and login sources

---

### 3. Command & Process Monitoring

* Enabled process tracking using:

  * **Event ID 4688 (Process Creation)**
  * **Event ID 4689 (Process Termination)**
* Captured executed commands such as `ping` and system applications

---

### 4. Tracking Successful Logins

* Used **Event ID 4624** to monitor legitimate user access
* Developed PowerShell scripts to filter and analyze login activity

```powershell
Get-EventLog -LogName Security | Where-Object {$_.EventID -eq 4624}
```

---

### 5. Automated Log Analysis (PowerShell)

* Created custom script: `login_info.ps1`
* Extracted:

  * Username
  * Login time
  * Source

---

### 6. Web-Based Reporting (IIS)

* Generated automated HTML reports from security logs
* Hosted reports using IIS web server

```powershell
Get-EventLog Security | ConvertTo-Html > C:\inetpub\wwwroot\security_report.html
```

* Enabled continuous monitoring with scheduled script execution

---

### 7. Network & Access Configuration

* Configured firewall rules for port **8080**
* Implemented port forwarding using:

```bash
netsh interface portproxy add v4tov4 listenport=8080 listenaddress=127.0.0.1 connectport=80 connectaddress=127.0.0.1
```

---

## 🔐 Key Findings

* Detected multiple failed login attempts (potential brute-force indicators)
* Observed command execution activity via process logs
* Identified patterns in legitimate user logins
* Demonstrated centralized monitoring and reporting

---

## 📊 Outcome

This project demonstrates practical SOC skills including:

* Log monitoring
* Threat detection
* Security automation
* Incident visibility

---

## 📌 Conclusion

By combining audit policies, event log analysis, and automated reporting, this project provides a strong foundation for real-world security monitoring and incident response in Windows environments.

- 
# 📸 Sample Output

### 🖥️ Web-Based Security Report (IIS)
![IIS Report](iis-security-report.png)

### ⚙️ PowerShell Log Analysis
![PowerShell Output](powershell-output.png)

### 📊 Event Viewer Logs
![Event Viewer](event-viewer-logs.png)
