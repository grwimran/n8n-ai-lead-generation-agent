# AI-Powered Lead Generation Automation

An automated lead discovery and qualification system built using n8n, LLMs, external search APIs, Redis, and Google Sheets.

## Overview

This project automates the process of discovering potential business leads based on industry, location, and target business criteria.

## Architecture

- **n8n:** Workflow orchestration and automation.
- **OpenRouter:** AI-powered search query planning.
- **External Search APIs:** Business and prospect discovery.
- **JavaScript:** Data transformation, validation, and deduplication.
- **Upstash Redis:** Job status and request tracking.
- **Google Sheets:** Lead storage and reporting.

## Key Features

- Dynamic search query generation.
- Automated business lead discovery.
- Lead normalization and deduplication.
- Public business contact extraction.
- Asynchronous job tracking.
- Google Sheets integration.

## Workflow

User Input → AI Search Planner → Search API → Lead Processing → Deduplication → Contact Extraction → Google Sheets.

## Technologies

n8n, OpenRouter, JavaScript, REST APIs, Upstash Redis, Google Sheets.

## Setup

1. Import the workflow JSON files into n8n.
2. Configure the required API credentials.
3. Configure Redis and Google Sheets integrations.
4. Update environment-specific settings.
5. Execute the workflow using the configured trigger.

**Security:** API credentials and private configuration values are intentionally excluded from this repository.
