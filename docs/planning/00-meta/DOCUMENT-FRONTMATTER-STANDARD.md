---
schema_version: 1.0.0
id: workbench-doc-frontmatter-standard
title: Document Frontmatter Standard
slug: document-frontmatter-standard
project:
  name: Workbench
  short_name: workbench
  product_name: AI Software Engineering Workbench
  repository_name: workbench
document:
  type: documentation-standard
  status: draft
  version: 0.1.0
  lifecycle_stage: planning
  created: 2026-05-10
  updated: 2026-05-10
  owner: Thomas Carter
  authors:
    - Thomas Carter
  reviewers: []
  approvers: []
  audience:
    - maintainer
    - contributor
    - ai-assistant
  confidentiality: internal
  source_of_truth: true
  canonical_path: docs/planning/00-meta/DOCUMENT-FRONTMATTER-STANDARD.md
classification:
  domain: documentation
  subdomain: metadata
  tags:
    - documentation
    - frontmatter
    - metadata
    - standards
relationships:
  parent: null
  supersedes: null
  superseded_by: null
  related:
    - docs/planning/00-product/PRODUCT-INCEPTION-BRIEF.md
traceability:
  adr_refs: []
  requirement_refs: []
  epic_refs: []
  work_packet_refs: []
  issue_refs: []
change_control:
  change_policy: pull-request-reviewed
  approval_required: false
  review_cadence: as-needed
ai:
  ai_assisted: true
  ai_usage_allowed: true
  context_priority: high
  summary: Defines the canonical YAML frontmatter pattern for Workbench planning, product, architecture, ADR, requirement, and work packet documents.
verification:
  required_checks:
    - markdown-frontmatter-present
    - yaml-frontmatter-valid
    - canonical-path-matches-file-location
  last_verified: null
  verification_notes: null
---

# Document Frontmatter Standard

## 1. Purpose

This document defines the standard YAML frontmatter format for Workbench planning documents.

Workbench documents should be easy for humans, automation, and AI assistants to locate, classify, summarize, validate, and cross-reference.

The frontmatter standard exists so that documents can support:

- durable project memory;
- document lifecycle tracking;
- traceability;
- AI context assembly;
- future repository validation;
- changelog generation;
- requirement and work packet linking;
- architecture governance.

## 2. Applicability

This standard applies to Markdown documents that serve as durable project artifacts, including:

- product documents;
- planning documents;
- architecture documents;
- ADRs;
- domain model documents;
- requirements;
- epics;
- work packets;
- runbooks;
- verification records;
- AI context documents;
- repository governance documents.

Lightweight notes, temporary scratch files, generated logs, and machine-only artifacts may be exempt unless later promoted into durable documentation.

## 3. Required Frontmatter Template

Use the following template for new durable Markdown documents.

```yaml
---
schema_version: 1.0.0
id: workbench-doc-example
title: Example Document Title
slug: example-document-title
project:
  name: Workbench
  short_name: workbench
  product_name: AI Software Engineering Workbench
  repository_name: workbench
document:
  type: example-document-type
  status: draft
  version: 0.1.0
  lifecycle_stage: planning
  created: YYYY-MM-DD
  updated: YYYY-MM-DD
  owner: Thomas Carter
  authors:
    - Thomas Carter
  reviewers: []
  approvers: []
  audience:
    - maintainer
    - contributor
    - ai-assistant
  confidentiality: internal
  source_of_truth: true
  canonical_path: docs/planning/path/to/file.md
classification:
  domain: product
  subdomain: planning
  tags: []
relationships:
  parent: null
  supersedes: null
  superseded_by: null
  related: []
traceability:
  adr_refs: []
  requirement_refs: []
  epic_refs: []
  work_packet_refs: []
  issue_refs: []
change_control:
  change_policy: pull-request-reviewed
  approval_required: false
  review_cadence: as-needed
ai:
  ai_assisted: true
  ai_usage_allowed: true
  context_priority: medium
  summary: One-sentence document summary for AI context assembly.
verification:
  required_checks:
    - markdown-frontmatter-present
    - yaml-frontmatter-valid
    - canonical-path-matches-file-location
  last_verified: null
  verification_notes: null
---
```

## 4. Field Definitions

### 4.1 `schema_version`

The version of this frontmatter standard used by the document.

Initial value:

```yaml
schema_version: 1.0.0
```

### 4.2 `id`

A stable machine-readable document identifier.

Guidance:

* lowercase;
* kebab-case;
* prefixed with `workbench-doc-`, `workbench-adr-`, `workbench-req-`, or similar;
* should not change when the file is renamed unless the document identity itself changes.

Example:

```yaml
id: workbench-doc-product-charter
```

### 4.3 `title`

The human-readable title of the document.

Example:

```yaml
title: Product Charter
```

### 4.4 `slug`

A URL-safe or file-safe slug for the document.

Example:

```yaml
slug: product-charter
```

### 4.5 `project`

Identifies the owning product.

Workbench is a separate product from any prior project and should use Workbench naming consistently.

Required default:

```yaml
project:
  name: Workbench
  short_name: workbench
  product_name: AI Software Engineering Workbench
  repository_name: workbench
```

### 4.6 `document`

Describes the document’s lifecycle and ownership.

Recommended statuses:

* `draft`
* `review`
* `approved`
* `superseded`
* `deprecated`
* `archived`

Recommended lifecycle stages:

* `planning`
* `design`
* `implementation`
* `verification`
* `operations`
* `maintenance`
* `archived`

Recommended confidentiality values:

* `public`
* `internal`
* `restricted`
* `confidential`

### 4.7 `classification`

Classifies the document by domain, subdomain, and tags.

Example:

```yaml
classification:
  domain: product
  subdomain: charter
  tags:
    - product
    - charter
    - scope
```

### 4.8 `relationships`

Connects the document to other durable artifacts.

Use relative repository paths when linking documents.

Example:

```yaml
relationships:
  parent: docs/planning/00-product/PRODUCT-INCEPTION-BRIEF.md
  supersedes: null
  superseded_by: null
  related:
    - docs/planning/01-architecture/ARCHITECTURE-OVERVIEW.md
```

### 4.9 `traceability`

Connects the document to ADRs, requirements, epics, work packets, and external issues.

Example:

```yaml
traceability:
  adr_refs:
    - ADR-0001
  requirement_refs:
    - REQ-001
  epic_refs:
    - EPIC-001
  work_packet_refs:
    - WP-0001
  issue_refs: []
```

### 4.10 `change_control`

Defines how the document should be changed.

For early planning documents, `approval_required` may be false.

For approved architecture, requirements, security, or governance documents, it should usually be true.

### 4.11 `ai`

Defines how AI assistants should treat the document.

Recommended `context_priority` values:

* `critical`
* `high`
* `medium`
* `low`
* `exclude`

Use `critical` for documents that define product identity, architecture constraints, or active implementation state.

### 4.12 `verification`

Defines expected validation checks.

Initial checks may be manual.

Later, Workbench should include repository validation commands that verify frontmatter automatically.

## 5. Naming Rules

Workbench documents should avoid references to unrelated prior products.

Use:

```txt
Workbench
AI Software Engineering Workbench
.workbench/
workbench
```

Do not use prior project names as product identifiers, command names, memory directory names, or default examples.

## 6. Canonical Memory Directory

The default durable local project memory directory for this product should be:

```txt
.workbench/
```

Potential future structure:

```txt
.workbench/
  config.json
  manifest.json
  audit.ndjson
  context/
  runs/
  patches/
  verification/
  providers/
  routing/
```

## 7. Verification

After creating or editing frontmatter-bearing documents, run:

```bash
grep -Rni "foundry" docs/planning || true
```

No output should appear.

Also inspect the first section of the changed document:

```bash
sed -n '1,80p' path/to/document.md
```

## 8. Commit Recommendation

Use this atomic Conventional Commit after adding this standard:

```bash
git add docs/planning/00-meta/DOCUMENT-FRONTMATTER-STANDARD.md
git commit -m "docs(meta): add document frontmatter standard"
```

