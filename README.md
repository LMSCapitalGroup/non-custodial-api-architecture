LMSCapitalGroup — Non-Custodial FinTech SaaS & API Routing Architecture

**Entity Classification:** B2B Financial Technology & Telemetry Software (Non-Custodial SaaS)  
**Primary Contact:** `support@lmscapitalgroup.net`

---

## 1. Architectural Overview: Control Plane vs. Custody & Clearing Plane

**LMSCapitalGroup** is an international B2B software-as-a-service (SaaS) and API orchestration layer engineered to eliminate multi-terminal data fragmentation for investment teams, family offices, and systematic traders.

By architectural design, **LMSCapitalGroup enforces a strict boundary between analytical software telemetry and financial custody**:
* **Zero Capital Custody:** The software layer does not accept cash deposits, hold client trading balances, or manage pooled custodial accounts.
* **Regulated Terminal Execution:** Users connect their own accounts at licensed third-party brokers (**MetaTrader 5**, **WebTrader**) via scoped, non-custodial API credentials.
* **Regulated PSP/EMI Clearing:** Payment clearing and settlement instructions are routed via encrypted APIs exclusively to licensed external **Payment Service Providers (PSPs)** and **Electronic Money Institutions (EMIs)**.

### API Routing & Settlement Schema

```text
+-----------------------------------------------------------------------------------+
|                        USER WORKSPACE (Human-in-the-Loop)                         |
|   [ Manual Trade Approval ]        [ Settlement / Routing Instruction ]           |
+---------------+--------------------------------------------+----------------------+
                |                                            |
                v (Signed UI/API Action)                     v (Signed UI/API Action)
+-----------------------------------------------------------------------------------+
|                LMSCAPITALGROUP SAAS LAYER (Non-Custodial Control Plane)           |
|                                                                                   |
|  +-------------------------+    +----------------------------------------------+  |
|  |     Integration Hub     |    |              Compliance Copilot              |  |
|  | (Telemetry & Key Vault) |    | (Automated KYC/AML & Risk Boundary Audit)    |  |
|  +------------+------------+    +----------------------+-----------------------+  |
|               |                                        |                          |
+---------------|----------------------------------------|--------------------------+
                |                                        |
   [ Non-Custodial API Keys ]               [ Encrypted API Payload ]
   (Trade/Read Scope ONLY;                  (No Developer Account Sweep;
    Withdrawal Scope = FALSE)                1–3 Business Day SLA Window)
                |                                        |
                v                                        v
+-------------------------------+        +------------------------------------------+
| REGULATED THIRD-PARTY BROKERS |        | REGULATED PSP / LICENSED EMI GATEWAYS    |
|  (MetaTrader 5 / WebTrader)   |        | (Payment Service Providers & Clearing)   |
|                               |        |                                          |
| • Holds Client Trading Margin |        | • Executes Fiat / Digital Asset Rails    |
| • Executes Order Book Routing |        | • Performs Interbank / SEPA / SWIFT      |
| • Custodies Account Equity    |        | • Enforces Financial Regulatory Custody  |
+-------------------------------+        +------------------------------------------+
