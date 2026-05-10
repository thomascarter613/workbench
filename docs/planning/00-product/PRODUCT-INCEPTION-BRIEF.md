---
title: Product Inception Brief
project: AI Software workbench Workbench
document_type: product-inception-brief
status: draft
version: 0.1.0
created: 2026-05-10
updated: 2026-05-10
owner: Thomas Carter
---

# Product Inception Brief

## 1. Product Name

The working product name is:

**AI Software workbench Workbench**

This name is provisional. The product may later be renamed before public release.

## 2. One-Sentence Description

AI Software workbench Workbench is a local-first, provider-agnostic software engineering application that helps developers design, generate, verify, and evolve software projects using AI while controlling cost, preserving user ownership, and supporting local, remote self-hosted, and third-party model execution.

## 3. Product Thesis

Developers increasingly want AI-assisted software engineering, but the current options create a difficult trade-off:

1. Hosted frontier AI tools can be powerful but expensive.
2. Local models can reduce subscription dependency but often require hardware that many developers do not have.
3. Existing AI coding tools often optimize for convenience rather than durable architecture, project memory, verification, user supervision, and cost governance.

This product exists to solve that problem.

The central thesis is:

> AI-assisted software engineering should be controllable, affordable, provider-agnostic, architecture-aware, and usable even when the developer does not own high-end local AI hardware.

The product should not merely wrap an LLM. It should function as a software engineering control plane that coordinates project planning, context assembly, model routing, supervised file changes, verification, and project memory.

## 4. Core Problem

The primary user problem is two-fold:

1. The cost of relying on hosted AI/GPT/LLM subscriptions and usage-based APIs can become significant over time.
2. The user may not have enough local workstation resources to run high-quality LLMs with acceptable speed and capability.

This creates a gap between what developers want and what their hardware or budget can support.

The product should bridge that gap by combining:

- local-first workflows;
- optional local inference;
- optional LAN or remote self-hosted inference;
- optional hosted provider inference;
- model routing based on task complexity;
- aggressive context reduction;
- caching;
- reusable project memory;
- deterministic verification;
- supervised repository modification.

## 5. Target Users

### 5.1 Primary User

The primary user is an independent software developer, technical founder, consultant, or advanced builder who wants to use AI to design and build software products without becoming fully dependent on expensive hosted AI subscriptions.

This user may be technically capable but cost-sensitive.

They may have a normal laptop or workstation, but not a high-end GPU server.

They want strong engineering discipline, not just conversational code generation.

### 5.2 Secondary Users

Secondary users include:

- small development teams;
- AI-assisted software consultants;
- open-source maintainers;
- solo SaaS founders;
- technical product builders;
- developers experimenting with local models;
- organizations that want AI assistance but need more control over data, cost, and provider choice.

### 5.3 Future Users

Future users may include:

- teams using shared self-hosted inference infrastructure;
- agencies building repeatable client project templates;
- enterprises requiring provider abstraction, auditability, and policy controls;
- developers using cloud-hosted GPU workers on demand.

## 6. Product Goals

The product must help users:

1. design new software projects from first principles;
2. create and maintain product documents, architecture documents, ADRs, requirements, epics, work packets, and implementation plans;
3. generate new repositories and project structures;
4. index existing repositories;
5. assemble relevant AI context without sending the entire repository to a model;
6. use local AI models when sufficient;
7. use remote self-hosted models when local hardware is insufficient;
8. use hosted AI providers only when appropriate or explicitly configured;
9. route AI tasks based on cost, quality, latency, privacy, and required reasoning depth;
10. propose file changes before applying them;
11. require user review and approval before destructive or meaningful repository changes;
12. run verification commands after changes;
13. produce clean atomic Conventional Commit recommendations;
14. maintain durable project memory inside the repository.

## 7. Product Non-Goals

The initial product is not intended to be:

1. a general-purpose chatbot;
2. a simple wrapper around one AI provider;
3. an IDE replacement on day one;
4. a fully autonomous coding agent that mutates repositories without supervision;
5. a cloud-only SaaS product;
6. a system that requires paid AI subscriptions to function;
7. a system that requires high-end local GPU hardware to be useful;
8. a replacement for Git, CI, package managers, or established build tools;
9. a black-box code generator without audit trails;
10. a tool that hides architectural decisions from the user.

## 8. Key Product Principles

### 8.1 Local-First

The product should run locally by default.

The user’s repository, project memory, generated documents, work packets, audits, and verification history should be stored locally unless the user explicitly configures remote services.

### 8.2 Provider-Agnostic

The product must not be coupled to a single LLM provider.

It should support multiple model execution backends through a common model gateway abstraction.

Potential backends include:

- local models;
- Ollama;
- llama.cpp;
- OpenAI-compatible APIs;
- vLLM;
- LiteLLM;
- self-hosted inference servers;
- hosted commercial providers;
- future MCP-compatible model/tool providers.

### 8.3 Cost-Aware by Design

The product must treat cost as a first-class architectural concern.

It should avoid unnecessary expensive model calls by using:

- local deterministic logic;
- context indexing;
- retrieval;
- summarization;
- caching;
- prompt reuse;
- small/local models;
- model routing;
- user-configured budget limits.

### 8.4 Supervised Repository Execution

The product should not blindly write to the user’s repository.

The expected workflow is:

1. inspect;
2. plan;
3. propose;
4. generate patch;
5. show diff;
6. request approval;
7. apply;
8. verify;
9. summarize;
10. recommend commit.

### 8.5 Repository as Durable Project Memory

The repository should contain durable project state.

The product should write and maintain project artifacts such as:

- product documents;
- architecture documents;
- ADRs;
- work packets;
- generated context summaries;
- audit logs;
- verification records;
- provider configuration;
- project manifest files.

The repository should remain useful even if the AI provider changes.

### 8.6 Verification Before Trust

The product should never treat generated code as correct merely because an AI produced it.

Every meaningful implementation step should be paired with verification, such as:

- formatting;
- linting;
- typechecking;
- tests;
- build checks;
- contract checks;
- generated file validation;
- repository structure validation.

### 8.7 Architecture Before Automation

Automation should reinforce architecture, not bypass it.

The product should guide users through disciplined software delivery:

1. vision;
2. product charter;
3. requirements;
4. architecture;
5. ADRs;
6. domain model;
7. epics;
8. work packets;
9. implementation;
10. verification;
11. commit.

## 9. Core Use Cases

### 9.1 Start a New Project

A user wants to create a new software product.

The product helps generate:

- product inception brief;
- product charter;
- SRS;
- architecture overview;
- ADR index;
- ADRs;
- domain model;
- epics;
- work packets;
- initial repository structure;
- verification scripts;
- CI baseline.

### 9.2 Continue an Existing Project

A user points the application at an existing repository.

The product:

- scans the repository;
- identifies structure;
- detects package managers and languages;
- builds a project graph;
- finds docs and architectural artifacts;
- identifies missing governance files;
- creates a context pack;
- recommends next steps.

### 9.3 Ask Questions About a Repository

A user asks questions such as:

- “Where is authentication handled?”
- “What would break if I change this module?”
- “What should the next work packet be?”
- “Which files are relevant to this bug?”
- “What architecture decision governs this?”

The product answers using indexed repository context rather than blindly sending the entire repository to an LLM.

### 9.4 Generate a Work Packet

A user wants to implement a specific feature.

The product generates a work packet containing:

- goal;
- scope;
- affected files;
- implementation steps;
- verification commands;
- rollback guidance;
- expected commit message.

### 9.5 Apply a Safe Code Change

A user asks the product to implement a change.

The product:

- inspects the repo;
- builds a task-specific context pack;
- chooses an appropriate model;
- generates a proposed patch;
- shows the diff;
- waits for approval;
- applies the change;
- runs verification;
- summarizes the result;
- recommends an atomic commit.

### 9.6 Use Local AI First

A user wants to avoid paid inference.

The product first attempts to use:

- deterministic logic;
- templates;
- local context;
- local small models.

Only when the task exceeds local capability should the product recommend a stronger model or remote backend.

### 9.7 Use Remote Self-Hosted AI

A user has insufficient laptop resources but wants to avoid recurring AI subscriptions.

The product allows the user to connect to a remote self-hosted inference server, such as a rented GPU instance or LAN workstation.

The product treats this backend as a configurable provider.

## 10. MVP Definition

The MVP should prove the product thesis with a local CLI.

### 10.1 MVP Must Include

The MVP must include:

1. a CLI entrypoint;
2. project initialization;
3. repository inspection;
4. basic project manifest generation;
5. documentation scaffold generation;
6. model provider configuration;
7. OpenAI-compatible provider support;
8. Ollama-compatible provider support;
9. context pack generation;
10. cost-aware model routing policy;
11. supervised patch generation;
12. verification command execution;
13. audit log generation;
14. Conventional Commit recommendation.

### 10.2 MVP Should Include

The MVP should include:

1. ADR generation;
2. work packet generation;
3. repo health checks;
4. TypeScript monorepo support;
5. polyglot project awareness;
6. provider capability detection;
7. prompt and response caching;
8. dry-run mode;
9. JSON output mode;
10. CI-friendly verification commands.

### 10.3 MVP Could Include

The MVP could include:

1. web UI;
2. desktop app wrapper;
3. vector database integration;
4. remote GPU lifecycle management;
5. multi-user/team mode;
6. billing or credit tracking;
7. marketplace templates;
8. plugin SDK;
9. project graph visualization;
10. IDE extension integration.

## 11. Initial System Shape

The initial system should be structured around the following conceptual components:

### 11.1 Workbench CLI

The command-line interface used to operate the system.

Example future commands:

```bash
workbench init
workbench inspect
workbench index
workbench ask
workbench plan
workbench generate
workbench patch
workbench apply
workbench verify
```

The final command names may change.

### 11.2 Project Intelligence Engine

Responsible for understanding the repository.

It should inspect:

* files;
* directories;
* package manifests;
* language ecosystems;
* docs;
* ADRs;
* dependency files;
* Git state;
* verification scripts.

### 11.3 Context Pack Assembler

Responsible for creating compact, task-specific context bundles for AI models.

It should avoid sending unnecessary files to the model.

### 11.4 Model Gateway

Responsible for abstracting AI model providers.

The application should talk to the gateway, not directly to individual providers.

### 11.5 Cost-Aware Router

Responsible for deciding which model or backend should handle a task.

Routing factors include:

* task type;
* model capability;
* cost;
* privacy;
* latency;
* context window;
* user preference;
* budget limits.

### 11.6 Patch and Execution Engine

Responsible for proposing, validating, applying, and verifying file changes.

This component must be conservative and non-destructive by default.

### 11.7 Audit and Memory Store

Responsible for preserving durable project state.

Likely local directory:

```txt
.workbench/
```

Potential contents:

```txt
.workbench/
  config.json
  manifest.json
  audit.ndjson
  context/
  runs/
  patches/
  verification/
```

## 12. Architectural Constraints

The system must satisfy the following constraints:

1. It must run locally.
2. It must not require a paid AI subscription.
3. It must support optional hosted AI providers.
4. It must support optional self-hosted remote inference.
5. It must be provider-agnostic.
6. It must support non-destructive dry runs.
7. It must preserve audit history.
8. It must support deterministic verification.
9. It must keep generated project state in the repository.
10. It must be extensible through future plugins.
11. It must avoid hidden provider lock-in.
12. It must avoid hidden destructive actions.
13. It must support constrained developer hardware.
14. It must treat software engineering artifacts as first-class outputs.
15. It must support future monetization without making the local workflow useless.

## 13. Security and Privacy Principles

The product should treat repository data as sensitive.

It should include safeguards for:

* secret detection;
* redaction;
* provider boundary warnings;
* local-only mode;
* per-provider data sharing rules;
* audit logs;
* user approval before remote transmission;
* explicit model/provider configuration.

The product should make it clear when repository content may be sent to a remote model provider.

## 14. Monetization Hypothesis

The product may eventually be monetized without compromising local-first usefulness.

Possible monetization paths include:

1. paid hosted control plane;
2. managed remote inference;
3. team collaboration features;
4. hosted project memory and sync;
5. enterprise policy controls;
6. private template marketplace;
7. support subscriptions;
8. managed GPU burst compute;
9. paid plugin ecosystem;
10. premium UI features.

The open/local developer workflow should remain useful even without paid services.

## 15. Competitive Positioning

The product overlaps with several categories but should not be reduced to any one of them.

It is not just:

* an AI chatbot;
* a code editor;
* a scaffolder;
* a monorepo tool;
* a local model runner;
* a CI tool;
* a project management app.

It is best understood as:

> A local-first AI software engineering control plane.

Its differentiation should come from the combination of:

* provider agnosticism;
* cost-aware routing;
* local and remote self-hosted inference;
* repo intelligence;
* supervised patching;
* project memory;
* architecture discipline;
* verification-first workflows.

## 16. Initial Risks

### 16.1 Model Quality Risk

Local or small models may produce lower-quality output.

Mitigation:

* use retrieval and context packs;
* route hard tasks to stronger models;
* allow remote self-hosted inference;
* require verification;
* keep human approval in the loop.

### 16.2 Scope Creep Risk

The product could become too broad too quickly.

Mitigation:

* start with CLI MVP;
* focus on repo inspection, context packs, provider gateway, and supervised patching;
* defer full UI until core workflows work.

### 16.3 Provider Fragmentation Risk

Supporting many providers could create complexity.

Mitigation:

* define a strict provider interface;
* support OpenAI-compatible APIs early;
* treat specific providers as adapters.

### 16.4 Safety Risk

The product could damage repositories if file writes are unsafe.

Mitigation:

* dry-run by default for early versions;
* generate patches before applying;
* require approval;
* log all changes;
* support rollback guidance.

### 16.5 Cost Control Risk

Users may accidentally spend money on remote APIs or GPU compute.

Mitigation:

* budget caps;
* provider-level cost estimates;
* local-first defaults;
* explicit remote execution approval;
* per-run audit logs.

## 17. Success Criteria

The product is successful if a developer can:

1. initialize or inspect a repository;
2. generate project planning artifacts;
3. configure local and remote model providers;
4. ask useful questions about the repository;
5. generate a task-specific implementation plan;
6. produce a proposed patch;
7. review and apply that patch safely;
8. run verification;
9. receive a clean commit recommendation;
10. do all of this without being locked into one paid AI provider.

## 18. First Release Goal

The first meaningful release should prove this workflow:

```txt
Initialize project
→ inspect repository
→ configure model provider
→ generate context pack
→ generate work packet
→ propose patch
→ apply after approval
→ run verification
→ recommend commit
```

The first release does not need to be beautiful.

It needs to be trustworthy, useful, auditable, and extensible.

## 19. Immediate Next Documents

The next planning documents should be created in this order:

1. Product Charter
2. Stakeholder and User Model
3. Software Requirements Specification
4. Architecture Overview
5. ADR Index and ADR Template
6. ADR-0001: Local-First Provider-Agnostic AI Engineering Workbench
7. ADR-0002: Hybrid Local and Remote Self-Hosted Model Execution
8. ADR-0003: Cost-Aware Model Routing
9. ADR-0004: Repository as Durable Project Memory
10. ADR-0005: Supervised Patch and Execution Workflow

## 20. Initial Commit Recommendation

After creating this document, use the following atomic Conventional Commit:

```bash
git add docs/planning/00-product/PRODUCT-INCEPTION-BRIEF.md
git commit -m "docs(product): add product inception brief"
```

