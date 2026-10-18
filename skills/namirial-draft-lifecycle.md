---
name: namirial-draft-lifecycle
description: Create, configure, and send a draft for signature collection.
api: openapi/namirial-esignanywhere-openapi.yml
operations:
- Draft_Create
- Draft_Update
- Draft_Get
- Draft_GetConfiguration
- Draft_SendDraft
generated: '2026-10-18'
method: generated
generator: extract-docs-artifacts.py skills (deepseek)
source: openapi/namirial-esignanywhere-openapi.yml ; every operationId checked against the contract
---

# namirial-draft-lifecycle

Create, configure, and send a draft for signature collection.

## Steps

1. 1. Create a new draft using `Draft_Create` with required draft configuration fields
2. 2. Update the draft configuration using `Draft_Update` with the draftId and updated configuration fields
3. 3. Get draft overview using `Draft_Get` with the draftId path parameter
4. 4. Get draft configuration using `Draft_GetConfiguration` with the draftId path parameter
5. 5. Send the draft using `Draft_SendDraft` with the draftId and send parameters

## Rules

- Authentication requires either basicAuth (HTTP) or oAuth2AuthCode/oAuth2ClientCredentials (OAuth2)
- All operations use the base server URL: https://esaw-conn-test.namirialtsp.com
- Draft operations require draftId path parameter for most operations
- POST operations for draft management require appropriate request bodies
