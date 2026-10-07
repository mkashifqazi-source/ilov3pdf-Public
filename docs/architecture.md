# Architecture and processing boundaries

ilov3pdf has a Next.js/React tool and content frontend plus a separate FastAPI processing/account backend. Public tool metadata and page content are data-driven. Markdown articles/guides, route metadata, sitemap and robots definitions support the content surface. Generated tool pages are not proof that every underlying operation is production-ready.

There are two implemented processing paths. Dedicated Merge PDF, Split PDF and JPG-to-PDF components use pdf-lib in the browser. Reader/share workflows also have browser-local behavior. Server-assisted tools send multipart requests through the shared frontend API client directly to FastAPI. Next.js tool API routes are deprecated stubs, rather than the processing authority.

FastAPI dispatches to modules for basic edits, conversion, OCR, optimization, security transformations, health/compare reports and optional AI operations. Tools select Python libraries and external executables according to their actual requirements. Dependency availability is exposed by a system check and reflected in tool errors.

Uploads receive random filenames in random per-request directories. Route wrappers validate/save input, call the processing function and return either a file response or structured JSON. File responses schedule directory cleanup after response handling; handled failure paths attempt immediate cleanup; startup attempts removal of sufficiently old directories. Cancellation, disconnects and process death are not proven to share that handled-exception path. These are best-effort lifecycle controls, not proof of forensic erasure.

Async upload/HTTP functions coexist with direct synchronous processing calls. No durable processing queue, resumable job API or asynchronous worker pool was established. Long CPU/converter work is a deployment/concurrency constraint.

Account state uses SQLAlchemy with SQLite by default and JWT cookies. A relational production migration is described as future work. The non-sensitive deployment boundary is a frontend host, an independently hosted Python service, private temporary disk, account database and optional local model/runtime binaries.
