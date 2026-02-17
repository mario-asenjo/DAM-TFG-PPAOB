# PPAOB – Pre-Exploitation Platform for Offensive Binary Analysis

## Overview

PPAOB is a security-oriented platform designed to support the pre-exploitation phase of offensive security audits.  
Its purpose is to centralize and structure the initial analysis of executable binaries, focusing on understanding attack surface, security mitigations, and runtime behavior before any exploitation attempts.

The project targets ELF binaries on Linux systems and follows an ethical approach, explicitly excluding automatic exploitation features.

---

## Key Features

- User authentication and role-based access control
- Binary upload with hash-based deduplication
- Static analysis of ELF binaries
- Controlled dynamic analysis
- Persistent storage of analysis results
- Risk scoring and prioritization
- HTML report generation
- Full audit and traceability of user actions

---

## Architecture Summary

The system is composed of:

- Web Frontend
- Backend API
- Isolated Analysis Workers
- PostgreSQL relational database
- S3-compatible object storage
- Append-only audit subsystem

All components are designed to be modular and independently evolvable.

For more details, see `ARCHITECTURE.md`.

---

## Technology Stack

- Backend: Java with Spring Boot
- Frontend: Web-based UI
- Database: PostgreSQL
- Object Storage: MinIO (S3 compatible)
- Containerization: Docker and Docker Compose

---

## Repository Structure
```bash
.
├── backend
├── frontend
├── infra
│ ├── compose
│ └── db
│ └── migrations
├── docs
└── README.md
```

---

## Development Status

This project is currently under active development.  
The initial phase focuses on architecture, data modeling, and documentation before implementation.

---

## Ethical Considerations

The platform is intended for controlled environments such as laboratories, training scenarios, and authorized security assessments.  
It does not include automated exploitation capabilities and emphasizes traceability and accountability.

---

## License

This project is licensed under the MIT License.

