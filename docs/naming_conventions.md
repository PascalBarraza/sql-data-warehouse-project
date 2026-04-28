# Naming Conventions

---

This document outlines the naming conventions used for schemas, tables, views, columns, and other objects in the data warehouse.

---

## Table of Contents

- General Principles  
- Table Naming Conventions  
  - Bronze Rules  
  - Silver Rules  
  - Gold Rules  
- Column Naming Conventions  
  - Surrogate Keys  
  - Technical Columns  
- Stored Procedure  

---

## General Principles

- **Naming Convention:** Use `snake_case`, with lowercase letters and underscores (`_`) to separate words.  
- **Language:** Use English for all names.  
- **Avoid Reserved Words:** Do not use SQL reserved words as object names.  

---

## Table Naming Conventions

### Bronze Rules

- All names must start with the source system name.  
- Table names must match their original names without renaming.  

**Pattern:**


- `<sourcesystem>`: Name of the source system (e.g., `crm`, `erp`)  
- `<entity>`: Exact table name from the source system  

**Example:**

→ Customer information from the CRM system  

---

### Silver Rules

- All names must start with the source system name.  
- Table names must match their original names without renaming.  

**Pattern:**

- `<sourcesystem>`: Name of the source system (e.g., `crm`, `erp`)  
- `<entity>`: Exact table name from the source system  

**Example:**

→ Customer information from the CRM system  

---

### Gold Rules

- Use meaningful, business-aligned names.  
- Tables must start with a category prefix.  

**Pattern:**

- `<category>`: Role of the table (`dim`, `fact`)  
- `<entity>`: Business-aligned name (e.g., `customers`, `products`, `sales`)  

**Examples:**

---

## Glossary of Category Patterns

| Pattern  | Meaning          | Example(s)                          |
|----------|------------------|-------------------------------------|
| dim_     | Dimension table  | dim_customer, dim_product           |
| fact_    | Fact table       | fact_sales                          |
| report_  | Report table     | report_customers, report_sales_monthly |

---

## Column Naming Conventions

### Surrogate Keys

- All primary keys in dimension tables must use the suffix `_key`.  

**Pattern:**

- `<table_name>`: Refers to the entity name  
- `_key`: Indicates a surrogate key  

**Example:**

→ Surrogate key in the `dim_customers` table  

---

### Technical Columns

- All technical columns must start with the prefix `dwh_`.  

**Pattern:**

- `dwh`: Prefix for system-generated metadata  
- `<column_name>`: Descriptive purpose  

**Example:**

→ Stores the date when the record was loaded  

---

## Stored Procedure

- All stored procedures used for loading data must follow this pattern:

- `<layer>`: Represents the layer (`bronze`, `silver`, `gold`)  

**Examples:**
- Load_bronze -> Stored procedure for loading data into the Bronze layer
- Load_silver -> Stored procedure for loading data into the Silver layer
