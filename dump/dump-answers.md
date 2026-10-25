# AZ 900 - Azure Fundamentals

## Q1

![Q1](/dump/question-images/q1-50/q1.png)


### Answer 

The support plans that should be dragged to the **Answer** area are:

* **Developer**
* **Standard**
* **Professional Direct**
* **Premier** (Unified)

---

### Explanation

In Microsoft Azure, the ability to open technical support tickets depends on the subscription tier:

* **Basic Plan (Excluded):** The Basic plan is included for all Azure customers at no cost, but it **does not allow opening technical support requests**. It only provides access to billing, subscription management, quota increase requests, documentation, and Azure Community Support forums.
* **Developer, Standard, Professional Direct, and Premier (Included):** All paid Azure support tiers grant access to submit one-on-one **technical support cases** (break-fix requests) through the Azure portal:
* **Developer:** Business hours access for non-production environments.
* **Standard:** $24/7$ technical support access for production workloads.
* **Professional Direct:** $24/7$ access with faster response times, architectural guidance, and dedicated support engineering.
* **Premier / Unified:** Enterprise-wide technical support with designated account managers and the fastest SLA response times.

## Q2

![Q2](/dump/question-images/q1-50/q2.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** A company has datacenters in Los Angeles and New York configured as geo-clustered sites for site resiliency and needs an Azure storage redundancy option.


* **Requirements:**
* Data must be stored on multiple nodes.


* Data must be stored on nodes in separate geographic locations.


* Data can be read from the secondary location as well as from the primary location.




* **Options:**
* A. Geo-redundant storage


* B. Read-only geo-redundant storage


* C. Zone-redundant storage


* D. Locally redundant storage





---

### 2. Correct Answer

* **B. Read-only geo-redundant storage (RA-GRS)**

---

### 3. Verification of Visible Selection / Community Key

* *(Skipped: No answer selection or community key is highlighted or marked in the screenshot.)*

---

### 4. Official Microsoft Justification

* **Storage Redundancy & Secondary Read Access:**
* **GRS (Geo-redundant storage)** replicates data synchronously three times within a single physical location in the primary region using LRS, then replicates asynchronously to a single physical location in the secondary paired region (providing six total copies across two regions). However, with standard GRS, data in the secondary region is not accessible for read operations unless Microsoft initiates a failover or customer-managed failover is triggered.
* **RA-GRS (Read-access geo-redundant storage)** provides the exact same geographic replication as GRS, but additionally exposes a secondary read-only endpoint (e.g., `<accountname>-secondary.blob.core.windows.net`), enabling applications to read data directly from the secondary geographic location at any time.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **A. Geo-redundant storage (GRS):** While it replicates data to a separate geographic region, the secondary region is strictly passive/standby and cannot be read from unless a failover occurs.
* **C. Zone-redundant storage (ZRS):** Replicates data synchronously across three Azure availability zones within the primary region only. It does not provide redundancy across separate geographic regions (paired regions), nor does it satisfy the cross-region read requirement.
* **D. Locally redundant storage (LRS):** Replicates data three times within a single data center in the primary region. It provides no protection against regional outages or data access from a secondary geographic location.

---

### 6. Exam Keyword / Trap Alert

* **The "Read from Secondary" Trigger:** Whenever an AZ-900 question requires geo-replication and explicitly specifies that data must be readable or accessible from the secondary region without initiating a failover, look directly for **RA-GRS** (or **RA-GZRS**). Standard GRS is the primary distractor designed to catch candidates who overlook the read-access requirement.

