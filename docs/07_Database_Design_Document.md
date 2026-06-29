# Database Design Document (DDD)

## Project

**Enterprise Data Processing Platform (EDPP)**

**Version:** 1.0

---

# 1. Purpose

This document defines the logical database design for the Enterprise Data Processing Platform (EDPP).

The platform uses Oracle Database and follows a metadata-driven approach where platform tables are fixed while business tables are generated dynamically from metadata.

---

# 2. Database Objectives

The database shall:

* Store platform information.
* Store processing jobs.
* Store uploaded file information.
* Store audit information.
* Store validation errors.
* Store metadata definitions.
* Generate business tables dynamically.

---

# 3. Database Categories

The database consists of two categories.

## Platform Tables

Managed by EDPP.

Examples

* JOB
* JOB_FILE
* ERROR_RECORD
* AUDIT_LOG
* METADATA_CONFIG

These tables are permanent.

---

## Dynamic Business Tables

Generated automatically from YAML metadata.

Examples

* CUSTOMER
* TRADE
* EMPLOYEE
* PRODUCT

These tables are created at runtime.

---

# 4. Platform Tables

## JOB

Purpose

Represents one processing request.

Attributes

* Job ID
* Job Name
* Status
* Start Time
* End Time
* Total Records
* Success Count
* Failure Count
* Processing Duration

---

## JOB_FILE

Purpose

Stores uploaded file information.

Attributes

* File ID
* Job ID
* File Name
* File Path
* File Size
* File Type
* Checksum

---

## METADATA_CONFIG

Purpose

Stores metadata configuration history.

Attributes

* Metadata ID
* Version
* Entity Name
* YAML Location
* Status
* Created Date

---

## ERROR_RECORD

Purpose

Stores invalid records.

Attributes

* Error ID
* Job ID
* Record Number
* Error Code
* Error Message
* Original Data

---

## AUDIT_LOG

Purpose

Stores application audit events.

Attributes

* Audit ID
* Event Type
* Module
* Description
* User
* Timestamp

---

# 5. Dynamic Business Tables

Business tables are generated from metadata.

Example

Metadata

```yaml
entity:
  name: CUSTOMER

columns:
  - CUSTOMER_ID
  - NAME
  - CITY
```

Generated Table

```text
CUSTOMER

CUSTOMER_ID

NAME

CITY
```

The application shall generate Oracle DDL automatically.

---

# 6. Metadata Driven Schema

Metadata defines

* Table Name
* Column Name
* Data Type
* Length
* Precision
* Scale
* Nullable
* Default Value
* Primary Key
* Unique Constraint
* Index
* Comments

---

# 7. Oracle Data Type Mapping

| Metadata Type | Oracle Type |
| ------------- | ----------- |
| STRING        | VARCHAR2    |
| NUMBER        | NUMBER      |
| INTEGER       | NUMBER      |
| LONG          | NUMBER      |
| DECIMAL       | NUMBER      |
| DATE          | DATE        |
| TIMESTAMP     | TIMESTAMP   |
| BOOLEAN       | CHAR(1)     |
| CLOB          | CLOB        |

---

# 8. Naming Standards

Tables

UPPER_CASE

Example

CUSTOMER

Columns

UPPER_CASE

Example

CUSTOMER_NAME

Primary Keys

TABLE_NAME_ID

Example

CUSTOMER_ID

Indexes

IDX_<TABLE>_<COLUMN>

Example

IDX_CUSTOMER_NAME

Foreign Keys

FK_<TABLE>_<REFERENCE>

---

# 9. Relationships

Platform Tables

```text
JOB
 │
 ├──── JOB_FILE
 │
 ├──── ERROR_RECORD
 │
 └──── AUDIT_LOG
```

Business tables remain independent.

---

# 10. Dynamic Table Generation Rules

The Metadata Deployment Engine shall

* Read YAML
* Validate metadata
* Generate DDL
* Create table
* Create primary keys
* Create indexes
* Create unique constraints

Version 1 will not modify existing tables.

---

# 11. Transaction Strategy

Processing shall use transactions.

Each batch shall commit independently.

Future versions may support configurable batch sizes.

---

# 12. Index Strategy

Indexes shall exist on

* Primary Keys
* Foreign Keys
* Frequently searched columns
* Job ID

Future optimization

* Composite Indexes
* Function Based Indexes
* Partitioning

---

# 13. Scalability

The schema shall support

* Millions of records
* Batch processing
* Parallel processing
* Future partitioning

---

# 14. Constraints

Business tables shall never contain platform information.

Platform tables shall never contain business data.

Metadata shall remain the single source of truth.

---

# 15. Future Enhancements

Future versions may support

* ALTER TABLE generation
* Schema migration
* Metadata versioning
* Rollback
* Automatic index recommendations
* Partition management

---

# 16. Success Criteria

The database design is considered complete when

* Platform schema is stable.
* Business schema is metadata driven.
* Oracle naming conventions are followed.
* Dynamic DDL generation is supported.
* New business entities can be created without modifying Java code.
