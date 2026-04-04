---
name: firecrawl
description: Use this skill when working with Firecrawl. Triggers when user mentions Firecrawl or imports from it.
---

# Firecrawl

## What this is
Firecrawl is an API that enables users to search, scrape, and interact with the web at scale. It provides a powerful tool for powering AI agents with clean web data. Firecrawl is also open source, available on GitHub.

## Installation
```bash
pip install firecrawl
```
However, the exact installation command is not provided in the documentation. 

## Key concepts
The most important APIs and patterns in Firecrawl include:
- `scrape`: allows users to scrape any page and extract data.
- `interact`: enables users to click, type, and extract data from a webpage.
Example:
```json
[
  {
    // Example scrape configuration
  }
]
```
## Correct usage patterns
To use Firecrawl, users can follow these patterns:
- Scrape a webpage using the `scrape` endpoint.
- Interact with a webpage using the `interact` endpoint.
Example:
```json
[
  {
    "endpoint": "scrape",
    "url": "https://example.com",
    "autorun": true
  }
]
```
## Common mistakes to avoid
Common mistakes to avoid when using Firecrawl include:
- Not checking the API documentation for the most up-to-date information.
- Not handling errors and exceptions properly.

## File and folder conventions
Firecrawl files and folders follow standard conventions:
- Configuration files are typically stored in a `config` directory.
- API endpoints are accessed through the `https://www.firecrawl.dev/` base URL.
- The `playground` endpoint is used for testing and experimenting with Firecrawl.