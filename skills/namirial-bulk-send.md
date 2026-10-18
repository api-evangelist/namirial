---
generated: '2026-10-18'
method: generated
name: bulk-send
title: Bulk-send an envelope
description: Send one envelope to many recipients as a bulk and manage the bulk children.
api: openapi/namirial-esignanywhere-openapi.yml
operations:
- EnvelopeBulk_Send
- EnvelopeBulk_Get
- EnvelopeBulk_Find
- EnvelopeBulk_Remind
- EnvelopeBulk_Cancel
source: Grounded in openapi/namirial-esignanywhere-openapi.yml (Swagger 2.0, eSignAnywhere.Api V6); every operationId verified verbatim in the spec.
---

# Bulk-send an envelope

Send one envelope to many recipients as a bulk and manage the bulk children.

## Steps
1. `EnvelopeBulk_Send` (POST /v6/envelopebulk/send) — create and send the bulk.
2. `EnvelopeBulk_Get` (GET /v6/envelopebulk/{bulkId}) — overview of the bulk and its children.
3. `EnvelopeBulk_Find` — locate bulks by filter.
4. `EnvelopeBulk_Remind` — remind active activities of all children.
5. `EnvelopeBulk_Cancel` — cancel all active children.

## Rules (from the spec's info.description)
- Auth: send the API token in the `apiToken` header (or as a bearer token). Create a separate API token per integration so one can be disabled without breaking others (Settings -> Api Tokens and Apps).
- Errors: handled errors come back as HTTP 40x with an error code and error info; HTTP 500 is a generic server error. Do not blindly retry 40x.
- State changes are pushed via callbacks (envelope callback on final state, envelope status callback on events, draft callback); prefer callbacks over polling.
- Idempotency: the spec documents no idempotency key; mutating POSTs (send, cancel, delete) are not safe to retry without first checking state with a read operation.
- Sandbox: `demo.esignanywhere.net`; production: `saas.esignanywhere.net/api`.
