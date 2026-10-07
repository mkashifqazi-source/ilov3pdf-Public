# ilov3pdf

A modular PDF-tool application with explicit browser-local, server-assisted and optional AI-assisted processing boundaries.

Public Technical Overview · Private Development Repository

## Overview

ilov3pdf combines document operations with discoverable tool pages and guides. Its engineering centers on routing each operation to the right processing boundary and accurately explaining that boundary to the user.

## Problem

PDF workflows require very different capabilities: simple page rearrangement, OCR, Office conversion, document analysis and editing. A tool page cannot promise successful processing merely because its route exists; runtime dependencies, output fidelity, temporary data and errors need separate treatment.

## System Architecture

~~~mermaid
flowchart LR
  U[Browser tool page] --> L[Browser-local pdf-lib flows]
  U --> A[Shared multipart API client]
  A --> F[FastAPI processing service]
  F --> M[Modular PDF operations]
  M --> X[Optional external binaries / model]
  F --> T[(Private temporary request files)]
  F --> D[(SQLAlchemy account database)]
  C[Tool catalog and Markdown content] --> U
~~~

## Core Components

Data-driven tool/content pages; dedicated browser-local components; shared upload/error/download UI; Python modules for transformation, OCR, conversion, security, health and comparison; temporary file helpers; account service; and runtime dependency diagnostics.

## Key Technical Workflows

Browser-local: select → validate → transform → download → release object URL. Server-assisted: upload → random workspace → process → respond → cleanup, with failure cleanup and startup stale recovery. No durable background processing queue is established.

## Engineering Decisions

Server-assisted tools call FastAPI directly; legacy Next.js processing routes are stubs. Local tools use pdf-lib. Server files have random identities and best-effort cleanup. Runtime-dependent tools return explicit dependency failures rather than pretending to work.

## Reliability / Safety / Validation

Privacy is per operation. Server-assisted content leaves the browser. Cleanup hooks do not guarantee immediate erasure after interruption. Complex parsers/converters and synchronous work need resource and hosting validation.

## Technology Stack

Next.js, React, TypeScript, Tailwind CSS, pdf-lib, Markdown processing, FastAPI/Python, SQLAlchemy/SQLite, JWT/bcrypt, pypdf, PyMuPDF, pikepdf, Pillow and document/table libraries. Runtime paths reference LibreOffice, Tesseract, qpdf/Ghostscript and optional Ollama; availability is not assumed.

## Testing

Historical lint/build and backend smoke records coexist with a manual QA matrix containing unrun cases. Output quality, browser/mobile behavior and deployed runtime dependencies remain launch gates. No source builds or live processing were run for this task.

## Current Status

Development MVP / staging preparation. Production readiness, converter availability and complete manual QA remain unresolved. This repository contains original technical documentation only.

## Technical Documentation

- [architecture](docs/architecture.md)
- [data model](docs/data-model.md)
- [workflows](docs/workflows.md)
- [testing and validation](docs/testing-and-validation.md)
- [reliability and failure model](docs/reliability-and-failure-model.md)
- [security and authority](docs/security-and-authority.md)
- [technical decisions](docs/technical-decisions.md)
- [project status](docs/project-status.md)
- [processing lifecycle](diagrams/processing-lifecycle.md)

## Repository Notice

This repository contains the public technical documentation for the project. The production source code and internal development materials are maintained separately and are not published here.
