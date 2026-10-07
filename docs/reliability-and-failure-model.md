# Reliability and failure model

| Failure | Expected observed boundary |
|---|---|
| Unsupported/empty/oversized upload | Admission failure with a user-facing message |
| Corrupt or encrypted document | Parser/tool validation failure rather than fake output |
| Missing converter or OCR executable | Structured dependency error or documented fallback |
| External process exceeds timeout | Timeout error and request-directory cleanup |
| Backend unavailable | Frontend distinguishes connectivity/configuration failure from unauthenticated status |
| Response completes | Cleanup is scheduled after file response |
| Process terminates before cleanup | Temporary data can survive; sufficiently old directories are eligible for best-effort cleanup on a later startup |
| Model unavailable | Explicit extractive fallback where supported; translation remains dependent |

Random workspace names isolate request file locations, but do not themselves establish resource sandboxing. Direct synchronous calls can consume CPU/block capacity within an async service. A subprocess timeout does not automatically bound every in-process PDF parser.

The audit records missing local system binaries and an unverified Linux backend image. Frontend tool wiring therefore cannot prove end-to-end conversion readiness. SQLite also requires durable single-instance storage; multi-instance deployment can split account state if each instance has independent local storage.

No fixed deletion guarantee, zero-retention certification, malware isolation, conversion-fidelity guarantee or background-job resilience is claimed. Operational cleanup and concurrency must be validated in the selected hosting environment.
