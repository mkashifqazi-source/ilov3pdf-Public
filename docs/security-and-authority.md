# Document privacy and processing authority

Document contents cross different trust boundaries depending on the tool. Browser-local operations keep their processing in the browser. Server-assisted operations upload bytes to the Python service; AI-assisted paths can additionally send extracted text to a configured model service. A single site-wide browser-only privacy claim would be inaccurate.

Uploads are untrusted. The file helper avoids using client names as server paths, validates extension/MIME declarations and enforces request-size bounds. Temporary storage must remain private. A successful download cleanup hook is best effort, while startup stale removal is a recovery mechanism. Neither proves immediate erasure after a crash.

Production startup checks reject placeholder authentication secrets, absent explicit origins and unsafe cookie settings. JWT cookies and account/password handling are separate from tool processing. Their presence does not establish mandatory authentication for every tool or protection against every document exploit.

Document content and filenames should not enter analytics. The source QA specification explicitly checks that analytics omit content, filenames, exact sizes, hashes, emails and extracted text. Actual production log/analytics behavior requires verification.

Redaction, password protection, signature preparation and PDF/A workflows have operation-specific limits. A downloadable file does not automatically prove irrecoverable redaction, completed signature delivery or standards certification. The current private review must validate those claims before launch.

The showcase contains no user documents, benchmark corpus, extracted text, prompts, credentials or deployment settings.
