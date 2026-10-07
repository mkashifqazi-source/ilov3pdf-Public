# Upload, processing and download workflows

## Browser-local PDF operation

Select files → validate supported input → load with browser library → apply page/image operation → produce output bytes → create download object URL → download or reset → release object URL. The browser-local badge explains where processing happens. Memory and device capacity still bound the operation.

## Server-assisted file output

Select tool/input/options → shared API client builds multipart request → FastAPI makes a random workspace → stream-save with aggregate size limits → call the operation module → return file response → background cleanup. Handled exceptions remove the workspace and map validation, dependency and timeout failures into actionable messages.

Some operations return JSON evidence instead of a transformed file. Their workspace cleanup belongs to that route's lifecycle; the common file-response wrapper alone is not proof every route cleans correctly.

## Runtime-dependent conversion

The tool requires its converter/OCR binary or uses a documented Python fallback. Missing runtime dependencies remain explicit. An installed Python package is insufficient to prove LibreOffice, Tesseract, qpdf, Ghostscript or a formal PDF/A validator is usable in a deployed image.

## Optional AI

Readable document text feeds an optional Ollama path. Several tools have an extractive fallback; translation requires the model path. OCR is prerequisite for useful text from scans. Model-generated interpretation, signature-request preparation and formal document certification must not be confused with verified facts, sent invitations or legal guarantees.

## Content navigation

Tool catalog → tool page → processing interface, instructions and accurate privacy/limitations → related tools/guides. Search-indexable content routes are separate from API/upload/result artifacts.
