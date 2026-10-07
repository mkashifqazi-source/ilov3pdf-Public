# Technical decisions

## Direct backend processing path

**Context:** The frontend contains legacy tool API routes and a separate Python service.

**Decision:** Shared frontend tool client sends server-assisted processing to FastAPI; legacy Next.js routes are deprecated stubs.

**Why:** The private architecture record identifies this as the canonical path.

**Alternatives considered:** A frontend proxy is mentioned only as a potential later architecture change, not an implemented path.

**Consequences:** Hosting must configure the backend origin, CORS and connectivity explicitly.

**Current status:** Documented and supported by client/backend wiring.

## Browser-local core operations

**Context:** Common page/image transformations can run with a browser PDF library.

**Decision:** Dedicated merge, split and JPG-to-PDF flows use pdf-lib locally.

**Why:** The implementation and QA notes preserve a truthful processing/privacy boundary.

**Alternatives considered:** These flows replaced earlier server-assisted behavior according to the QA history; no formal benchmark comparison is claimed.

**Consequences:** Fewer uploads for those tools, with browser memory/device limits and separate local/server QA.

**Current status:** Implemented; manual cross-browser coverage remains incomplete.

## Random ephemeral request workspaces

**Context:** Server tools need input and output files.

**Decision:** Random directories/filenames, response/failure cleanup and startup stale cleanup.

**Why:** Avoid treating client names as storage paths and bound normal retention.

**Alternatives considered:** No historical comparison is documented.

**Consequences:** Crash recovery is best effort; cleanup still needs production monitoring.

**Current status:** Implemented helpers, without an independently verified deletion guarantee.
