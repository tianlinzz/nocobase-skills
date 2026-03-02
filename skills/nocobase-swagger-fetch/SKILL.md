---
name: nocobase-swagger-fetch
description: Fetch NocoBase Swagger/OpenAPI documents by namespace via nocobase-api-call. Use when users need latest endpoint docs, request schemas, or operation details before building API calls.
argument-hint: "[namespace]"
allowed-tools: Bash, Read
---

# Goal

Retrieve live Swagger/OpenAPI JSON from NocoBase for endpoint discovery and request construction.

# Workflow

1. Ensure API authentication is ready by following `nocobase-api-call` skill rules.
2. Confirm namespace explicitly (no default in this skill).
3. Execute `scripts/get-swagger.sh <namespace>`.
4. This script delegates request execution to `../nocobase-api-call/scripts/nocobase-api.sh`.
5. Return raw JSON or pipe to `jq` for path/operation extraction.
6. If response indicates `404 Not Found`, prompt user to check and enable `API Docs` plugin, then retry.

# 404 Handling Note

- `404 Not Found` from `/swagger:get` usually means `API Docs` plugin is not enabled.
- Prompt user to enable `API Docs` in admin plugins before continuing.

# Resources

- `scripts/get-swagger.sh` - Fetch Swagger JSON by calling `nocobase-api-call`
- `../nocobase-api-call/` - Shared base skill for authentication and HTTP requests

# Usage

```bash
# Collection manager namespace
./scripts/get-swagger.sh plugins%2Fdata-source-main

# List all paths
./scripts/get-swagger.sh plugins%2Fdata-source-main | jq '.paths | keys'
```
