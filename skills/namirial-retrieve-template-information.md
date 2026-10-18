---
name: namirial-retrieve-template-information
description: Find a template using filter criteria and retrieve its comprehensive details including overview, files, elements, and configuration.
api: openapi/namirial-esignanywhere-openapi.yml
operations:
- Template_Find
- Template_GetTemplateById
- Template_GetFiles
- Template_GetElements
- Template_GetConfiguration
generated: '2026-10-18'
method: generated
generator: extract-docs-artifacts.py skills (deepseek)
source: openapi/namirial-esignanywhere-openapi.yml ; every operationId checked against the contract
---

# namirial-retrieve-template-information

Find a template using filter criteria and retrieve its comprehensive details including overview, files, elements, and configuration.

## Steps

1. 1. Use `Template_Find` with filter criteria in the request body to locate templates matching your requirements.
2. 2. Use `Template_GetTemplateById` with the `templateId` from the find results to get the template overview.
3. 3. Use `Template_GetFiles` with the same `templateId` to retrieve the template's documents.
4. 4. Use `Template_GetElements` with the same `templateId` to get the elements belonging to the template documents.
5. 5. Use `Template_GetConfiguration` with the same `templateId` to obtain the template's configuration and activities.

## Rules

- Authentication requires either basicAuth (HTTP) or oAuth2AuthCode/oauth2ClientCredentials (OAuth2) schemes.
- All operations use the base server URL: https://esaw-conn-test.namirialtsp.com.
- The `templateId` path parameter must be provided for template-specific operations.
- Filter criteria must be specified in the request body for the `Template_Find` operation.
