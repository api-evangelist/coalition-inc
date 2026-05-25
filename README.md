# coalition-inc

[Coalition](https://www.coalitioninc.com) — cyber insurance and active risk management. Founded 2017 in San Francisco by Joshua Motta (CEO) and John Hering. Operates across the US, Canada, UK, and Europe.

Coalition pairs commercial insurance lines (Cyber, Tech E&O, Executive Risks, MPL, AI Coverage) with an attack-surface monitoring and incident-response platform (Coalition Control, Wirespeed ADR, Coalition Incident Response).

## APIs

| API | Access | Surface |
|---|---|---|
| [Coalition Exploit Scoring System (ESS)](https://ess-api.coalitioninc.com/docs) | Public | 7 read-only endpoints over 200,000+ CVEs with ESS / EPSS / CVSS scoring, exploit references (ExploitDB, Metasploit), GitHub repo signals, and Twitter mentions. |
| [Coalition Active Insurance API](https://www.coalitioninc.com/brokers/api) | Partner | Rate, quote, bind, renew, generate documents, and consume webhooks for Coalition's commercial lines across US and Canada. No public OpenAPI. |

## Artifacts

- `apis.yml` — provider profile (APIs.json)
- `openapi/coalition-ess-openapi.yml` — Coalition ESS OpenAPI 3.1
- `rules/coalition-ess-rules.yml` — Spectral ruleset for ESS conventions
- `capabilities/exploit-scoring.yaml` — Naftiko capability composing the seven ESS operations
- `json-schema/coalition-ess-cve-schema.json` — JSON Schema for the ESS CVE record
- `json-structure/coalition-ess-cve-structure.json` — Field-level structure documentation
- `json-ld/coalition-inc-context.jsonld` — JSON-LD context aligning ESS terms with schema.org
- `examples/` — Request/response examples for list, detail, history, and GitHub-repo operations
- `vocabulary/coalition-inc-vocabulary.yml` — Domain vocabulary
- `plans/coalition-inc-plans-pricing.yml` — Access tiers (API Commons Plans 0.1)
- `rate-limits/coalition-inc-rate-limits.yml` — Rate-limit posture (API Commons Rate Limits 0.1)
- `finops/coalition-inc-finops.yml` — FinOps / FOCUS mapping
- `review.yml` — APIs.json lint review
