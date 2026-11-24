# Universal AI Lead Generation Agent

An AI-powered lead generation automation system built using n8n, LLMs, external search APIs, and Google Sheets.

## Overview

This project automates business lead discovery based on user-provided keywords, business categories, and geographic locations.

## Architecture

1. Receive lead-generation requests through a webhook.
2. Validate and normalize user input.
3. Generate search queries using an AI model through OpenRouter.
4. Discover relevant businesses using external search APIs.
5. Parse, normalize, and deduplicate lead records.
6. Extract publicly available business contact information from company websites.
7. Store processed leads in Google Sheets.

## Technologies

- n8n
- OpenRouter / LLMs
- REST APIs
- JavaScript
- Google Sheets
- Upstash Redis

## Repository Structure

- `workflows/` – Exported n8n workflow.
- `docs/` – Architecture and setup documentation.
- `screenshots/` – Workflow screenshots.

## Setup

1. Import `workflows/main-orchestrator.json` into n8n.
2. Configure the required API credentials.
3. Configure Google Sheets and Redis integrations where required.
4. Update environment-specific settings.
5. Execute the workflow using its configured trigger.

## Security

API credentials, tokens, and private configuration values must not be committed to this repository.
