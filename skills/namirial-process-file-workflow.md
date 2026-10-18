---
name: namirial-process-file-workflow
description: Upload a file, prepare it for processing, download the completed file, and optionally delete it.
api: openapi/namirial-esignanywhere-openapi.yml
operations:
- File_Upload
- File_Prepare
- File_DownloadCompleted
- File_Delete
generated: '2026-10-18'
method: generated
generator: extract-docs-artifacts.py skills (deepseek)
source: openapi/namirial-esignanywhere-openapi.yml ; every operationId checked against the contract
---

# namirial-process-file-workflow

Upload a file, prepare it for processing, download the completed file, and optionally delete it.

## Steps

1. 1. Upload a file using `File_Upload` operation with the file data in the request body
2. 2. Prepare the uploaded file using `File_Prepare` operation to extract elements, document tags, and SigStrings
3. 3. Download the completed file using `File_DownloadCompleted` operation with the `fileId` path parameter
4. 4. Delete the uploaded file using `File_Delete` operation when no longer needed

## Rules

- Authentication requires either basicAuth (HTTP) or oAuth2AuthCode/oauth2ClientCredentials (OAuth2) schemes
- The API server endpoint is https://esaw-conn-test.namirialtsp.com
- File operations require proper file identification through parameters like `fileId`
- File uploads are for temporary use and may need to be deleted after processing
