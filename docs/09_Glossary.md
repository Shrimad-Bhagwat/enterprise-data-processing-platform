# Glossary

## Project

**Enterprise Data Processing Platform (EDPP)**

**Version:** 1.0

---

# Purpose

This glossary defines the terminology used throughout the Enterprise Data Processing Platform.

These definitions should be used consistently across documentation, code, APIs, and discussions.

---

# Terms

## Audit

A record of significant system events generated for traceability and troubleshooting.

---

## Audit Event

An individual entry recorded in the audit log.

Examples:

* File uploaded
* Processing started
* Processing completed
* Validation failed
* Configuration reloaded

---

## Batch

A collection of records processed together as a single unit.

---

## Business Data

The actual data being processed by the platform.

Examples:

* Customers
* Products
* Employees
* Trades
* Orders

The platform remains independent of the business domain.

---

## Configuration

External settings that define system behavior without changing application code.

Initially stored in YAML.

---

## Dynamic Table

A database table generated automatically from metadata.

Example:

```text
CUSTOMER
PRODUCT
EMPLOYEE
```

---

## Entity

A metadata definition representing a business object.

An entity eventually becomes a database table.

---

## Error Record

A record that failed validation or processing.

Error records are stored separately from successfully processed records.

---

## File Definition

Metadata describing an input file.

Includes:

* File type
* Delimiter
* Header information
* Encoding

---

## Job

A single processing request initiated by uploading one file.

A job owns all records processed from that upload.

---

## Job Status

Represents the current state of a processing job.

Possible values include:

* RECEIVED
* VALIDATING
* PROCESSING
* COMPLETED
* FAILED

---

## Metadata

Configuration describing how data should be interpreted and processed.

Metadata includes:

* Entity definition
* Column definitions
* Validation rules
* Processing rules

---

## Metadata Registry

The logical repository that provides metadata to the application.

Initially implemented using YAML files.

Future versions may support database-backed metadata.

---

## Module

An independent functional component of the platform.

Examples:

* Upload
* Parser
* Validation
* Reporting

---

## Parser

The component responsible for converting raw file content into generic records.

The parser does not perform validation.

---

## Persistence

The process of storing application data in the Oracle database.

---

## Pipeline

The ordered sequence of processing modules.

Example:

Upload → Parser → Validation → Transformation → Persistence → Reporting

---

## Platform Data

Data owned by EDPP itself.

Examples:

* Jobs
* Audit Logs
* Metadata
* Error Records

---

## Platform Table

A permanent database table used internally by EDPP.

Examples:

* JOB
* JOB_FILE
* AUDIT_LOG
* METADATA_CONFIG

---

## Processing

The complete workflow from receiving a file to storing processed data.

---

## Processing Engine

Coordinates the execution of the processing pipeline.

---

## Record

A single logical row extracted from an input file.

One file contains multiple records.

---

## Reporting

The process of exposing processed information through REST APIs.

Reporting never modifies business data.

---

## Transformation

The process of converting validated records into the internal data model before persistence.

Transformation does not perform validation.

---

## Validation

The process of verifying that records satisfy configured rules.

Validation is metadata-driven.

---

## Validation Rule

A configurable rule used during validation.

Examples:

* Mandatory
* Positive Number
* Date Format
* Maximum Length
* Allowed Values

---

## YAML

The external configuration format used to define metadata and processing behavior.

YAML is the initial configuration source for EDPP.

---

# Naming Convention

The terminology defined in this document shall be used consistently throughout:

* Documentation
* Source Code
* Database Objects
* REST APIs
* GitHub Issues
* Commit Messages

No alternative terminology should be introduced without updating this glossary.
