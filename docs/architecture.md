# AI Lead Generation Agent – Architecture

## 1. Overview

The Universal AI Lead Generation Agent is an automated lead discovery and data extraction system built using n8n.

It allows users to submit business keywords, industries, and geographic locations to discover relevant companies and collect publicly available business contact information.

The system uses AI-powered search planning, external search APIs, data processing, website extraction, and Google Sheets integration.

## 2. High-Level Architecture

```text
User / External Application
          |
          v
     n8n Webhook
          |
          v
 Validate & Normalize Input
          |
          v
    AI Search Planner
       (OpenRouter)
          |
          v
     Parse AI Plan
          |
          v
    Split Search Queries
          |
          v
 External Search API
          |
          v
    Parse Search Results
          |
          v
    Deduplicate Leads
          |
          v
      Limit & Clean
          |
          v
 Fetch Company Websites
          |
          v
 Extract Public Contacts
          |
          v
    Google Sheets
```

## 3. Main Components

### Input and Webhook
Receives lead-generation requests through an n8n webhook.

Example input:

```json
{
  "keywords": "Trucking Companies, United States, Michigan"
}
```

### Input Validation and Normalization
- Validates incoming requests.
- Normalizes keyword formats.
- Extracts business categories and geographic information.
- Applies default values where necessary.
- Generates or preserves a unique request ID.

### AI Search Planner
Uses an LLM through OpenRouter to interpret the user's requirements and generate relevant search queries.

### External Search API
Uses external search services to discover relevant businesses and search results.

### Lead Processing
- Parses search results.
- Extracts business names, websites, addresses, and available details.
- Removes duplicate records.
- Applies lead limits.
- Normalizes the output structure.

### Website Contact Extraction
Visits publicly accessible company websites and attempts to extract:
- Business email addresses.
- Business phone numbers.
- Website domains.
- Public contact information.

Website access restrictions and failed requests are handled separately.

### Google Sheets Integration
Stores processed lead information for review and sales follow-up.

## 4. Data Management

The lead records can contain:

- Company name
- Website
- Company domain
- Place ID
- Business address
- Country
- Business phone
- Public business emails
- Candidate business phones
- Lead status
- Contact review status
- Website fetch status

## 5. Job Tracking

Upstash Redis can be used to maintain request execution status.

Example lifecycle:

```text
Queued → Processing → Done
```

A unique request ID helps associate execution status with the original request.

## 6. Error Handling

The workflow accounts for external service limitations, including:

- API rate limiting (HTTP 429).
- Website access restrictions (HTTP 403).
- Failed website requests.
- Missing or incomplete search results.
- Invalid API responses.

Each processing stage should validate its inputs and outputs before passing data to the next stage.

## 7. Technology Stack

| Technology | Purpose |
|---|---|
| n8n | Workflow orchestration |
| OpenRouter | LLM integration |
| External Search APIs | Business discovery |
| JavaScript | Data transformation |
| Upstash Redis | Job tracking |
| Google Sheets | Lead storage |
| REST APIs | External integrations |

## 8. Design Approach

The system follows a modular automation approach. Search planning, lead discovery, data processing, and contact extraction are handled as separate logical stages.

This makes the workflow easier to maintain, troubleshoot, and extend with additional search providers or CRM integrations.