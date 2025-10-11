# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the documentation repository for the DoDays API, containing OpenAPI specifications and markdown documentation. The main purpose is to maintain API documentation and generate code/documentation from the OpenAPI specification.

## Key Architecture

- **OpenAPI Specification**: `openapi.yaml` contains the complete API specification for the DoDays API
- **Documentation**: Markdown files provide human-readable API documentation
- **Code Generation**: Uses OpenAPI Generator CLI for generating code from the specification
- **TypeScript SDK**: The OpenAPI schema generates the TypeScript SDK located at `../ts-sdk` using the `typescript-fetch` generator

## Development Commands

### OpenAPI Generator

```bash
# Generate code/documentation from OpenAPI spec
npx @openapitools/openapi-generator-cli generate

# Check available generators
npx @openapitools/openapi-generator-cli list
```

### Package Management

```bash
# Install dependencies
pnpm install

# Or with npm
npm install
```

## Important Files

- `openapi.yaml` - Complete OpenAPI 3.1 specification for DoDays API
- `openapitools.json` - Configuration for OpenAPI Generator CLI
- `01-Introduction.md` - API introduction and overview
- `02-Authentication.md` - Authentication flow documentation

## API Details

The DoDays API provides access to family account management at dodays.co.uk with:

- Token-based authentication (72-hour expiry)
- Multiple environments: Local, Staging, Production
- Contact: engineering@dodays.co.uk

## TypeScript SDK Generation

The `openapi.yaml` specification is used to automatically generate the TypeScript SDK (`@dodayslabs/ts-sdk`) located at `../ts-sdk`:

- **Generator**: Uses `typescript-fetch` generator from OpenAPI Generator CLI
- **Source**: Generated from `openapi.yaml` (this repository)
- **Output**: Generated code is placed in `../ts-sdk/src`
- **Build Process**:
  - `pnpm generate` - Generates TypeScript client from OpenAPI spec
  - `pnpm compile` - Compiles TypeScript to JavaScript
  - `pnpm build` - Runs both generate and compile

**IMPORTANT**: When modifying `openapi.yaml`, the changes will directly affect the generated TypeScript SDK. Always ensure:

- All endpoint definitions, schemas, and examples are properly maintained
- Changes are compatible with the `typescript-fetch` generator
- The SDK is regenerated and tested after specification changes
- Breaking changes are properly versioned in the SDK package
