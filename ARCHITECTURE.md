# System Architecture

## Overview

This project implements a pre-exploitation and offensive binary analysis platform focused on the early stages of a security audit.  
The system is designed as a modular and extensible product, oriented to controlled environments and ethical security assessment.

The architecture follows a layered and decoupled approach, allowing independent evolution of each component while keeping a clear separation of responsibilities.

---

## High Level Architecture

The platform is composed of the following main components:

- Web Frontend
- Backend API
- Analysis Workers
- Persistent Storage
- Object Storage
- Audit and Logging subsystem

Each component can be deployed independently and communicates through well-defined interfaces.

---

## Components Description

### Web Frontend

The frontend provides a web-based user interface to interact with the platform.  
Its responsibilities include:

- User authentication and session management
- Binary upload and management
- Analysis execution control
- Visualization of analysis results
- Report download

The frontend communicates exclusively with the Backend API over HTTPS.

---

### Backend API

The Backend API acts as the central orchestrator of the system.

Main responsibilities:

- Authentication and authorization
- Access control enforcement
- Binary metadata management
- Analysis lifecycle management
- Results aggregation and exposure
- Audit event generation

The API exposes REST endpoints and persists all system state in the relational database.

---

### Analysis Workers

Workers are isolated components responsible for executing the actual analysis logic.

Responsibilities:

- Static analysis of binaries
- Controlled dynamic execution and tracing
- Evidence extraction and scoring
- Artifact generation

Workers do not expose public endpoints and interact with the Backend API and storage services only.

This design allows horizontal scaling and strict isolation of risky execution environments.

---

### Persistent Storage (PostgreSQL)

PostgreSQL is used as the primary system database.

Stored data includes:

- Users and roles
- Binary metadata
- Analysis lifecycle information
- Analysis results stored as JSONB
- Audit events

The use of JSONB allows flexible evolution of analysis results without requiring frequent schema migrations.

---

### Object Storage (MinIO / S3 compatible)

Binary files and generated artifacts are stored outside the database in object storage.

Stored objects include:

- Uploaded binaries
- Generated reports
- Large analysis outputs

The database only stores references to these objects, keeping the relational model clean and efficient.

---

### Audit and Traceability

The platform includes an append-only audit subsystem.

All relevant actions are recorded, including:

- Authentication events
- Binary uploads
- Analysis execution
- Report downloads

This ensures traceability and accountability, which are critical in professional security assessment environments.

---

## Architectural Principles

The system design follows these principles:

- Separation of concerns
- Least privilege
- Defense in depth
- Explicit trust boundaries
- Observability and traceability
- Evolution-oriented design

---

## Deployment Model

The platform is designed to be deployed using container-based environments.

A typical deployment includes:

- One Backend API service
- One or more Analysis Worker services
- PostgreSQL database
- Object storage service

This model supports both single-node deployments and future scalable environments.

---

## Security Considerations

- No automatic exploitation features are included
- Dynamic analysis is executed in controlled environments
- Access to sensitive data is strictly role-based
- All actions are auditable
- Secrets are externalized via environment variables

---

## Future Evolution

The architecture allows future extensions such as:

- Advanced sandboxing mechanisms
- External identity providers integration
- Additional analysis engines
- Distributed deployments

These evolutions can be introduced without major architectural changes.
