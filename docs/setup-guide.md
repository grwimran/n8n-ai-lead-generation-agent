# AI Lead Generation Agent – Setup Guide

## 1. Prerequisites

Before importing the workflow, you need:

- An n8n Cloud account or self-hosted n8n instance.
- OpenRouter API key.
- External search API credentials.
- Google Sheets account and credentials.
- Upstash Redis credentials (if using job tracking).

## 2. Import Workflow

1. Log in to your n8n instance.
2. Open the Workflows section.
3. Select Import from File.
4. Choose `workflows/main-orchestrator.json`.
5. Open the imported workflow.
6. Review all nodes and connections.

## 3. Configure Credentials

Configure the required credentials inside n8n:

### OpenRouter
- Create an API key.
- Configure the appropriate authentication credential.
- Select a supported LLM model.

### Search API
- Configure your external search API credentials.
- Verify the API endpoint and request parameters.

### Google Sheets
- Connect your Google account.
- Select the destination spreadsheet.
- Map workflow output fields to the appropriate columns.

### Upstash Redis
- Configure Redis REST authentication if job tracking is enabled.
- Verify connectivity and request status updates.

## 4. Configure Workflow Parameters

Review the following settings:

- Default business type.
- Default geographic location.
- Maximum lead limit.
- Contact fields to extract.
- Output destination.
- Search API pagination settings.

## 5. Example Webhook Request

```json
{
  "keywords": "Trucking Companies, United States, Michigan"
}
```

The workflow should validate the input and generate search queries based on the requested business category and location.

## 6. Execute and Test

1. Save the workflow.
2. Activate it if using a production webhook.
3. Submit a test request.
4. Inspect each execution.
5. Verify that search results are processed correctly.
6. Confirm that leads are stored in Google Sheets.

## 7. Troubleshooting

| Problem | Possible cause |
|---|---|
| HTTP 429 | Search API rate limit |
| HTTP 403 | Website blocks automated access |
| Empty search results | Search query or API issue |
| Missing contact details | Website does not publish contact information |
| Redis failure | Incorrect credentials or connectivity |
| Google Sheets error | Missing permissions or incorrect spreadsheet mapping |

## 8. Security

- Never commit API keys or access tokens to GitHub.
- Configure credentials directly inside n8n.
- Do not publish private webhook URLs.
- Use appropriate API access permissions.
- Review exported workflow JSON before sharing.

## 9. Important Note

This repository contains the exported main orchestrator workflow. Additional dependencies, credentials, and external services must be configured separately before the complete system can run.