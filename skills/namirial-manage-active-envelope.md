---
generated: '2026-10-18'
method: generated
name: manage-active-envelope
title: Manage an in-flight envelope
description: Remind, replace a signer, restart an expired envelope, or cancel it.
api: openapi/namirial-esignanywhere-openapi.yml
operations:
- Envelope_Get
- Envelope_Remind
- EnvelopeActivity_Replace
- Envelope_RestartExpired
- Envelope_Cancel
source: Grounded in openapi/namirial-esignanywhere-openapi.yml (Swagger 2.0, eSignAnywhere.Api V6); every operationId verified verbatim in the spec.
---

# Manage an in-flight envelope

Remind, replace a signer, restart an expired envelope, or cancel it.

## Steps
1. `Envelope_Get` — read current status first (these mutations are not idempotent).
2. `Envelope_Remind` (POST /v6/envelope/remind) — nudge active activities.
3. `EnvelopeActivity_Replace` (POST /v6/envelope/activity/replace) — swap an unfinished activity (e.g. wrong signer).
4. `Envelope_RestartExpired` (POST /v6/envelope/restartexpired) — restart if expired.
5. `Envelope_Cancel` (POST /v6/envelope/cancel) — cancel an active envelope.

## Rules (from the spec's info.description)
- Auth: send the API token in the `apiToken` header (or as a bearer token). Create a separate API token per integration so one can be disabled without breaking others (Settings -> Api Tokens and Apps).
- Errors: handled errors come back as HTTP 40x with an error code and error info; HTTP 500 is a generic server error. Do not blindly retry 40x.
- State changes are pushed via callbacks (envelope callback on final state, envelope status callback on events, draft callback); prefer callbacks over polling.
- Idempotency: the spec documents no idempotency key; mutating POSTs (send, cancel, delete) are not safe to retry without first checking state with a read operation.
- Sandbox: `demo.esignanywhere.net`; production: `saas.esignanywhere.net/api`.
