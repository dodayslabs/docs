# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the documentation repository for the DoDays API, containing OpenAPI specifications and markdown documentation. The main purpose is to maintain API documentation and generate code/documentation from the OpenAPI specification.

## Key Architecture

- **OpenAPI Specification**: `openapi.yaml` contains the complete API specification for the DoDays API
- **Documentation**: Markdown files provide human-readable API documentation
- **Code Generation**: Uses OpenAPI Generator CLI for generating code from the specification

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

When modifying the OpenAPI specification, ensure all endpoint definitions, schemas, and examples are properly maintained for code generation compatibility.