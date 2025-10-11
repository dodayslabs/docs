# DoDays API Documentation

Documentation and OpenAPI specification for the DoDays API - providing access to family account management at [dodays.co.uk](https://dodays.co.uk).

## Overview

This repository contains:

- **OpenAPI 3.1 Specification** (`openapi.yaml`) - Complete API specification for the DoDays API
- **API Documentation** - Human-readable markdown documentation
- **Code Generation Configuration** - Settings for generating SDKs and documentation from the OpenAPI spec

The OpenAPI specification in this repository is the source of truth for the DoDays API and is used to automatically generate the [TypeScript SDK](https://github.com/dodayslabs/ts-sdk).

## Getting Started

### Prerequisites

- Node.js (v24.9.0 or higher)
- pnpm

### Installation

```bash
# Using pnpm
pnpm install
```

## Working with the OpenAPI Specification

### Generate Code/Documentation

```bash
# Generate code from the OpenAPI spec
npx @openapitools/openapi-generator-cli generate

# List available generators
npx @openapitools/openapi-generator-cli list
```

### TypeScript SDK Generation

The `openapi.yaml` specification automatically generates the TypeScript SDK (`@dodayslabs/ts-sdk`) located on npm at [package/@dodayslabs/ts-sdk](https://www.npmjs.com/package/@dodayslabs/ts-sdk):

- **Generator**: `typescript-fetch` (OpenAPI Generator CLI)
- **Output**: [ts-sdk/src](https://github.com/dodayslabs/ts-sdk/src)
- **Build Commands** (run from ts-sdk directory):
  ```bash
  pnpm generate  # Generate TypeScript client
  pnpm compile   # Compile TypeScript to JavaScript
  pnpm build     # Run both generate and compile
  ```

> **⚠️ Important**: Changes to `openapi.yaml` directly affect the generated TypeScript SDK. After modifying the specification:
>
> 1. Ensure compatibility with the `typescript-fetch` generator
> 2. Regenerate the SDK
> 3. Test the SDK thoroughly
> 4. Version breaking changes appropriately

## Repository Structure

```
.
├── openapi.yaml              # OpenAPI 3.1 specification
├── openapitools.json         # OpenAPI Generator CLI configuration
├── 01-Introduction.md        # API introduction and overview
├── 02-Authentication.md      # Authentication flow documentation
└── README.md                 # This file
```

## API Information

- **Authentication**: Token-based (72-hour expiry)
- **Environments**: Local, Staging, Production
- **Contact**: engineering@dodays.co.uk

## Documentation Files

- [Introduction](01-Introduction.md) - Getting started with the DoDays API
- [Authentication](02-Authentication.md) - Authentication flow and token management

## Contributing

When modifying the OpenAPI specification:

1. Ensure all endpoint definitions, schemas, and examples are valid
2. Maintain compatibility with code generators
3. Update relevant documentation files
4. Test generated code after changes
5. Follow semantic versioning for breaking changes
