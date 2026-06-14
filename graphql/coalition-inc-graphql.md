# Coalition GraphQL Schema

## Overview

This conceptual GraphQL schema models the Coalition Active Insurance API and Exploit Scoring System (ESS) API as a unified graph. Coalition is a cyber insurance and active risk management provider that exposes broker-facing APIs for rating, quoting, binding, and managing commercial insurance policies across Cyber, Technology E&O, Executive Risks, and other lines. The ESS API provides public vulnerability intelligence over 200,000+ CVEs.

The schema covers the full insurance lifecycle: application intake, security assessment, quote generation, bind operations, policy management, document generation, endorsements, renewals, claims, and webhook event delivery. It also surfaces the ESS vulnerability intelligence surface used in underwriting.

## Schema Source

Conceptual schema derived from:

- Coalition Active Insurance API documentation (partner-gated): https://docs.coalitioninc.com/
- Coalition ESS API (public): https://ess-api.coalitioninc.com/docs
- Coalition broker overview: https://www.coalitioninc.com/brokers/api
- Coalition product pages: https://www.coalitioninc.com/cyber-insurance

## Root Types

### Query

- `policy(id: ID!)` — Retrieve a policy by ID
- `policies(filter: PolicyFilter)` — List policies with optional filtering
- `quote(id: ID!)` — Retrieve a quote by ID
- `quotes(filter: QuoteFilter)` — List quotes
- `application(id: ID!)` — Retrieve an application by ID
- `applications(filter: ApplicationFilter)` — List applications
- `claim(id: ID!)` — Retrieve a claim by ID
- `claims(filter: ClaimFilter)` — List claims
- `cve(cveId: String!)` — Retrieve CVE details and ESS scoring
- `cves(filter: CVEFilter)` — List CVEs with scoring
- `insurer(id: ID!)` — Retrieve insurer details
- `webhook(id: ID!)` — Retrieve webhook configuration
- `webhooks` — List all webhook configurations

### Mutation

- `createApplication(input: ApplicationInput!)` — Start a new insurance application
- `submitApplication(id: ID!)` — Submit an application for underwriting
- `createQuote(applicationId: ID!)` — Generate a quote from a submitted application
- `bindPolicy(input: BindRequest!)` — Bind a quoted policy
- `updatePolicy(id: ID!, input: PolicyInput!)` — Update policy details
- `cancelPolicy(id: ID!, reason: String!)` — Cancel an active policy
- `createEndorsement(policyId: ID!, input: EndorsementInput!)` — Add an endorsement
- `initiateRenewal(policyId: ID!)` — Begin a renewal for an expiring policy
- `fileClaim(input: ClaimInput!)` — File a new claim
- `updateClaim(id: ID!, input: ClaimUpdateInput!)` — Update claim details
- `createWebhook(input: WebhookInput!)` — Register a webhook endpoint
- `deleteWebhook(id: ID!)` — Remove a webhook registration
- `generateAPIKey(input: APIKeyInput!)` — Generate a new API key
- `revokeAPIKey(id: ID!)` — Revoke an API key

## Named Types

### Policy Types

- `Policy` — Top-level policy record with all metadata, coverage details, and lifecycle status
- `PolicyDetails` — Extended policy information including terms, conditions, and endorsements
- `PolicyType` — Enum of policy product lines (CYBER, TECH_EO, EXEC_RISKS, MPL, AI_COVERAGE)
- `PolicyStatus` — Enum of policy states (QUOTED, BOUND, ACTIVE, CANCELLED, EXPIRED, RENEWED)
- `CyberPolicy` — Cyber-specific policy fields including breach response, network security, media liability
- `TechPolicy` — Technology E&O specific fields covering professional services, tech products

### Quote Types

- `Quote` — Quote record with pricing, coverage, and expiry metadata
- `QuoteDetails` — Detailed quote breakdown including per-coverage premiums, sublimits, retentions
- `QuoteStatus` — Enum (PENDING, ISSUED, ACCEPTED, DECLINED, EXPIRED, BOUND)
- `QuoteExpiry` — Expiry date and countdown for a quote

### Bind Types

- `BindDetails` — Record of a bind transaction including effective date, documents, and signatures
- `BindRequest` — Input for initiating a policy bind

### Coverage Types

- `Coverage` — A coverage component within a policy or quote
- `CoverageDetails` — Full description, terms, and conditions for a coverage
- `CoverageLimit` — Occurrence and aggregate limit for a coverage
- `Sublimit` — Sub-limit within a coverage (e.g., social engineering, ransomware)
- `Deductible` — Deductible amount and applicable conditions
- `Retention` — Self-insured retention amount
- `TechLimit` — Technology-specific limit fields for Tech E&O policies

### Application Types

- `Application` — Insurance application record capturing business and risk data
- `ApplicationDetails` — Full application data including all question responses and attachments
- `SecurityQuestion` — A security-related application question (e.g., MFA, EDR, backups)
- `SecurityAnswer` — An applicant's answer to a security question with evidence notes

### Assessment Types

- `Assessment` — Risk assessment report generated from application data and external signals
- `AssessmentDetails` — Full assessment including risk drivers, scan results, and recommendations
- `RiskScore` — Numeric risk score with band classification and contributing factors
- `SecurityRating` — Letter or numeric security posture rating

### Tech Stack & Business Types

- `TechStack` — Technology inventory declared by the insured (cloud, OS, security tools)
- `EmployeeCount` — Employee headcount band for underwriting classification
- `Revenue` — Annual revenue figure with currency
- `CloudProvider` — Cloud infrastructure provider (AWS, Azure, GCP, etc.)
- `DomainDetails` — Internet-facing domain metadata used in attack-surface scanning
- `VulnerabilityScan` — External vulnerability scan result tied to insured domains
- `ExposureDetails` — Exposed service or port details from attack-surface monitoring

### Insured & Business Types

- `InsuredDetails` — The insured entity profile with contact and business metadata
- `Business` — Business entity record with legal name, DBA, incorporation state
- `BusinessType` — Enum of entity types (LLC, CORP, PARTNERSHIP, SOLE_PROP, NON_PROFIT)
- `Naics` — NAICS industry classification code and description
- `Address` — Mailing or physical address
- `Contact` — Named contact with role, phone, and email

### Insurer Types

- `Insurer` — Capacity provider (Allianz, Arch, Ascot, Zurich, Swiss Re, Lloyd's syndicate)

### Document Types

- `PolicyDocument` — A policy document artifact (PDF, declaration page, specimen)
- `Certificate` — Certificate of insurance
- `Endorsement` — Policy endorsement adding, removing, or modifying coverage terms

### Lifecycle Types

- `Renewal` — Renewal record linking expiring policy to renewal quote and new policy
- `Premium` — Total premium amount with payment schedule
- `PremiumDetails` — Per-coverage premium breakdown with taxes and fees

### Claim Types

- `Claim` — A claim filed against a policy
- `ClaimDetails` — Full claim record with incident details, reserves, payments, status
- `ClaimType` — Enum (BREACH, RANSOMWARE, FRAUD, BEC, PRIVACY, NETWORK_OUTAGE, MEDIA, OTHER)
- `ClaimStatus` — Enum (REPORTED, UNDER_REVIEW, INVESTIGATION, SETTLED, CLOSED, DENIED)
- `Incident` — Underlying incident record for a claim
- `IncidentDetails` — Full incident description including timeline, affected systems, attacker TTPs

### Auth & Integration Types

- `APIKey` — API key credential for partner integrations
- `Token` — Short-lived bearer token for API authentication
- `Webhook` — Registered webhook endpoint with event subscription configuration

### CVE / ESS Types (ESS API)

- `CVE` — CVE record with identifiers, description, publication date, and scores
- `CVEScores` — Aggregated ESS, EPSS, and CVSS scores for a CVE
- `ESSScore` — Coalition Exploit Scoring System score and severity band
- `ESSHistory` — Time-series of ESS score changes for a CVE
- `EPSSScore` — Exploit Prediction Scoring System probability score
- `CVSSScore` — CVSS v2/v3 base score and vector string
- `ExploitReference` — A public exploit reference (ExploitDB entry, Metasploit module)
- `GitHubRepo` — GitHub repository mentioning or implementing a CVE exploit
- `TwitterMention` — Tweet referencing a CVE with timestamp and engagement metrics

## Connections and Pagination

All list fields use cursor-based pagination via a `Connection` pattern:

- `edges` — Array of edge objects containing `node` and `cursor`
- `pageInfo` — `hasNextPage`, `hasPreviousPage`, `startCursor`, `endCursor`
- `totalCount` — Total number of matching records

## Enums Summary

| Enum | Values |
|---|---|
| PolicyType | CYBER, TECH_EO, EXEC_RISKS, MPL, AI_COVERAGE, CRIME, DO, EPL, FIDUCIARY |
| PolicyStatus | QUOTED, BOUND, ACTIVE, CANCELLED, EXPIRED, RENEWED, PENDING |
| QuoteStatus | PENDING, ISSUED, ACCEPTED, DECLINED, EXPIRED, BOUND |
| ClaimType | BREACH, RANSOMWARE, FRAUD, BEC, PRIVACY, NETWORK_OUTAGE, MEDIA, OTHER |
| ClaimStatus | REPORTED, UNDER_REVIEW, INVESTIGATION, SETTLED, CLOSED, DENIED |
| BusinessType | LLC, CORP, PARTNERSHIP, SOLE_PROP, NON_PROFIT, TRUST |
| CloudProvider | AWS, AZURE, GCP, IBM_CLOUD, ORACLE_CLOUD, ON_PREMISES, HYBRID, OTHER |

## Notes

- The Coalition Active Insurance API is partner-gated; no public OpenAPI spec is published. This schema is conceptual and derived from public documentation and product descriptions.
- The ESS API is fully public with an OpenAPI 3.1 spec at https://ess-api.coalitioninc.com/openapi.json.
- Coverage for Executive Risks products (D&O, EPL, Fiduciary, Crime) follows the same Policy/Quote/Bind lifecycle but uses product-specific application questions and coverage fields.
- Webhook events are delivered as signed JSON payloads; the `Webhook` type captures endpoint URL, secret, and subscribed event types.
