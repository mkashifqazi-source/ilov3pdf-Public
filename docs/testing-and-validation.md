# Testing and validation

The project uses lint/build checks, backend health/system checks, targeted smoke tests and a detailed manual QA matrix. Source audits record historical frontend passes and backend smoke checks. The QA matrix leaves many desktop/mobile and output-quality cases not run; no new tests were executed for this showcase.

Verification needs to examine the output, not merely a successful HTTP response. Merge checks page totals/order; split checks selected ranges; image conversion checks orientation/dimensions; compression checks readability and actual reduction; OCR checks searchability and transcription quality; Office conversion checks editable structure and layout limits.

The matrix includes invalid, corrupt, encrypted, oversized and multi-file inputs; download opening; mobile upload/reset/download; runtime dependency failure; processing/privacy badge accuracy; and privacy-safe analytics. It explicitly refuses to mark Pass without the actual test.

Staging gates cover production URL configuration, cookies/CORS, required binaries, backend image smoke and rollback. Dependency advisories and frontend version drift remain tracked issues. These source-recorded checks are not a claim of current production readiness.

Cleanup tests should include client disconnect, converter timeout, interrupted process and stale-workspace recovery. Production load/isolation and durable cleanup behavior were not established by the reviewed evidence.
