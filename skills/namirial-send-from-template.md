---
generated: '2026-10-18'
method: generated
name: send-from-template
title: Send an envelope from a template
description: Locate a stored template, create a draft from it, adjust it, and send it.
api: openapi/namirial-esignanywhere-openapi.yml
operations:
- Template_Find
- Template_GetConfiguration
- Template_CreateDraft
- Draft_Update
- Draft_SendDraft
source: Grounded in openapi/namirial-esignanywhere-openapi.yml (Swagger 2.0, eSignAnywhere.Api V6); every operationId verified verbatim in the spec.
---

# Send an envelope from a template

Locate a stored template, create a draft from it, adjust it, and send it.

## Steps
1. `Template_Find` (POST /v6/template/find) — locate the template.
2. `Template_GetConfiguration` — inspect its activities.
3. `Template_CreateDraft` (POST /v6/template/createdraft) — create a draft from the template.
4. `Draft_Update` (POST /v6/draft/update) — fill in recipients/configuration.
5. `Draft_SendDraft` (POST /v6/draft/send) — send the draft as an envelope (a draft callback fires when the draft is used).

## Rules (from the spec's info.description)
- Auth: send the API token in the `apiToken` header (or as a bearer token). Create a separate API token per integration so one can be disabled without breaking others (Settings -> Api Tokens and Apps).
- Errors: handled errors come back as HTTP 40x with an error code and error info; HTTP 500 is a generic server error. Do not blindly retry 40x.
- State changes are pushed via callbacks (envelope callback on final state, envelope status callback on events, draft callback); prefer callbacks over polling.
- Idempotency: the spec documents no idempotency key; mutating POSTs (send, cancel, delete) are not safe to retry without first checking state with a read operation.
- Sandbox: `demo.esignanywhere.net`; production: `saas.esignanywhere.net/api`.
