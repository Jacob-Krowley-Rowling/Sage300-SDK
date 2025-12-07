# Payroll Configuration

This directory contains configuration files for payroll setup across Sage 300 SDK repositories.

## Overview

The payroll configuration system provides:
- Multi-repository payroll module setup
- Repository batching for efficient operations
- Domain and URL caching for API interactions
- Employee data schemas and templates
- Timesheet and payroll run processing

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

## Data Schemas

The `schemas/` directory contains JSON Schema definitions for payroll data:

### employee-schema.json
Defines the complete structure for employee payroll data including:
- **Personal Info**: Name, tax identifier (SSN/SIN), address, contact
- **Employment Info**: Hire date, pay rate, pay type (hourly/salary), pay frequency
- **Tax Info**: Federal, state/provincial, and local withholding settings
- **Banking Info**: Direct deposit accounts with split deposit support
- **Deductions**: Pre-tax (401k, RRSP, health insurance) and post-tax deductions

### timesheet-schema.json
Defines time and attendance data:
- Pay period dates
- Daily time entries with regular, overtime, and double-time hours
- Leave tracking (vacation, sick, personal, holiday)
- Approval workflow status

### payroll-run-schema.json
Defines payroll processing run configuration:
- Pay period and pay date
- Run type (regular, bonus, correction, final)
- Employee inclusion/exclusion
- Calculation totals
- Processing status and outputs

## Templates

The `templates/` directory contains sample data files:

| Template | Description |
|----------|-------------|
| `employee-template-ca.json` | Sample Canadian employee (CP module) |
| `employee-template-us.json` | Sample US employee (UP module) |
| `timesheet-template.json` | Sample bi-weekly timesheet |
| `payroll-run-template.json` | Sample payroll run configuration |

## Information Required to Pay an Employee

To process payroll for an employee, you need:

1. **Personal Information**
   - Full legal name
   - Tax identifier (SSN or SIN)
   - Date of birth
   - Address

2. **Employment Information**
   - Employee ID
   - Hire date
   - Pay rate and type (hourly/salary)
   - Pay frequency

3. **Tax Withholding**
   - Federal tax form (W-4 for US, TD1 for Canada)
   - State/Provincial withholding
   - Filing status and allowances

4. **Banking Information** (for direct deposit)
   - Bank routing/transit number
   - Account number
   - Account type

5. **Deductions**
   - Retirement contributions
   - Health insurance
   - Other voluntary deductions

6. **Time & Attendance**
   - Hours worked (for hourly employees)
   - Leave used
