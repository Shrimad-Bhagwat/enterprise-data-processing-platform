# Software Requirements Specification (SRS)

## Project

**Enterprise Data Processing Platform (EDPP)**

**Version:** 1.0

---

# 1. Purpose

The Enterprise Data Processing Platform (EDPP) is a configurable backend application designed to ingest structured data, validate it using external metadata, process it through configurable rules, persist the results, and expose reporting APIs.

The project is intended to simulate how enterprise backend systems are designed while remaining independent of any business domain.

---

# 2. Project Objectives

## Primary Objective

Learn enterprise backend development by building a production-quality application from scratch.

## Secondary Objectives

* Build using enterprise software engineering practices.
* Learn Spring Boot through implementation rather than tutorials.
* Design a highly configurable platform.
* Minimize hardcoded business logic.
* Produce a resume-quality project.
* Evolve the application into a microservices architecture.

---

# 3. Scope

## Included

* File Upload
* Metadata Driven Processing
* YAML Configuration
* Generic Validation Engine
* Generic Processing Engine
* Oracle Database Persistence
* Reporting APIs
* Audit Logging
* Job Management
* Search APIs

## Future Scope

* Authentication
* Async Processing
* Scheduling
* Docker
* Microservices
* Cloud Deployment

---

# 4. System Principles

The platform shall follow these principles:

* Domain Independent
* Configuration over Hardcoding
* Metadata Driven
* Extensible
* Layered Architecture
* Modular Monolith
* Enterprise Coding Standards

---

# 5. Actors

### User

Can

* Upload files
* Check processing status
* View reports
* Search processed data
* Download errors

---

### Processing Engine

Responsible for

* Reading metadata
* Parsing files
* Validation
* Processing
* Persistence

---

### Oracle Database

Stores

* Processing Jobs
* Metadata
* Processed Records
* Error Records
* Audit Logs
* Configuration

---

# 6. Functional Requirements

## FR-1 Upload Management

The platform shall:

* Accept file uploads
* Validate supported file type
* Create processing job
* Store upload metadata

---

## FR-2 Metadata Management

The platform shall read configuration from YAML.

Configuration includes:

* File Type
* Delimiter
* Column Definitions
* Data Types
* Validation Rules
* Processing Options

No Java code should require modification when metadata changes.

---

## FR-3 Dynamic Schema Definition

Columns shall be configurable.

Example attributes:

* Name
* Position
* Data Type
* Mandatory
* Length
* Date Format
* Default Value

---

## FR-4 Validation Engine

Validation rules shall be configurable through YAML.

Examples:

* Mandatory
* Positive Number
* Date Format
* Regex
* Length
* Allowed Values

The validation engine shall execute rules dynamically.

---

## FR-5 Processing Engine

The processing engine shall

* Parse records
* Validate records
* Transform records
* Persist valid records
* Persist invalid records

The processing logic shall remain generic.

---

## FR-6 Job Management

Each processing job shall maintain:

* Job Id
* Status
* Start Time
* End Time
* Uploaded File
* Total Records
* Success Count
* Failure Count
* Processing Duration

---

## FR-7 Reporting

Provide APIs for

* Job Summary
* Processing Summary
* Validation Summary
* Error Summary
* Search Records

Support

* Pagination
* Filtering
* Sorting

---

## FR-8 Audit Logging

Maintain audit information for

* Upload
* Processing
* Errors
* Configuration Changes

---

# 7. Configuration Requirements

Configuration shall reside outside the application.

Initial format:

* YAML

Configuration shall define:

* File Structure
* Column Metadata
* Validation Rules
* Processing Rules

Future versions may support:

* Database Driven Configuration
* UI Configuration

---

# 8. Data Volume Requirements

The platform shall support varying workloads.

Target ranges

* Small : 10K records
* Medium : 100K records
* Large : 1M+ records
* Very Large : Up to 10M records

The architecture shall support future optimization for skewed workloads.

---

# 9. Non Functional Requirements

## Performance

Designed for high-volume processing.

---

## Scalability

Architecture should support migration to microservices.

---

## Maintainability

Configuration should replace code changes wherever possible.

---

## Extensibility

Adding a new file format or validation rule should require minimal code changes.

---

## Reliability

Processing failures should not corrupt data.

---

## Testability

Every module should be independently testable.

---

# 10. Technology Stack

Backend

* Java
* Spring Boot

Database

* Oracle Database

Persistence

* Spring Data JPA

Build

* Maven

Version Control

* Git

Configuration

* YAML

---

# 11. Architecture Goals

Version 1

Modular Monolith

Future

Microservices

No business logic should depend on a specific domain.

---

# 12. Out of Scope (Version 1)

* Kafka
* Kubernetes
* Distributed Transactions
* Event Streaming
* Multi-Tenant Architecture
* Cloud Deployment

---

# 13. Success Criteria

The project is successful when it demonstrates:

* Clean Architecture
* Generic Processing Pipeline
* YAML Driven Configuration
* Dynamic Validation
* Oracle Integration
* Enterprise Coding Practices
* RESTful APIs
* Extensible Design
* Clear Migration Path to Microservices

---

# 14. Future Evolution

v1.0

* Modular Monolith

v2.0

* Enterprise Features

    * Security
    * Async Processing
    * Scheduler
    * Docker

v3.0

* Microservices

    * API Gateway
    * Service Discovery
    * Inter-service Communication
    * Configuration Server

v4.0

* Cloud Native Deployment
