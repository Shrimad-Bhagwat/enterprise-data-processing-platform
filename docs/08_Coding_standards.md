# Coding Standards

## Purpose

This document defines the coding standards followed throughout the Enterprise Data Processing Platform (EDPP).

---

# General Principles

* Write readable code over clever code.
* Follow Clean Code principles.
* Follow SOLID principles.
* Prefer composition over inheritance.
* Avoid code duplication (DRY).
* Keep methods small and focused.
* Use meaningful names.

---

# Package Structure

Packages shall be organized by feature.

Example:

```
upload
metadata
parser
validation
transformation
persistence
reporting
audit
common
```

---

# Naming Conventions

## Classes

* PascalCase
* Nouns

Examples

```
UploadService
JobController
ValidationRule
```

---

## Interfaces

No "I" prefix.

Examples

```
MetadataProvider
Parser
Validator
```

---

## Methods

camelCase

Method names should describe actions.

Examples

```
uploadFile()

validateRecord()

createJob()

generateReport()
```

---

## Variables

camelCase

Avoid abbreviations.

Bad

```
str
tmp
obj
```

Good

```
fileName
recordCount
processingStatus
```

---

# API Standards

* RESTful APIs
* JSON only
* Standard response wrapper
* Meaningful HTTP status codes

---

# Exception Handling

* Never swallow exceptions.
* Throw domain-specific exceptions.
* Use global exception handling.
* Log before propagating.

---

# Logging

Use structured logging.

Log:

* Startup
* Shutdown
* Upload
* Processing
* Errors

Do not log:

* Passwords
* Sensitive data

---

# Database

* Use transactions appropriately.
* Avoid unnecessary queries.
* Prefer batch operations.
* Index searchable columns.

---

# Testing

Every feature should include:

* Unit tests
* Integration tests (where applicable)

---

# Git

* Small commits
* Meaningful commit messages
* One logical change per commit

Example

```
feat(upload): implement file upload endpoint

fix(validation): handle null metadata

refactor(parser): simplify parsing workflow
```

---

# Code Review Checklist

* Readability
* Naming
* SOLID
* Exception handling
* Logging
* Performance
* Tests
* Documentation

---

# Definition of Good Code

Good code is:

* Simple
* Readable
* Testable
* Maintainable
* Extensible
* Consistent
