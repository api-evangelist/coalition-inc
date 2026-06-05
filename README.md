# Coalition (coalition-inc)

Coalition is a San Francisco–headquartered cyber insurance and active risk management provider founded in 2017 by Joshua Motta (CEO) and John Hering. Coalition pairs commercial insurance lines — Cyber, Technology Errors & Omissions, Executive Risks (D&O, EPL, Fiduciary, Crime), Miscellaneous Professional Liability, and AI coverage — with a continuous attack-surface monitoring and incident-response platform (Coalition Control, Wirespeed ADR, Coalition Incident Response, Security Awareness Training). The company's underwriting engine is exposed to brokers and distribution partners through the Coalition Active Insurance API, a RESTful surface that supports rate, quote, bind, document generation, renewals, and webhook events across the United States and Canada, with executive risks APIs and additional product lines added over time. Coalition also publishes a public Exploit Scoring System (ESS) API at ess-api.coalitioninc.com that exposes CVE detail, ESS/EPSS/CVSS scoring, exploit references (ExploitDB, Metasploit), GitHub repository signals, and Twitter mention timelines for over 200,000 vulnerabilities. Coalition is backed by Allianz X, Valor Equity Partners, Ribbit Capital, Mitsui Sumitomo, Kinetic Partners and other strategic insurers (Allianz, Arch, Ascot, Zurich, Swiss Re, Lloyd's syndicates); it raised a $250M Series F in 2022 at a $5B valuation. The Active Insurance API is partner-gated (no public OpenAPI), but the ESS API is fully public with OpenAPI 3.1, an interactive docs UI, and ReDoc.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/coalition-inc/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/coalition-inc/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Provider
- **Access:** 3rd-Party

## Tags

- Cyber Insurance
- Insurance
- Insurtech
- Risk Management
- Cybersecurity
- Vulnerability Management
- CVE
- Exploit Scoring
- Threat Intelligence
- Incident Response
- Attack Surface Management
- Brokers
- MGA
- Executive Risks
- Technology E&O
- Active Insurance

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### Coalition Exploit Scoring System (ESS) API

Public REST API exposing Coalition's machine-learning Exploit Scoring System over more than 200,000 CVEs. Returns vulnerability detail, ESS / EPSS / CVSS score summaries, ESS shift history, public exploit references (ExploitDB, Metasploit), GitHub repository mentions and keyword extraction, and Twitter mention timelines. Useful for vulnerability triage, prioritization, and threat-intel enrichment.

- **Human URL:** [https://ess.coalitioninc.com](https://ess.coalitioninc.com)
- **Base URL:** `https://ess-api.coalitioninc.com`

#### Tags

- CVE
- Vulnerability
- Exploit Scoring
- Threat Intelligence
- Cybersecurity

#### Properties

- [Documentation](https://ess-api.coalitioninc.com/docs)
- [Re Doc](https://ess-api.coalitioninc.com/redoc)
- [OpenAPI](https://ess-api.coalitioninc.com/openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Local Open A P I](openapi/coalition-ess-openapi.yml)
- [Console](https://ess.coalitioninc.com/explore/)
- [Spectral Rules](rules/coalition-ess-rules.yml)
- [JSON Schema](json-schema/coalition-ess-cve-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/coalition-ess-cve-structure.json)
- [Example](examples/coalition-ess-listCves-example.json)
- [Example](examples/coalition-ess-getCve-example.json)
- [Example](examples/coalition-ess-getEssHistory-example.json)
- [Example](examples/coalition-ess-listGithubRepos-example.json)
- [Postman Collection](collections/coalition-ess.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/coalition-ess.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Coalition Active Insurance API

Partner-gated REST API that brokers and distribution partners use to rate, quote, bind, generate documents (quote PDF, Coalition Risk Assessment, signature bundle, specimen policy), and manage renewals for Coalition's commercial insurance lines — Cyber, Technology E&O, Executive Risks (D&O, EPL, Fiduciary, Crime), Miscellaneous Professional Liability, and AI coverage. Supports webhook events and ships with a sandbox environment, dedicated implementation manager, and QA test plans. Coverage spans the United States and Canada, with a 99.9% uptime SLA and sub-2-second quote response target. Documentation is provisioned to vetted partners; no public OpenAPI is published.

- **Human URL:** [https://www.coalitioninc.com/brokers/api](https://www.coalitioninc.com/brokers/api)

#### Tags

- Cyber Insurance
- Quote
- Bind
- Policy
- Brokers
- Webhooks

#### Properties

- [Sign Up](https://web.coalitioninc.com/partnership.html)
- [Overview](https://www.coalitioninc.com/brokers/api)
- [Broker Portal](https://www.coalitioninc.com/brokers/broker-iq)
- [Blog](https://www.coalitioninc.com/blog/coalition-apis-helping-power-the-future-of-insurance-distribution)
- [Announcement](https://www.coalitioninc.com/announcements/coalition-launches-new-API-solution-for-streamlined-partner-integration)
- [Announcement](https://www.coalitioninc.com/announcements/coalition-introduces-new-apis-to-power-executive-risks-insurance)
- [Postman Collection](collections/coalition-ess.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/coalition-ess.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Website](https://www.coalitioninc.com)
- [About](https://www.coalitioninc.com/about)
- [Products](https://www.coalitioninc.com/cyber-insurance)
- [Control](https://www.coalitioninc.com/control)
- [Security](https://www.coalitioninc.com/security)
- [Exploit Scoring System](https://ess.coalitioninc.com)
- [Broker I Q](https://www.coalitioninc.com/brokers/broker-iq)
- [A P I](https://www.coalitioninc.com/brokers/api)
- [Partners](https://www.coalitioninc.com/serviceproviders)
- [Partnership](https://web.coalitioninc.com/partnership.html)
- [Newsroom](https://www.coalitioninc.com/newsroom)
- [Announcements](https://www.coalitioninc.com/announcements)
- [Blog](https://www.coalitioninc.com/blog)
- [Knowledge Center](https://www.coalitioninc.com/knowledge-center)
- [Help Center](https://help.coalitioninc.com)
- [Careers](https://www.coalitioninc.com/careers)
- [Contact](https://www.coalitioninc.com/contact)
- [LinkedIn](https://www.linkedin.com/company/coalitioninc)
- [Twitter](https://twitter.com/SolveCyberRisk)
- [YouTube](https://www.youtube.com/channel/UCoc7ed_HZrl-Ln4ZCnDsuZA)
- [Facebook](https://www.facebook.com/coalitioninc)
- [Instagram](https://www.instagram.com/coalitioninc)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
