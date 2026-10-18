---
name: namirial-retrieve-envelope-details
description: Retrieve comprehensive details about an envelope including its overview, files, history, elements, viewer links, and configuration.
api: openapi/namirial-esignanywhere-openapi.yml
operations:
- Envelope_Get
- Envelope_GetFiles
- Envelope_GetHistory
- Envelope_GetElements
- Envelope_GetViewerLinks
- Envelope_GetConfiguration
generated: '2026-10-18'
method: generated
generator: extract-docs-artifacts.py skills (deepseek)
source: openapi/namirial-esignanywhere-openapi.yml ; every operationId checked against the contract
---

# namirial-retrieve-envelope-details

Retrieve comprehensive details about an envelope including its overview, files, history, elements, viewer links, and configuration.

## Steps

1. 1. Get envelope overview by calling `Envelope_Get` with the envelopeId path parameter
2. 2. Retrieve envelope files and documents by calling `Envelope_GetFiles` with the envelopeId path parameter
3. 3. Get envelope event history by calling `Envelope_GetHistory` with the envelopeId path parameter
4. 4. Retrieve envelope elements by calling `Envelope_GetElements` with the envelopeId path parameter
5. 5. Get viewer links for active activities by calling `Envelope_GetViewerLinks` with the envelopeId path parameter
6. 6. Retrieve envelope configuration by calling `Envelope_GetConfiguration` with the envelopeId path parameter

## Rules

- Authentication required using basicAuth, oAuth2AuthCode, or oAuth2ClientCredentials schemes
- All operations use the envelopeId path parameter to identify the specific envelope
- All operations are GET requests for retrieving envelope information
- Server endpoint is https://esaw-conn-test.namirialtsp.com
