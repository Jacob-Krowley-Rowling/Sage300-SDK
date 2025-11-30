# Payroll Configuration

This directory contains configuration files for payroll setup across Sage 300 SDK repositories.

## Overview

The payroll configuration system provides:
- Multi-repository payroll module setup
- Repository batching for efficient operations
- Domain and URL caching for API interactions

## Configuration Files

### payroll-config.json
Main payroll configuration file that defines:
- Supported payroll modules (Canada Payroll, US Payroll)
- Repository settings for payroll features
- Cache settings for domain/URL tracking

### repo-batch-config.json
Repository batching configuration for:
- Batch operation settings (size, concurrency, retry)
- Repository definitions with priority ordering
- Payroll-specific batch groupings

### cache-config.json
Domain and URL caching configuration for:
- Cache TTL and size settings
- Domain allow/deny lists
- URL patterns for payroll API endpoints
- Interaction logging settings

### cache-data.json
Runtime cache storage for tracked domains and URLs.

### interaction-log.json
Log of API interactions for auditing and debugging.

## Supported Payroll Modules

| Module ID | Module Name     | Resource Path |
|-----------|-----------------|---------------|
| CP        | Canada Payroll  | resources/Sage300Resources/Sage.CA.SBS.ERP.Sage300.PR.Resources |
| UP        | US Payroll      | resources/Sage300Resources/Sage.CA.SBS.ERP.Sage300.PR.Resources |

## API Patterns

The following payroll API patterns are configured:
- Calculate Payroll: `PR/PRCalculatePayroll('$process')`
- Payroll Checks: `PR/PRPayrollChecks`
- Company Payroll Taxes: `PR/PRCompanyPayrollTaxes`

## Usage

1. Configure payroll modules in `payroll-config.json`
2. Set up repository batching in `repo-batch-config.json`
3. Configure caching settings in `cache-config.json`
4. The system will automatically track domains and URLs in `cache-data.json`
5. Interactions are logged to `interaction-log.json`

## Related Resources

- [Web API Sample Integration](../samples/WebApi_SampleIntegration/)
- [Web API Postman Collection](../samples/WebAPI_Postman/)
- [Payroll Resources](../resources/Sage300Resources/Sage.CA.SBS.ERP.Sage300.PR.Resources/)
