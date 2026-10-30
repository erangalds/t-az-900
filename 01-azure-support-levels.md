# Azure Support Plans (Including Premier / Unified)

Microsoft Azure support options span four direct-subscription tiers (**Basic**, **Developer**, **Standard**, and **Professional Direct**) and an overarching enterprise contract tier (**Premier / Microsoft Unified Support**).

---

### Why "Premier" (or "Premium") Was Not in the Standalone List

1. **Naming Confusion ("Premium" vs. "Premier"):** Azure has never offered a plan named *"Premium Support."* The legacy enterprise tier was officially called **Microsoft Premier Support**.
2. **Retirement / Replacement:** Microsoft retired **Premier Support** and migrated its commercial enterprise contracts to **Microsoft Unified Support**.
3. **Standalone vs. Organization-Wide Agreement:** Unlike Developer, Standard, and Professional Direct (which can be purchased directly per Azure subscription through the Azure Portal credit card or Enterprise Agreement enrollment), **Premier / Unified** is not a standalone Azure plan. It is a comprehensive, company-wide contractual agreement covering the entire Microsoft ecosystem (Azure, Microsoft 365, Windows Server, Dynamics 365, etc.) with a dedicated Customer Success Account Manager (CSAM).

However, **older practice question pools (including CertylQ and ExamTopics) still feature "Premier" heavily**, making it essential to include alongside the modern standalone tiers.

---

### Support Tiers & Key Features

| Support Plan | Target Audience | Technical Support Access | Architecture & Advisory Support | Key Features Included |
| --- | --- | --- | --- | --- |
| **Basic** | All Azure accounts (Free/Default) | **None** (Billing & subscription management only) | None | 24/7 self-help documentation, Azure Advisor recommendations, Service Health dashboard, and Microsoft Q&A forum access. |
| **Developer** | Non-production / trial environments | Business hours only (Email/portal submission) | General guidance based on best practices | Unlimited break-fix support tickets, access to Azure Advisor, prioritized responses on Microsoft Q&A. |
| **Standard** | Production workload environments | **24x7** access via phone and email | General architectural guidance | Unlimited break-fix tickets, third-party software troubleshooting support, high-severity escalation routing. |
| **Professional Direct (ProDirect)** | Business-critical workloads | **24x7** access via phone and email | Architectural guidance from a dedicated pool of **ProDirect Delivery Managers** | Proactive guidance, onboarding seminars, service reviews, incident escalation management, and access to Support APIs. |
| **Premier / Unified Support** | Enterprise-wide multi-product deployments | **24x7** access with dedicated escalation specialists | Comprehensive end-to-end architecture reviews & designated Technical Account Manager (TAM) / CSAM | Organization-wide coverage (Azure, M365, Dynamics, On-Premises), proactive risk assessments, on-demand training labs, and rapid response options. |

---

### Service Level Agreements (Initial Response Times by Severity)

Azure classifies technical issues across three primary severity levels:

* **Severity A:** Critical business impact (complete outage / severe loss of service)
* **Severity B:** Moderate business impact (work impaired, but operations continue)
* **Severity C:** Minimal business impact (minor inquiry / minor impediment)

| Plan | Severity A (Critical) | Severity B (Moderate) | Severity C (Minimal) |
| --- | --- | --- | --- |
| **Basic** | N/A (No technical support) | N/A | N/A |
| **Developer** | Not Available (Sev A not supported) | Not Available (Sev B not supported) | **< 8 business hours** |
| **Standard** | **< 1 hour** (24/7) | **< 4 hours** | **< 8 business hours** |
| **Professional Direct** | **< 1 hour** (24/7) | **< 2 hours** | **< 4 business hours** |
| **Premier / Unified** | **< 1 hour** (or **< 15 minutes** with Rapid Response add-on) | **< 2 hours** | **< 4 hours** |

---

### Core Distinctions for Azure Certifications (AZ-900 / PL-900)

* **Free for Everyone:** Billing, quota management, and subscription support are available 24x7 to **all** plans, including **Basic**, at no cost.
* **First Tier with 24x7 Technical Support:** **Standard** (Developer is strictly business hours).
* **First Tier Supporting Severity A Incidents:** **Standard** (Developer allows only Severity C).
* **Named Delivery Manager Pool:** **Professional Direct** (provides access to ProDirect Delivery Managers, but not a dedicated personal account manager).
* **Dedicated Account Representative (TAM / CSAM):** Exclusive to **Premier / Unified Support**.
* **Legacy "Premier" in Practice Exams:** Whenever a question asks *"Which plans allow you to open technical support requests?"*, both **Premier** and the paid standalone tiers (**Developer, Standard, Professional Direct**) are correct; only **Basic** is excluded.