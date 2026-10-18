---
generated: '2026-10-18'
method: generated
name: download-signed-documents
title: Track an envelope and download signed documents
description: Find envelopes, inspect history, and download the files of a completed envelope.
api: openapi/namirial-esignanywhere-openapi.yml
operations:
- Envelope_Find
- Envelope_Get
- Envelope_GetHistory
- Envelope_GetFiles
- File_DownloadCompleted
source: Grounded in openapi/namirial-esignanywhere-openapi.yml (Swagger 2.0, eSignAnywhere.Api V6); every operationId verified verbatim in the spec.
---

# Track an envelope and download signed documents

Find envelopes, inspect history, and download the files of a completed envelope.

## Steps
1. `Envelope_Find` (POST /v6/envelope/find) — filter envelopes (or use the id delivered by the envelope callback).
2. `Envelope_Get` — check the envelope reached a completed state.
3. `Envelope_GetHistory` — read the event history for audit.
4. `Envelope_GetFiles` — list documents and related files (e.g. audit trail).
5. `File_DownloadCompleted` (GET /v6/file/{fileId}) — download each file; only valid for completed envelopes.

## Rules (from the spec's info.description)
- Auth: send the API token in the `apiToken` header (or as a bearer token). Create a separate API token per integration so one can be disabled without breaking others (Settings -> Api Tokens and Apps).
- Errors: handled errors come back as HTTP 40x with an error code and error info; HTTP 500 is a generic server error. Do not blindly retry 40x.
- State changes are pushed via callbacks (envelope callback on final state, envelope status callback on events, draft callback); prefer callbacks over polling.
- Idempotency: the spec documents no idempotency key; mutating POSTs (send, cancel, delete) are not safe to retry without first checking state with a read operation.
- Sandbox: `demo.esignanywhere.net`; production: `saas.esignanywhere.net/api`.
