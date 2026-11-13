# Security & Non-Custodial Governance Policy — LMSCapitalGroup

## Zero-Custody Security Boundary
**LMSCapitalGroup**  operates strictly as a non-custodial SaaS telemetry and API workflow provider. The platform architecture enforces three hard security controls:

1. **Scoped Non-Custodial Credentials:** Integrations with external brokerage terminals (**MetaTrader 5**, **WebTrader**) reject API tokens with withdrawal or account-sweep privileges.
2. **External PSP/EMI Settlement Isolation:** All fiat and digital asset payment clearing flows are routed via encrypted APIs directly to accredited third-party **Payment Service Providers (PSPs)** and **Electronic Money Institutions (EMIs)**.
3. **Human-in-the-Loop (HITL) Authorization:** Quantitative modules (*Portfolio Intelligence Engine*, *Market Signal Engine*) generate analytical telemetry only; 100% of trade executions and settlement routings require explicit manual confirmation by the human operator.

## Encryption & Auditability
* **Data Protection:** AES-256-GCM encryption at rest and TLS 1.3 in transit across all API gateways.
* **Compliance Screening:** Automated Tier-1/Tier-2 KYC/AML and sanctions checks are administered via *Compliance Copilot* within a **1 to 3 business day SLA window**.

## Security Disclosures
For infrastructure security inquiries or API vulnerability reports, contact: `support@lmscapitalgroup.com`.
