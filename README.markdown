# AWS Honeypot Project README

## Overview
This repository contains the documentation and findings from the **AWS Honeypot Project**, conducted by Hector Agwara. The project involves deploying a T-Pot honeypot platform on a Debian 11 AWS instance to capture and analyze cyberattack patterns over a 24-hour period from April 22, 2025, 4:00 AM to April 23, 2025, 4:00 AM. A parallel T-Pot instance was also deployed in Tokyo, Japan, to study the impact of geographic location on attack frequency and behavior.

The full report, titled **AWS Honeypot Observations**, is available in the file `AWS_honeypot_observations.pdf`.

## Purpose
The project aims to:
- Analyze the performance of a T-Pot honeypot in capturing cyberattack data.
- Identify trends, attack patterns, and vulnerabilities exploited by attackers.
- Investigate the influence of geographic location on cyberattack frequency and nature.
- Provide actionable insights for enhancing network security, including identifying weak spots, compromised credentials, and the effectiveness of existing security controls.

## Key Components
The T-Pot platform deploys multiple honeypots, including:
- **Honeytrap**: Emulates various network services (SSH, Telnet, FTP, HTTP, SMTP) to attract and trap attackers.
- **Dionaea**: A low-interaction honeypot emulating vulnerable Windows environments to capture malware and attack payloads.
- **Cowrie**: A high-interaction SSH and Telnet honeypot that records detailed attacker activities, such as login credentials and commands.
- Other honeypots include Tanner, SentryPeer, ADB Honeypot, h0neytr4p, DICOMpot, Mailoney, Redishoneypot, and Conpot, each targeting specific systems or protocols.

## Key Findings
- **Attack Distribution**:
  - **Honeytrap** received the most attacks (15,000; 45%), followed by **Dionaea** (6,445; 42%) and **Cowrie** (614; 4%).
  - Honeytrap's broad protocol support led to higher automated scan hits, while Dionaea's specialized malware capture provided higher-value interactions.
- **Top Exploited CVEs**:
  - CVE-1999-0265 (Windows vulnerability), CVE-2002-0013 (SMTP/FTP flaws), CVE-2021-3449 (OpenSSL bug), and CVE-2019-011500 (Pulse Secure VPN flaw).
  - Common targets included outdated systems, cloud services, and VPNs.
- **Attack Sources**:
  - Major sources included the United States (Charter Communications, AWS, Linode), Ethiopia (Ethio Telecom), Russia (Rostelecom), and Bolivia (AXS Bolivia, Entel).
  - Cloud-hosted attacks (e.g., AWS AS16509) and residential networks (e.g., Charter Communications) were prevalent.
  - Countries like China (29%), the United States (20%), and India (18%) were top sources for Cowrie attacks.
- **Attack Patterns**:
  - Common usernames (e.g., admin, root, user) and passwords (e.g., none, 123456, password) were highly predictable and vulnerable to dictionary attacks.
  - Telnet was used more frequently than SSH, likely due to its plaintext nature and lower traceability.
  - Attack peaks occurred at 10 AM and 8 PM, with consistent activity throughout the day.
- **Suricata Alerts**:
  - Top alerts included DoublePulsar backdoor (12,796 hits), Nmap SYN scans (749 hits), and SSH-related anomalies (e.g., invalid banners, unusual ports).

## Recommendations
- **Patch Management**: Prioritize patching known vulnerabilities, especially in older systems (e.g., Windows, OpenSSL).
- **Strong Credentials**: Enforce unique, strong usernames and passwords with multi-factor authentication (MFA) for SSH, Telnet, and RDP.
- **Traffic Filtering**: Block traffic from high-risk regions (e.g., Ethiopia, Bolivia) and suspicious IPs (e.g., Ethio Telecom, Rostelecom).
- **Port Monitoring**: Monitor unusual port activity (e.g., 445/SMB, 2103/VoIP, 1900/UPnP) to detect attacks early.
- **Proactive Measures**: Conduct regular vulnerability scans, share threat intelligence, and deploy honeypots to study emerging threats.

## Future Trends
- Increased abuse of cloud infrastructure (e.g., AWS, Linode) for attacks.
- Growing targeting of IoT devices and industrial control systems due to weak security.
- Higher attack volumes from regions with lax cybersecurity regulations (e.g., Ethiopia, Bolivia).

## Challenges
- **Data Extraction**: Issues with Elasticvue servers due to strict request formatting.
- **Cost**: The AWS instance cost ($0.24/hour, $5.76/day) was significant and requires optimization for long-term deployments.

## Repository Contents
- **AWS_honeypot_observations.pdf**: The full report detailing the honeypot setup, statistics, analysis of top honeypots (Honeytrap, Dionaea, Cowrie), exploited CVEs, attacker IP analysis, and recommendations.
- **README.md**: This file, providing an overview of the project and key findings.

## How to Use
1. **Review the Report**: Read `AWS_honeypot_observations.pdf` for detailed insights into the honeypot experiment and attack analysis.
2. **Replicate the Setup**: Deploy T-Pot on a Debian 11 AWS instance using the official T-Pot documentation (https://github.com/telekom-security/tpotce).
3. **Analyze Data**: Use Elastic and Kibana for log analysis and visualization, as described in the report.
4. **Apply Recommendations**: Implement the suggested security measures to protect your network.

## Contact
For questions or further details, contact Hector Agwara at [insert contact information, if available].

## License
This project is for educational and research purposes. No specific license is provided; use the findings responsibly to enhance cybersecurity practices.