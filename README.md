# Greenbone OpenVAS Vulnerability Management Lab

## Overview

This project documents a Greenbone/OpenVAS vulnerability management lab deployed using Docker and the Greenbone Community Edition stack.

The lab is designed to demonstrate vulnerability assessment, scanning, report generation, vulnerability analysis, and remediation workflows from a security operations perspective.

## Architecture

```text
                    ┌──────────────────────────┐
                    │      Target Systems       │
                    │  Linux / Windows / VMs    │
                    └────────────┬─────────────┘
                                 │
                                 ▼
                    ┌──────────────────────────┐
                    │    Greenbone / OpenVAS   │
                    │      Vulnerability       │
                    │         Scanner          │
                    └────────────┬─────────────┘
                                 │
                                 ▼
                    ┌──────────────────────────┐
                    │     Vulnerability        │
                    │      Assessment          │
                    └────────────┬─────────────┘
                                 │
                   ┌─────────────┴─────────────┐
                   │                           │
                   ▼                           ▼
          ┌─────────────────┐         ┌─────────────────┐
          │ Scan Results    │         │ Vulnerability   │
          │ & Reports       │         │ Analysis        │
          └────────┬────────┘         └────────┬────────┘
                   │                           │
                   └─────────────┬─────────────┘
                                 ▼
                    ┌──────────────────────────┐
                    │ Remediation & Security   │
                    │ Recommendations          │
                    └──────────────────────────┘
```

## Technology Stack

* Greenbone Community Edition
* OpenVAS Scanner
* Greenbone Vulnerability Manager (`gvmd`)
* Greenbone Security Assistant (`gsad`)
* PostgreSQL
* Redis
* Nginx
* Docker
* Docker Compose

## Main Components

| Component           | Purpose                                         |
| ------------------- | ----------------------------------------------- |
| OpenVAS Scanner     | Performs vulnerability scanning                 |
| `gvmd`              | Vulnerability management and scan orchestration |
| `gsad`              | Web/API interface                               |
| PostgreSQL          | Stores vulnerability management data            |
| Redis               | Scanner-related runtime communication           |
| Nginx               | Frontend/reverse proxy                          |
| Vulnerability Tests | Vulnerability test feed                         |
| SCAP Data           | Security Content Automation Protocol data       |
| CERT Data           | CERT and advisory information                   |
| Notus Data          | Local vulnerability detection data              |

## Deployment

The deployment is based on the Greenbone Community Edition Docker Compose stack.

The reproducible deployment configuration is available under:

```text
config/docker-compose.yml
```

## Scanning Workflow

```text
Target Discovery
      ↓
Target Configuration
      ↓
Scan Configuration
      ↓
Vulnerability Scan
      ↓
Result Collection
      ↓
Severity Analysis
      ↓
Report Generation
      ↓
Remediation
```

## Example Use Cases

* Vulnerability assessment of Linux systems
* Vulnerability assessment of Windows systems
* Identification of critical and high-risk vulnerabilities
* Security baseline validation
* Remediation verification
* SOC vulnerability-management workflows

## Security Considerations

This repository intentionally excludes:

* Database contents
* Vulnerability feed databases
* Runtime logs
* Private keys
* Credentials
* API tokens
* TLS secrets
* Persistent Docker volumes

Configuration should be reviewed and sanitized before deploying in another environment.

## Project Structure

```text
greenbone-openvas-lab/
├── README.md
├── .gitignore
├── config/
│   └── docker-compose.yml
└── docs/
    └── screenshots/
```

## Future Improvements

* Add deployment documentation
* Add target configuration examples
* Add authenticated-scan documentation
* Add sample vulnerability reports
* Add vulnerability remediation workflow
* Integrate scan findings with Wazuh/SOAR
* Add automated deployment validation

## Author

Kiran Pamidipalli

Cybersecurity | SOC | Vulnerability Management | Network Security
