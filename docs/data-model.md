# Domain model

| Concept | Contents | Boundary |
|---|---|---|
| Tool definition | Slug, category, description and UI/processing information | Discoverability does not establish runtime capability |
| Tool-page content | Instructions, limitations, FAQs and related tools | Claims must match the processing path |
| Upload | Client filename, declared MIME, byte stream | Untrusted input; original name is not a server pathname |
| Processing workspace | Random directory and random input/output files | Ephemeral request storage, not a durable queued job |
| Operation parameters | Page ranges, ordering, conversion/annotation options | Validated according to the chosen operation |
| Download | Output media type, response filename and stream | Cleanup begins after response handling |
| Health/compare result | Derived document observations | Report scope is bounded by parser and document availability |
| Account | User/profile/password data | Private authentication state |
| Article/guide | Markdown content and route metadata | Separate from uploads and generated output |

Browser-local tools hold files and generated objects in browser memory. Download object URLs are released during reset/replacement/unmount lifecycle. No server upload follows merely from the local merge operation.

Server-assisted uploads use extension and declared MIME checks, permit some generic MIME declarations and enforce bounds on bytes saved by these helpers. This is not an established ingress-body limit or a bound on earlier multipart parsing. These are admission checks, not comprehensive content-type authentication or malware scanning. Parser failures still need safe handling.

The inspected service has no persisted canonical ProcessingJob state machine. A local job directory is a request workspace, so calling it a distributed asynchronous job would overstate the architecture.
