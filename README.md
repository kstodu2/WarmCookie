# Wireshark Lab: WarmCookie, Network Traffic Analysis.

This lab exercise demonstrates the capture and analysis of network traffic using Wireshark, with a focus on identifying suspicious activity and understanding packet communication.

---
## Background
A Windows host was infected, and it seems to be from WarmCookie malware.

## Objective
- Executive Summary: State in simple, direct terms what happened (when, who, what).
- Victim Details: Details of the victim (hostname, IP address, MAC address, Windows user account name).
- Indicators of Compromise (IOCs): IP addresses, domains and URLs associated with the activity.  SHA256 hashes if any malware binaries can be extracted from the pcap.

---

## Lab Setup
- **Environment:** KaliVM 2026.1
- **Tools:** Wireshark 4.6.4, Virustotal


---

## Methodology
1. Analyze Conversations and Endpoints to find any out of ordinary.
![Conversations](screenshots/2-Conversationspng.png) ![Endpoints](screenshots/2-Endpoints.png) 
2. Apply filter to isolate traffic from potentially impacted machine. ![PotentialCulprit](screenshots/3-Culprit.png)
3. Examined hosts on VirusTotal for any finding & reports. 
4. Follow HTTP Stream from infected machine to a malicious host. Leading to a Phishing Email with Invoice zip attachment. ![PotentialCulprit2](screenshots/3-culprit2.0.png)
5. Extract the packet and check its hash on Virustotal to confirm that the attachment has malicious code.
6. Extract the packet destined to suspicious IP (72.5.43.29) to analyze the code.


---

## Findings
- At 2024-08-14 19:11:04.072, Pierce Lucero, @ DESKTOP-H8ALZBV.local, MAC: 00:1c:bf:03:54:82, IP: 10.8.15.133, attempted to download an attachment from an email. By doing so user was redirected to a typosquatting website called quote.checkfedexexp.com (104[.]21[.]55.70), where invoice 876597035_003.zip was downloaded on his machine. At 19:12:00.77, then Pierce (DESKTOP-H8ALZBV) opened a .js file which downloaded the warmcookie malaware from 72[.]5.43[.]29.


## IoCs
- Malicious Attachement: Invoice_876597035_003.zip
- SHA256 OF Invoice ZIP: 798563fcf7600f7ef1a35996291a9dfb5f9902733404dd499e2e736ea1dc6fc5 
- SHA256 OF .JS: dab98819d1d7677a60f5d06be210d45b74ae5fd8cf0c24ec1b3766e25ce6dc2c
- Malicious Code Recieved: 0f60a3e7baecf2748b1c8183ed37d1e4 (ddl)
- SHA256 OF DDL: b7aec5f73d2a6bbd8cd920edb4760e2edadc98c3a45bf4fa994d47ca9cbd02f6
  

