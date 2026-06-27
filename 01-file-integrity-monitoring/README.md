# 📁 File Integrity Monitoring with Wazuh

## Project Objective

The goal of this project was to configure and validate File Integrity Monitoring (FIM) using Wazuh. By monitoring a designated directory, Wazuh detects changes to files and generates alerts that help security analysts identify potentially unauthorized activity on an endpoint.

---

# Lab Environment

| Component      | Technology                      |
| -------------- | ------------------------------- |
| SIEM           | Wazuh                           |
| Endpoint       | Windows                         |
| Virtualization | VirtualBox                      |
| Monitoring     | File Integrity Monitoring (FIM) |

---

# Configuring File Integrity Monitoring

The first step was configuring Wazuh to monitor a custom directory for file changes. This was done by editing the **ossec.conf** configuration file and adding the directory that I wanted Wazuh to monitor.

After updating the configuration, I restarted the Wazuh agent so the new settings would take effect.

### Wazuh Configuration


![Wazuh Configuration](screenshots/ossec.config)

---

# Modifying a Monitored File

With File Integrity Monitoring configured, I modified the contents of a file located inside the monitored directory.

This simulated a real-world scenario where a critical system file is changed. While not every file modification is malicious, unexpected changes can be an early indicator of unauthorized activity or system compromise.

### Modified File


![Modified File](screenshots/modified-file)

---

# Alert Detection

Almost immediately after saving the file, Wazuh generated a File Integrity Monitoring alert.

The alert confirmed that Wazuh successfully detected the modification and recorded important information that could assist a SOC analyst during an investigation.

### Wazuh Alert

*Insert screenshot of the generated alert.*

![Wazuh Alert](screenshots/wazuh-alert1)

---

# MITRE ATT&CK Mapping

Wazuh automatically enriched the alert by mapping it to the MITRE ATT&CK framework.

MITRE ATT&CK provides a standardized way to categorize attacker behaviors, giving analysts additional context about the type of activity that generated the alert. While this file modification was expected as part of testing, the MITRE mapping demonstrates how Wazuh helps analysts quickly understand the nature of security events.

### MITRE ATT&CK Information


![MITRE ATT\&CK](screenshots/mitre-class)

---

# Event Details

The generated alert contained several pieces of information that are valuable during an investigation, including:

* Event ID
* Rule ID
* Rule Level
* Agent Name
* File Path
* Timestamp
* Alert Description

For this event, Wazuh assigned a **Rule Level of 7**, which represents a **medium-severity** alert. A Level 7 event does not necessarily indicate malicious activity on its own, but it is significant enough to warrant review by a security analyst. In this case, the alert confirmed that Wazuh successfully detected a modification to a monitored file exactly as expected.

### Event Details


![Event Details](screenshots/event-specifics)

---

# Results

This project successfully demonstrated that Wazuh can detect changes made to monitored files in near real time.

After modifying a file, Wazuh generated a detailed alert containing contextual information such as the affected file path, severity level, timestamp, and MITRE ATT&CK mapping. These details provide analysts with the information needed to investigate file integrity events efficiently.

---

# Skills Demonstrated

* Wazuh SIEM Administration
* File Integrity Monitoring (FIM)
* Linux Administration
* Endpoint Monitoring
* Security Event Analysis
* MITRE ATT&CK Framework
* Alert Investigation
* SOC Workflow Fundamentals

---

# What I Learned

This project gave me practical experience configuring File Integrity Monitoring within Wazuh and interpreting the alerts it generated.

One of the biggest takeaways was seeing how quickly Wazuh detected file modifications and enriched the alert with useful investigation data such as the Rule Level, Event ID, and MITRE ATT&CK mapping. Working through this lab helped me better understand how SIEM platforms support Security Operations Center (SOC) analysts by providing visibility into endpoint activity and helping prioritize events that may require investigation.

---

# Conclusion

This lab reinforced the importance of continuous endpoint monitoring and showed how File Integrity Monitoring can be used to detect unexpected changes to critical files. Although the modification performed in this project was intentional for testing purposes, the same detection process can help organizations identify unauthorized system changes, investigate suspicious activity, and respond to potential security incidents.
