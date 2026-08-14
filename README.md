# DVWA Network Security Assessment

A structured, end-to-end security assessment of a local test network (DVWA on a Dockerized Kali Linux lab), covering network reconnaissance, live traffic analysis, and web application vulnerability scanning.

## Overview

This project simulates a real-world security assessment engagement: scoping, testing, documenting findings, and delivering a professional report suitable for both technical and non-technical audiences. The target environment is [DVWA (Damn Vulnerable Web Application)](https://github.com/digininja/DVWA), deliberately vulnerable software used for security training, run in Docker on a Kali Linux VM.

## What's in this repo

| File | Description |
|---|---|
| [`network_security_assessment.md`](./network_security_assessment.md) | Full report — scope, methodology, findings register, executive summary, and remediation roadmap |
| `nmap_results.txt` | Raw Nmap scan output (Phase 1 — Reconnaissance) |
| `wireshark_capture.pcapng` | Raw packet capture (Phase 2 — Traffic Analysis) |
| `nikto_results.txt` | Raw Nikto scan output (Phase 3 — Web Vulnerability Scan) |
| `screenshots/` | Evidence screenshots referenced throughout the report |

## Methodology

1. **Reconnaissance** — `nmap -sV -O` against the target subnet to enumerate live hosts, open ports, and service versions
2. **Traffic Analysis** — 5+ minute Wireshark packet capture, filtered and analyzed for HTTP, DNS, and ARP activity
3. **Web Vulnerability Scan** — Nikto scan against the identified web server to surface misconfigurations and known issues

## Key findings

| Severity | Count |
|---|---|
| Critical | 1 |
| High | 2 |
| Medium | 3 |
| Low | 2 |

The headline finding: DVWA's login form transmits credentials in **plaintext over HTTP**, confirmed by capturing and inspecting the raw form data in Wireshark. Full details, evidence, and a prioritized remediation roadmap are in the [assessment report](./network_security_assessment.md).

## Tools used

- **Nmap** — host/service discovery
- **Wireshark** — packet capture and protocol analysis
- **Nikto** — automated web vulnerability scanning
- **Docker** — hosting the DVWA target
- **Markdown** — report authoring

## Scope & authorization

All testing was performed against a Docker-based DVWA instance running in a self-owned, isolated Kali Linux lab environment for educational and portfolio purposes only. No third-party or production systems were involved. See Section 1 of the report for full scope details.

---

*Part of my cybersecurity portfolio — [CeaVault](https://github.com/CeaVault)*
