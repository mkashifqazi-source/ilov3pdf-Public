# Processing lifecycles

~~~mermaid
flowchart TD
  F[Selected document] --> C{Tool processing boundary}
  C -->|Browser local| L[pdf-lib or local viewer]
  L --> B[Browser output / object URL]
  B --> BR[Download and object-URL release]
  C -->|Server assisted| U[Multipart file admission]
  U --> W[Random request workspace]
  W --> P[Operation module / required executable]
  P --> D[File or structured response]
  D --> X[Cleanup]
  P -->|Handled failure| X
  W -. interrupted request .-> S[Startup stale cleanup]
~~~

This diagram intentionally has no durable queue state: the reviewed processing path is request-bound.
