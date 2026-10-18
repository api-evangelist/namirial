---
generated: '2026-10-18'
method: generated
name: send-document-for-signature
title: Send a document for signature
description: Upload a PDF to eSignAnyWhere, let the platform extract fields and tags, send it as an envelope to signers, then fetch viewer links.
api: openapi/namirial-esignanywhere-openapi.yml
operations:
- File_Upload
- File_Prepare
- Envelope_Send
- Envelope_Get
- Envelope_GetViewerLinks
source: Grounded in openapi/namirial-esignanywhere-openapi.yml (Swagger 2.0, eSignAnywhere.Api V6); every operationId verified verbatim in the spec.
---

# Send a document for signature

Upload a PDF to eSignAnyWhere, let the platform extract fields and tags, send it as an envelope to signers, then fetch viewer links.

## Steps
1. `File_Upload` (POST /v6/file/upload, multipart `File`) — returns a temporary file id.
2. `File_Prepare` (POST /v6/file/prepare) — extract form elements, advanced document tags and SigStrings from the uploaded files.
3. `Envelope_Send` (POST /v6/envelope/send, body `EnvelopeSendRequest`) — create and send the envelope referencing the uploaded file ids and the signer activities.
4. `Envelope_Get` (GET /v6/envelope/{envelopeId}) — confirm status.
5. `Envelope_GetViewerLinks` (GET /v6/envelope/{envelopeId}/viewerlinks) — obtain SignAnyWhere Viewer links for active activities when embedding signing.

## Rules (from the spec's info.description)
- Auth: send the API token in the `apiToken` header (or as a bearer token). Create a separate API token per integration so one can be disabled without breaking others (Settings -> Api Tokens and Apps).
- Errors: handled errors come back as HTTP 40x with an error code and error info; HTTP 500 is a generic server error. Do not blindly retry 40x.
- State changes are pushed via callbacks (envelope callback on final state, envelope status callback on events, draft callback); prefer callbacks over polling.
- Idempotency: the spec documents no idempotency key; mutating POSTs (send, cancel, delete) are not safe to retry without first checking state with a read operation.
- Sandbox: `demo.esignanywhere.net`; production: `saas.esignanywhere.net/api`.
