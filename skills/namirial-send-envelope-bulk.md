---
name: namirial-send-envelope-bulk
description: Create and send an envelope bulk with multiple child envelopes.
api: openapi/namirial-esignanywhere-openapi.yml
operations:
- EnvelopeBulk_Send
- EnvelopeBulk_Get
- EnvelopeBulk_Find
generated: '2026-10-18'
method: generated
generator: extract-docs-artifacts.py skills (deepseek)
source: openapi/namirial-esignanywhere-openapi.yml ; every operationId checked against the contract
---

# namirial-send-envelope-bulk

Create and send an envelope bulk with multiple child envelopes.

## Steps

1. 1. Use `EnvelopeBulk_Send` POST /v6/envelopebulk/send to create and send the envelope bulk
2. 2. Use `EnvelopeBulk_Get` GET /v6/envelopebulk/{bulkId} to check the status of the sent bulk
3. 3. Use `EnvelopeBulk_Find` POST /v6/envelopebulk/find to search for envelope bulks matching filter criteria

## Rules

- Authentication required via basicAuth, oAuth2AuthCode, or oAuth2ClientCredentials schemes
- All operations use the https://esaw-conn-test.namirialtsp.com server endpoint
