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



## Q3

![Q3](/dump/question-images/q1-50/q3.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** A company has an Azure subscription with a **Basic** support plan. They want to request an assessment of their Azure environment's architecture/design from Microsoft, which is not included in the current plan. The goal is to upgrade to a support plan that provides this functionality while **minimizing costs**.


* **Proposed Solution:** Recommend subscribing to the **Professional Direct** support plan.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **A. Yes**

---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Incorrect.**


* The dump marks **B (No)**, which is incorrect because **Professional Direct** is the lowest-tier (and least expensive) support plan that provides architectural guidance and environment design reviews by Microsoft experts.



---

### 4. Official Microsoft Justification

* **Concept:** Azure Support Plans hierarchy and consultative architectural guidance.
* Under official Microsoft Support tier definitions:
* **Basic:** Billing and subscription management support only; zero technical or architectural guidance.
* **Developer:** Basic technical support during business hours; no architectural reviews.
* **Standard:** 24/7 technical support for minimal/moderate business impact; general how-to guidance only, no dedicated architectural design assessments.
* **Professional Direct (ProDirect):** Adds access to **Architectural Guidance** delivered by Azure specialist teams (e.g., design assessments, best practices reviews based on the Azure Well-Architected Framework), pooled delivery managers, and operational support.
* **Enterprise (Unified / Premier):** Offers full end-to-end designated Technical Account Managers and custom architectural assessments, but at an enterprise-scale cost.


* Since **Professional Direct** is the lowest-cost tier that unlocks architectural and design reviews from Microsoft, the proposed solution meets the requirement while keeping expenses to a minimum.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option B (No):** Incorrect. Rejecting Professional Direct would imply that either a cheaper plan supports architectural reviews (false—Developer and Standard do not) or that an Enterprise plan is required (false—ProDirect includes architectural guidance and design review consultations at a fraction of the Unified/Enterprise cost).



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for the phrase **"assessment of an Azure environment's design"** or **"architectural guidance"** combined with **"minimize costs."**


* **Rule of Thumb:**
* *Standard* = Break-fix technical support only (24/7).
* *Professional Direct* = Break-fix technical support + **Architectural guidance / consultative reviews** (the lowest tier that offers this).


## Q4

![Q4](/dump/question-images/q1-50/q4.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** You are tasked with deploying Azure virtual machines for your company and need to make use of the appropriate cloud service/deployment solution.


* **Proposed Solution:** You should make use of Software as a Service (SaaS).


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Correct.**


* The visible answer is accurate because Azure Virtual Machines are an Infrastructure as a Service (IaaS) offering, not Software as a Service (SaaS).



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Service Models (IaaS vs. PaaS vs. SaaS) and the Shared Responsibility Model.
* Under official Microsoft Learn definitions:
* **Infrastructure as a Service (IaaS):** The most flexible category of cloud services, providing maximum control over hardware resources. The cloud vendor manages the physical infrastructure, while the customer configures, manages, and updates the operating system, middleware, and installed applications. **Azure Virtual Machines (VMs)** are the quintessential example of **IaaS**.
* **Software as a Service (SaaS):** Fully managed, centrally hosted end-user software applications (e.g., Microsoft 365, OneDrive, Dynamics 365) where the provider manages everything from physical hardware up through the operating system, runtime, and application code. End users simply consume the software; you cannot deploy or configure virtual machines under SaaS.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Deploying virtual machines requires operating system control, virtual networking configuration, and storage disk management, which fall squarely into **Infrastructure as a Service (IaaS)**, not SaaS.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Whenever you see **"deploying virtual machines"** or **"migrating physical servers with OS control,"** the required cloud service model is always **IaaS (Infrastructure as a Service)**.


* **Quick Reference for AZ-900:**
* *IaaS:* Virtual Machines, Virtual Networks, Azure Disks.
* *PaaS:* Azure App Service, Azure SQL Database, Azure Functions.
* *SaaS:* Microsoft 365, Power BI Service, Dynamics 365.


## Q5

![Q5](/dump/question-images/q1-50/q5.png)


### Answer

### 1. Extracted Question Summary

* **Scenario:** You are tasked with deploying Azure virtual machines for your company and need to make use of the appropriate cloud service/deployment solution.


* **Proposed Solution:** You should make use of Platform as a Service (PaaS).


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B: No**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Correct.**


* Azure Virtual Machines fall under the **Infrastructure as a Service (IaaS)** cloud service category, not Platform as a Service (PaaS).



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Service Delivery Models (IaaS vs. PaaS vs. SaaS) and the Shared Responsibility Model.
* Under official Microsoft Learn standards:
* **Infrastructure as a Service (IaaS):** Provides instant computing infrastructure provisioned and managed over the internet. The customer retains control over the operating system, middleware, and runtime, and is responsible for configuring, patching, and maintaining them. **Azure Virtual Machines** are an **IaaS** offering.
* **Platform as a Service (PaaS):** Provides a complete development and deployment environment in the cloud without the need to manage the underlying operating system, server hardware, or virtualization layer (e.g., Azure App Service, Azure SQL Database). Because PaaS abstracts away the operating system and virtual machine layer, deploying a virtual machine is not possible using a PaaS model.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. PaaS solutions abstract the underlying infrastructure (including virtual machines) away from the user, giving you no direct access to or deployment of guest OS virtual machines.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Any question mentioning **"deploying virtual machines"** or **"migrating physical servers to virtual machines"** always points to **IaaS**. If the proposed solution suggests **PaaS** or **SaaS**, the answer is always **No**.


## Q6

![Q6](/dump/question-images/q1-50/q6.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** You are tasked with deploying Azure virtual machines for your company and need to make use of the appropriate cloud deployment solution.


* **Proposed Solution:** You should make use of Infrastructure as a Service (IaaS).


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **A. Yes**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: A): Correct.**


* The highlighted answer **A** is accurate because Azure Virtual Machines are provisioned and operated under the **Infrastructure as a Service (IaaS)** cloud service model.



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Service Delivery Models (IaaS vs. PaaS vs. SaaS) and the Shared Responsibility Model.
* Under official Microsoft Learn architecture standards:
* **Infrastructure as a Service (IaaS):** Delivers scalable compute, storage, and networking resources on demand. In this model, the cloud provider manages the physical data center, virtualization host, and hardware layer, while the customer manages the operating system, middleware, runtime environment, network traffic rules, and installed applications.
* **Azure Virtual Machines (VMs)** represent the baseline compute service for IaaS, giving administrators full root/administrative control over the operating system and software stack.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option B (No):** Incorrect. Choosing "No" would imply that IaaS is the wrong model for deploying virtual machines, whereas IaaS is the exact model designed for hosting and managing virtualized server infrastructure.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** This is the positive match in the recurring 3-part scenario cluster:
* Deploying Virtual Machines $\rightarrow$ **SaaS** = **No** (from Question 4).


* Deploying Virtual Machines $\rightarrow$ **PaaS** = **No** (from Question 5).


* Deploying Virtual Machines $\rightarrow$ **IaaS** = **Yes** (from Question 6).


## Q7

![Q7](/dump/question-images/q1-50/q7.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** Your developers have created 10 web applications that must be hosted on Azure. You need to determine which Azure App Service plan tier to host the web apps based on the following requirements:


* Must support **custom domains**.


* Each app requires **10 GB of storage** (total storage needs: 10 apps $\times$ 10 GB = 100 GB).


* Must run on **dedicated compute instances**.


* **Load balancing between instances** must be included (requires auto-scaling / multi-instance scale-out).


* **Costs must be minimized**.




* **Options:**
* **A.** Standard


* **B.** Basic


* **C.** Free


* **D.** Shared





---

### 2. Correct Answer

* **A: Standard**



---

### 3. Verification of Visible Selection / Community Key

* *(No answer is selected or marked in the provided screenshot.)*

---

### 4. Official Microsoft Justification

* **Concept:** Azure App Service Plan Pricing Tiers and Feature Matrix.
* Under official Microsoft App Service specifications:
* **Free & Shared Tiers:** Run apps on shared virtual machine infrastructure with other customers (not dedicated compute), have strict memory/compute quotas (1 GB storage max), and do not support scaling or load balancing.
* **Basic Tier:** Runs on dedicated Azure VMs and supports custom domains, but it **does not support auto-scale or traffic routing/load balancing between instances**, and offers a maximum of only **10 GB total storage** per plan (which cannot satisfy 10 web apps needing 10 GB each).
* **Standard Tier:** Runs on dedicated compute instances, supports up to **50 GB** (historically) or **250 GB** total storage across apps, supports custom domains and SSL, and natively includes **scale-out capabilities (up to 10 instances) with integrated Azure load balancing** between instances.


* Therefore, **Standard** is the lowest-cost tier that satisfies both the **multi-instance load balancing** and aggregate storage requirements on dedicated compute.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **B. Basic:** While it provides dedicated compute instances and supports custom domains, it lacks built-in auto-scaling and instance load balancing, and its plan storage limit (10 GB total) cannot support 10 apps requiring 10 GB each.
* **C. Free:** Runs on shared compute instances, caps storage at 1 GB total, does not support custom domains, and has no multi-instance load balancing.
* **D. Shared:** Runs on multi-tenant shared infrastructure (violates the dedicated instance requirement), caps storage at 1 GB total, and cannot scale out with instance load balancing.

---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Look for the combination of **"dedicated compute instances"** and **"load balancing between instances"** / **"auto-scale."**


* **Rule of Thumb:**
* *Basic* = Dedicated VMs, but **manual scale only** (no automated traffic load balancing across multiple instances).
* *Standard* = Minimum tier for **auto-scale, multi-instance load balancing, staging slots, and daily backups**.


Now let's further clarify the ambuiguity **the distinction between an App Service Plan and the Web Apps hosted within it.**

---

### 1. App Service Plan vs. App Service (Web App)

To understand how deployment, routing, and storage work, the foundational Azure concept is:

* **App Service Plan = The VM / Compute Infrastructure:** An App Service Plan (ASP) represents a set of compute resources (CPU, RAM, storage quota, and OS instances) provisioned in Azure. You pay for the **App Service Plan**, not per app.
* **Web App (App Service) = The Application Runtime:** A Web App is simply an execution context running on top of that App Service Plan.
* **1-to-Many Relationship:** You can deploy **multiple distinct web applications** (e.g., App 1 = HR Portal, App 2 = Inventory API, App 3 = Customer Portal) to run simultaneously inside a **single** App Service Plan.

---

### 2. How the 10 Web Apps Are Deployed

Whether you use Basic or Standard, the deployment model inside Azure is identical:

1. **Single App Service Plan:** You provision one App Service Plan in your region.
2. **Ten Web Apps Attached:** You create 10 separate App Services (`app1.azurewebsites.net`, `app2.azurewebsites.net`, etc.) and bind each to that same App Service Plan.
3. **Execution:** All 10 web applications run concurrently on the virtual machine instance(s) allocated to that plan.

---

### 3. How Storage and Code Are Handled

Many assume each app gets its own separate disk drive, but that is not how Azure App Service operates:

* **Shared Storage Volume:** In Azure App Service, the storage quota (e.g., 10 GB on Basic, 50 GB / 250 GB on Standard) belongs to the **entire App Service Plan**, not each individual web app.
* **Underlying File System:** Azure mounts a shared SMB/NFS Azure Storage share (visible inside the runtime as `C:\home` on Windows or `/home` on Linux) to the compute instances.
* **Separation of Code & Data:**
* Each web app is isolated into its own directory under the root:
* App 1: `/home/site/wwwroot/` (App 1's code and local files)
* App 2: `/home/site/wwwroot/` (isolated sandbox for App 2)


* Each app maintains its own runtime boundaries, environment variables, connection strings, and application configuration.
* **Aggregate Storage Limit:** The storage quota applies to the sum of all apps in that plan. If you deploy 10 apps and each app genuinely requires 10 GB of storage as stated in the question:

$$\text{Total Storage Required} = 10 \text{ apps} \times 10 \text{ GB} = 100 \text{ GB}$$


* **Basic Tier:** Hard limit of **10 GB total** across the entire plan. It cannot hold 100 GB of aggregate data.
* **Standard Tier:** Provides up to **50 GB / 250 GB** depending on the generation, accommodating the aggregate footprint.





---

### 4. How Traffic Routing Works: Basic vs. Standard

Azure uses an internal architecture called the **App Service Frontend Load Balancer Layer** (built on Azure ARR / Application Request Routing and reverse proxies).

#### A. Ingress Routing (Host Header Routing)

When a user hits a custom domain (e.g., `api.company.com` or `shop.company.com`):

1. The request hits Azure App Service’s shared frontend fleet.
2. The frontend inspects the HTTP **Host Header** (`Host: shop.company.com`).
3. The frontend looks up which Web App is bound to that custom domain and directs the request to the specific worker process running that application.
*Both Basic and Standard support this ingress custom-domain routing.*

#### B. Multi-Instance Routing & Load Balancing (The Difference)

The crucial difference between Basic and Standard lies in what happens when an App Service Plan scales across **multiple compute instances** (VM instances):

```
                                [ Incoming Requests ]
                                          |
                         +---------------------------------+
                         | App Service Frontend Fleet /    |
                         | Load Balancer (Host Header Map) |
                         +---------------------------------+
                                          |
                 +------------------------+------------------------+
                 |                                                 |
         [ Instance 1 (VM 1) ]                             [ Instance 2 (VM 2) ]
  +-------------------------------+                 +-------------------------------+
  | - App 1 (Proc 101)            |                 | - App 1 (Proc 201)            |
  | - App 2 (Proc 102)            |                 | - App 2 (Proc 202)            |
  | - ...                         |                 | - ...                         |
  | - App 10 (Proc 110)           |                 | - App 10 (Proc 210)           |
  +-------------------------------+                 +-------------------------------+

```

* **Basic Tier (Scale-out without Load Balancing):**
* Basic allows manual scaling up to 3 instances, but it is strictly designed for dev/test and lightweight workloads.
* It **does not support Autoscale**, health-check-driven dynamic load routing, or production-grade load distribution across instances.


* **Standard Tier (Multi-Instance Dynamic Load Balancing):**
* Standard scales out up to 10 dedicated instances.
* When scaled out, **every one of the 10 web apps runs across all active instances** (Worker 1, Worker 2, Worker 3, etc.).
* The App Service Frontend automatically distributes HTTP/HTTPS traffic across these instances using round-robin with ARR cookie affinity (sticky sessions) or health-probe-based distribution.
* Standard includes **Autoscale** (scaling in and out automatically based on metrics like CPU, Memory, or HTTP queue length).



---

### Summary Comparison

| Capability | Basic Tier | Standard Tier | Why It Matters for Question 7 |
| --- | --- | --- | --- |
| **Max Compute Instances** | Up to 3 | Up to 10 | Standard can handle larger multi-app workloads. |
| **Instance Load Balancing / Autoscale** | Manual only; no auto-load balancing rules | **Native dynamic load balancing & Autoscale** | **Fulfills "Load balancing between instances must be included"** |
| **Total Plan Storage** | **10 GB** | **50 GB / 250 GB** | 10 apps needing 10 GB each requires 100 GB total; Basic fails this immediately. |
| **Custom Domains & SSL** | Supported | Supported | Both satisfy this requirement. |



## Q8

![Q8](/dump/question-images/q1-50/q8.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** You are planning to migrate a company to Azure. Each of the company's numerous divisions will have an administrator in place to manage the Azure resources used by their respective division. You need to ensure the deployment allows Azure to be segmented for the divisions while keeping administrative effort to a minimum.


* **Proposed Solution:** You plan to make use of several Azure Active Directory (Azure AD, now Microsoft Entra ID) directories.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Correct.**


* The visible selection **B** is accurate because creating multiple identity tenants introduces significant management overhead rather than minimizing administrative effort.



---

### 4. Official Microsoft Justification

* **Concept:** Microsoft Entra ID (Azure AD) Single-Tenant Architecture vs. Azure Management Hierarchy (Subscriptions / Resource Groups / Azure RBAC).
* Under official Microsoft Cloud Adoption Framework (CAF) and Azure governance standards:
* An organization should maintain a **single Microsoft Entra tenant** to centralize identity management, authentication, conditional access, and licensing.
* Deploying multiple directories/tenants fragments user accounts, necessitates guest accounts or duplicate identities for users who span divisions, complicates single sign-on (SSO), and massively increases administrative overhead.
* To segment access and delegate administrative permissions across divisions with minimal administrative effort, Microsoft recommends using **Azure Role-Based Access Control (Azure RBAC)** scoped at the **Subscription** or **Resource Group** level (or organized under **Management Groups**), all trusted by a single Entra tenant.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Creating multiple directories violates the core requirement of "keeping administrative effort to a minimum". It forces administrators to manage separate identity planes, billing relationships, and access policies independently across each directory.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for questions pairing **"segmented for divisions / departments"** with **"keeping administrative effort to a minimum."**


* **Rule of Thumb:**
* Multiple *Directories / Tenants* = Administrative nightmare (almost always the wrong answer for internal division segmentation).
* Multiple *Subscriptions*, *Resource Groups*, or *Management Groups* under a single tenant = Microsoft best practice for administrative delegation and resource segmentation.


## Q9

![Q9](/dump/question-images/q1-50/q9.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** You plan to host an on-premises portal web app for Miami branch office users on Azure.


* **Requirements:**
* The website will use a custom URL: `miami.weyland.com`.


* The website will be deployed to **two instances**.


* **SSL support** must be included.


* The website **requires 12 GB of storage**.


* **Costs must be minimized**.




* **Question:** Which web tier plan should you use?


* **A.** Standard


* **B.** Basic


* **C.** Free


* **D.** Shared





---

### 2. Correct Answer

* **A: Standard**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: A - Standard): Correct.**


* The highlighted selection **A** is correct because the storage requirement (12 GB) exceeds the maximum disk limit supported by the Basic tier (10 GB).



---

### 4. Official Microsoft Justification

* **Concept:** Azure App Service Plan Pricing Tiers and Resource Quotas.
* Under official Microsoft App Service tier specifications:
* **Free & Shared:** Limited to 1 GB of storage, run on shared multi-tenant infrastructure, and do not support scaling to multiple instances or custom SSL bindings.


* **Basic:** Provides dedicated compute instances and supports manual scaling up to 3 instances, custom domains, and SSL bindings. However, the Basic tier has a hard ceiling of **10 GB storage per App Service Plan**.


* **Standard:** Provides dedicated compute instances, scales up to 10 instances with auto-scaling/load balancing, supports custom domains, custom SSL bindings, and provides **50 GB** (or 250 GB depending on SKU generation) of disk storage.




* Because the workload requires **12 GB of storage**, it cannot fit into the 10 GB storage envelope of the Basic tier. Therefore, **Standard** is the minimum and most cost-effective tier that meets all criteria.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **B. Basic:** Although Basic supports custom domains (`miami.weyland.com`), SSL, and 2 manual instances, its maximum plan storage is capped at **10 GB**, failing the 12 GB storage requirement.


* **C. Free:** Capped at 1 GB storage, does not support custom domains, SSL, or multi-instance scaling.


* **D. Shared:** Capped at 1 GB storage, runs on shared infrastructure, does not support SSL bindings or multi-instance scaling.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for the **storage size** figure in App Service tier questions.


* **Rule of Thumb:**
* If storage is **$\le$ 10 GB** and needs custom domain + SSL on dedicated VMs (without auto-scale), **Basic** is sufficient.
* If storage is **$> 10 GB$** (such as the 12 GB specified here), it automatically eliminates the **Basic** tier and forces an upgrade to **Standard**.



## Q10

![Q10](/dump/question-images/q1-50/q10.png)


### Answer

### 1. Extracted Question Summary

* **Scenario:** Your company plans to migrate all their virtual machines (currently hosted on Hyper-V hosts in an on-premises data center) to an Azure pay-as-you-go subscription. You must ensure the intended Azure solution uses the correct expenditure model.


* **Proposed Solution:** You should recommend the use of the **elastic expenditure model**.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Correct.**


* The visible answer is accurate because "elastic" is a cloud computing architectural characteristic (elasticity), not an accounting/expenditure model recognized in cloud financial management or Microsoft Learn.



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Expenditure Models — Capital Expenditure (CapEx) vs. Operational Expenditure (OpEx).
* Under official Microsoft Learn definitions:
* **Capital Expenditure (CapEx):** The upfront spending of money on physical infrastructure (e.g., buying physical servers, storage arrays, network switches, data center facilities) and deducting that expense on your tax bill over time. The company's on-premises Hyper-V deployment is a typical CapEx model.
* **Operational Expenditure (OpEx):** Spending money on services or products now and being billed for them continuously as they are consumed (pay-as-you-go, subscription pricing, recurring monthly/annual billing) with no upfront hardware purchase.
* An Azure pay-as-you-go subscription operates strictly on the **Operational Expenditure (OpEx)** model.
* **"Elastic"** describes a resource's ability to automatically scale dynamically with demand; it is **not** an expenditure model.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Recommending an "elastic expenditure model" fails because no such accounting or procurement framework exists. Recommending this does not set up or explain the correct financial model (OpEx) for Azure pay-as-you-go services.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch out for questions conflating cloud technical attributes (**Elasticity**, **Scalability**, **Agility**) with financial accounting models (**CapEx** vs. **OpEx**).
* **Rule of Thumb:**
* On-premises data centers / physical server hardware = **CapEx**
* Azure Pay-as-you-go / consumption-based cloud subscriptions = **OpEx**


## Q11

![Q11](/dump/question-images/q1-50/q11.png)

### 1. Extracted Question Summary

* **Scenario:** Your company plans to migrate all their virtual machines (currently hosted on Hyper-V hosts in an on-premises data center) to an Azure pay-as-you-go subscription. You are required to make sure that the intended Azure solution uses the correct expenditure model.


* **Proposed Solution:** You should recommend the use of the **scalable expenditure model**.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Correct.**


* The visible selection **B** is accurate because "scalable" is a technical capability of cloud computing (scalability), not a recognized financial or expenditure model in cloud accounting or Microsoft Learn.



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Financial Models — Capital Expenditure (CapEx) vs. Operational Expenditure (OpEx).
* Under official Microsoft Learn standards:
* **Capital Expenditure (CapEx):** Involves upfront capital investments in physical data center assets (hardware, storage, networking, facilities) that depreciate over time. The on-premises Hyper-V infrastructure represents this model.
* **Operational Expenditure (OpEx):** Involves continuous spending on services and operational consumption (billing based on usage/pay-as-you-go) without upfront infrastructure costs. An Azure pay-as-you-go subscription is strictly classified under the **Operational Expenditure (OpEx)** model.
* **Scalability** defines an architecture's ability to allocate additional resources (vertically or horizontally) to handle growing workloads; it is **not** an expenditure model.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. There is no financial accounting or cloud procurement framework known as a "scalable expenditure model". Recommending this does not meet the goal of applying the proper cloud expenditure model (OpEx) for pay-as-you-go migration.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch out for scenario variants that substitute technical cloud terms (**elastic**, **scalable**, **agile**) into the expenditure model position.


* **Rule of Thumb:**
* Expenditure models in AZ-900 are binary: **CapEx** (on-prem/upfront hardware) vs. **OpEx** (cloud/pay-as-you-go).
* Any solution claiming an "elastic expenditure model" or "scalable expenditure model" is automatically **No**.


## Q12

![Q12](/dump/question-images/q1-50/q12.png)


### 1. Extracted Question Summary

* **Scenario:** Your company plans to migrate all their virtual machines (currently hosted on Hyper-V hosts in an on-premises data center) to an Azure pay-as-you-go subscription. You must ensure the intended Azure solution uses the correct expenditure model.


* **Proposed Solution:** You should recommend the use of the **operational expenditure model**.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **A. Yes**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: A): Correct.**


* The highlighted selection **A** is accurate because an Azure pay-as-you-go subscription is billed on consumption and services used over time, representing an Operational Expenditure (OpEx) model.



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Financial Models — Capital Expenditure (CapEx) vs. Operational Expenditure (OpEx).
* Under official Microsoft Learn standards:
* **Operational Expenditure (OpEx):** Spending money on services or products continuously as they are consumed, with no upfront purchase costs. You pay for computing resources, storage, and networking on an ongoing basis (such as monthly pay-as-you-go billing) and deduct these operational costs within the same tax accounting period.
* **Capital Expenditure (CapEx):** Spending money upfront on physical assets (servers, storage arrays, network switches, cooling, real estate) and amortizing the cost over its useful lifespan.
* Moving from on-premises Hyper-V hosts (CapEx) to an Azure pay-as-you-go subscription transitions IT spending directly into the **Operational Expenditure (OpEx)** model.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option B (No):** Incorrect. Selecting "No" would imply that pay-as-you-go cloud subscriptions do not align with OpEx, whereas OpEx is the standard financial model for public cloud consumption pricing.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** This is the correct, definitive solution to the 3-question CapEx/OpEx question set:
* Pay-as-you-go subscription $\rightarrow$ **Elastic expenditure model** = **No** (from Question 10).


* Pay-as-you-go subscription $\rightarrow$ **Scalable expenditure model** = **No** (from Question 11).


* Pay-as-you-go subscription $\rightarrow$ **Operational expenditure model** = **Yes** (Question 12).





## Q13 
![Q13](/dump/question-images/q1-50/q13.png)


### Answer

### 1. Extracted Question Summary

* **Scenario:** You are required to deploy an Artificial Intelligence (AI) solution in Azure. You want to make sure that you are able to build, test, and deploy predictive analytics for the solution.


* **Proposed Solution:** You should make use of Azure Cosmos DB.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B: No**

---

### 3. Verification of Visible Selection / Community Key

* *(No answer is selected or marked in the provided screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Azure Artificial Intelligence & Machine Learning Services vs. Azure Database Services.
* Under official Microsoft Learn definitions:
* **Azure Machine Learning (Azure ML):** The dedicated cloud service for building, training, evaluating, testing, and deploying machine learning models and predictive analytics solutions at scale.
* **Azure Cosmos DB:** A globally distributed, multi-model NoSQL database service designed for high performance, low latency, and high availability data storage. While Cosmos DB can store data consumed by AI applications, it does not provide tooling or runtimes to build, train, test, or deploy predictive analytics models.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Suggesting Azure Cosmos DB fails to meet the goal because a database engine does not provide machine learning development environments, algorithm libraries, experiment tracking, or predictive model deployment capabilities.

---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Look for the phrase **"build, test, and deploy predictive analytics"** or **"train and deploy AI models."**


* **Rule of Thumb:**
* Build/test/deploy predictive analytics $\rightarrow$ **Azure Machine Learning** (the correct solution).
* Any answer substituting a database (e.g., **Azure Cosmos DB**, **Azure SQL Database**) or compute service (e.g., **Azure App Service**) into this role is always **No**.



## Q14

![Q14](/dump/question-images/q1-50/q14.png)


### Answer

### 1. Extracted Question Summary

* **Scenario:** Your company's Active Directory forest includes thousands of user accounts. All network resources will be migrated to Azure, and thereafter the on-premises data center will be retired. You must employ a strategy that reduces the impact/effect on users once the migration is complete.


* **Proposed Solution:** You plan to sync all the Active Directory user accounts to Azure Active Directory (Azure AD, now Microsoft Entra ID).


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **A. Yes**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: A): Correct.**


* The visible answer is accurate because synchronizing existing on-premises accounts to Microsoft Entra ID (using Microsoft Entra Connect) preserves existing user identities, credentials/passwords, and UPNs, minimizing disruption and user friction during and after the cloud migration.



---

### 4. Official Microsoft Justification

* **Concept:** Hybrid Identity Synchronization and User Experience Preservation.
* Under official Microsoft identity guidelines:
* When migrating enterprise workloads from an on-premises Active Directory Domain Services (AD DS) environment to Azure, synchronizing identities via **Microsoft Entra Connect Sync** (or Cloud Sync) brings existing identities, security groups, and password hashes into the cloud.
* This allows end users to continue logging in using their familiar credentials (Same Sign-On or Seamless Single Sign-On) without needing newly provisioned usernames or password resets.
* Once the on-premises infrastructure is decommissioned, synced identities can be cut over to cloud-managed identities in Microsoft Entra ID without re-creating accounts from scratch.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option B (No):** Incorrect. Rejecting identity synchronization would force administrators either to manually re-create thousands of individual user accounts directly in the cloud or require users to configure new credentials, significantly increasing user disruption and administrative overhead.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Look for the phrase **"Active Directory forest includes thousands of user accounts"** combined with **"reduces the effect / impact on users."**


* **Rule of Thumb:**
* Migrating on-prem AD users to Azure with minimal user friction $\rightarrow$ **Synchronize accounts to Microsoft Entra ID (Azure AD)**.




## Q15

![Q15](/dump/question-images/q1-50/q15.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** You are required to deploy an Artificial Intelligence (AI) solution in Azure. You want to make sure that you are able to build, test, and deploy predictive analytics for the solution.


* **Proposed Solution:** You should make use of Azure Machine Learning Studio.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **A. Yes**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: A - Yes): Correct.**


* The highlighted selection **A** is accurate because Azure Machine Learning Studio is the purpose-built visual and code-based web workspace designed specifically to build, test, train, and deploy predictive models and machine learning pipelines.



---

### 4. Official Microsoft Justification

* **Concept:** Azure Artificial Intelligence & Machine Learning Service Ecosystem.
* Under official Microsoft Learn definitions:
* **Azure Machine Learning Studio:** The integrated web interface for Azure Machine Learning that provides collaborative, low-code/no-code (Automated ML and drag-and-drop Designer) as well as developer/code-first environments (Jupyter notebooks) to build, test, evaluate, track, and deploy predictive analytics solutions and ML models directly as REST endpoints.
* Because it enables end-to-end lifecycle management of predictive analytics—from dataset ingestion and experiment execution to endpoint deployment—the proposed solution satisfies all criteria of the scenario.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option B (No):** Incorrect. Selecting "No" would imply that Azure Machine Learning Studio cannot handle end-to-end predictive analytics workflows, whereas it is the primary Azure tool engineered for this exact purpose.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** This is the positive counterpart to Question 13:


* Predictive analytics solution $\rightarrow$ **Azure Cosmos DB** = **No** (from Question 13).


* Predictive analytics solution $\rightarrow$ **Azure Machine Learning Studio** = **Yes** (Question 15).




* **Rule of Thumb:**
* Whenever an AZ-900 question pairs **"predictive analytics"** with **"build, test, and deploy"**, the matching Azure service is **Azure Machine Learning / Azure Machine Learning Studio**.



## Q16

![Q16](/dump/question-images/q1-50/q16.png)


### Answer

### 1. Extracted Question Summary

* **Scenario:** Your company's infrastructure includes multiple business units that each require a large number of various, identical Azure resources for daily operation. You need to establish a strategy to create these Azure resources automatically.


* **Proposed Solution:** You recommend including the **Azure API Management** service in the strategy.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Correct.**


* Azure API Management is an API gateway and developer portal service, not an automation or Infrastructure-as-Code (IaC) deployment tool.



---

### 4. Official Microsoft Justification

* **Concept:** Azure Resource Automation / Infrastructure as Code (IaC) vs. Application Integration Services.
* Under official Microsoft Learn standards:
* **Azure Resource Manager (ARM) Templates / Azure Bicep:** The native Infrastructure-as-Code (IaC) solution used to define, automate, and repeatedly deploy identical sets of Azure resources consistently across business units, resource groups, or subscriptions.
* **Azure API Management (APIM):** A turnkey hybrid and multi-cloud management platform for publishing, securing, transforming, routing, and analyzing APIs. It does not provision, deploy, or automate Azure infrastructure resources.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Suggesting Azure API Management fails because APIM manages API traffic (gateways, developer portals, rate limiting), having zero functionality for orchestrating or creating baseline Azure resources automatically.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Look for the combination of **"identical resources required by business units"** and **"create Azure resources automatically."**


* **Rule of Thumb:**
* Automated deployment of identical Azure resources $\rightarrow$ **Azure Resource Manager (ARM) templates / Azure Bicep** (or Azure Automation / Management groups / Blueprints).
* Any solution offering application services like **Azure API Management** or **Azure Logic Apps** as the resource-provisioning engine is an automatic **No**.



## Q17

![Q17](/dump/question-images/q1-50/q17.png)



## Q18

![Q18](/dump/question-images/q1-50/q18.png)


## Q19

![Q19](/dump/question-images/q1-50/q19.png)


### 1. Extracted Question Summary

* **Scenario:** You are tasked with deploying a critical line-of-business (LOB) application, which will be installed on a virtual machine, to Azure. The deployment strategy must guarantee an availability of **99.99 percent**. You need to ensure the strategy requires as few virtual machines and availability zones as possible.


* **Proposed Solution:** You include **two virtual machines and one availability zone** in your strategy.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**

---

### 3. Verification of Visible Selection / Community Key

* *(No answer is selected or marked in the provided screenshot.)*

---

### 4. Official Microsoft Justification

* **Concept:** Azure Virtual Machine Service Level Agreements (SLAs) and Resiliency Topologies.
* Under official Microsoft SLA documentation for Virtual Machines:
* **Single Instance VM:** Provides up to **99.9%** SLA (when configured with Premium SSD or Ultra Disk).
* **Availability Sets (2+ VMs):** Provides **99.95%** SLA (protects against local hardware/rack faults and planned updates within a single datacenter).
* **Availability Zones:** To achieve Microsoft's highest SLA of **99.99%**, you must deploy two or more VM instances across **two or more Availability Zones** within the same region.


* Placing two virtual machines in **one availability zone** only protects against faults within the same physical zone if configured in an availability set (which maxes out at **99.95%**). It does not provide datacenter-level fault tolerance and cannot achieve the **99.99%** SLA guarantee.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Restricting deployment to **one availability zone** exposes both VMs to a single datacenter outage (power, water, cooling, or network failure affecting that specific zone), failing to meet the **99.99%** SLA requirement. The minimum viable configuration to achieve 99.99% is **two VMs deployed across two separate Availability Zones**.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Memorize the direct pairing between the VM **SLA percentage** and the required redundancy construct:
* **99.9%** $\rightarrow$ Single VM with Premium SSD.
* **99.95%** $\rightarrow$ $\ge 2$ VMs in an **Availability Set**.
* **99.99%** $\rightarrow$ $\ge 2$ VMs deployed across **$\ge 2$ Availability Zones**.


* If a question asks for **99.99%** and the proposed solution mentions only **one availability zone**, the answer is always **No**.


## Q20

![Q20](/dump/question-images/q1-50/q20.png)


## Q21

![Q21](/dump/question-images/q1-50/q21.png)



## Q22

![Q22](/dump/question-images/q1-50/q22.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** Your company's developers intend to deploy a large number of custom virtual machines on a weekly basis, and then remove them during the same week they are deployed. Sixty percent run Windows Server 2016, and forty percent run Ubuntu Linux. You need to employ a suitable Azure service to minimize the administrative effort required for this repeating lifecycle.


* **Proposed Solution:** You recommend the use of **Microsoft Managed Desktop**.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**

---

### 3. Verification of Visible Selection / Community Key

* *(No answer is selected or marked in the provided screenshot.)*

---

### 4. Official Microsoft Justification

* **Concept:** Developer/Test Lab Automation vs. Managed End-User Device Services.
* Under official Microsoft Learn standards:
* **Azure DevTest Labs:** The purpose-built Azure service designed specifically for developers to quickly self-provision pre-configured Windows and Linux virtual machines using custom images, formulas, and artifacts, with automated shutdown and expiration policies to automatically discard VMs when done.
* **Microsoft Managed Desktop (MMD):** A cloud-based device management service that delivers a managed IT workspace on end-user client devices (Windows Enterprise PCs/laptops) via Microsoft Intune and Microsoft 365. It is not an Azure infrastructure service for provisioning, tearing down, and automating custom server/Linux development VMs.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Microsoft Managed Desktop handles end-user physical endpoint device operations (updates, security monitoring, client OS support), not the dynamic creation and destruction of custom Windows/Linux server test environments.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Whenever you encounter **"deploy a large number of custom virtual machines"** that are **"removed / destroyed weekly"** (or transient test environments for developers) to reduce administrative effort, the required answer is **Azure DevTest Labs**.


* Any solution proposing **Microsoft Managed Desktop**, **Azure Virtual Desktop**, or standard **Azure Policy** for this scenario is **No**.


## Q23 

![Q23](/dump/question-images/q1-50/q23.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** Your company's developers intend to deploy a large number of custom virtual machines on a weekly basis and remove them during the same week they are deployed. 60% run Windows Server 2016, and 40% run Ubuntu Linux. You are required to ensure that the administrative effort needed for this process is reduced by employing a suitable Azure service.


* **Proposed Solution:** You recommend the use of **Azure Reserved Virtual Machines (VM) Instances**.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**

---

### 3. Verification of Visible Selection / Community Key

* *(No answer is selected or marked in the provided screenshot.)*

---

### 4. Official Microsoft Justification

* **Concept:** Billing/Commitment Models vs. Developer Environment Lifecycle Management.
* Under official Microsoft Learn definitions:
* **Azure Reservations (Reserved VM Instances):** A pricing commitment model where you commit to a one-year or three-year plan for compute resources in exchange for significant billing discounts compared to pay-as-you-go rates. Reserved Instances are purely a cost-saving billing mechanism for stable, predictable, long-running production workloads. They do not automate VM provisioning, configuration, or lifecycle de-provisioning.
* **Azure DevTest Labs:** The purpose-built service designed to reduce administrative overhead when provisioning and automatically tearing down transient, short-lived development and testing environments (featuring reusable custom images, artifacts, and auto-shutdown/auto-delete policies).



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Recommending Reserved VM Instances fails on two fronts:
1. It provides zero automation for deploying custom images or deleting them at the end of the week.
2. Committing to a 1-year or 3-year term for transient, short-lived VMs that exist for only a few days each week completely misaligns with cloud cost optimization principles.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch out for the word **"Reserved Instances"** pitched as a solution for provisioning or administrative automation.


* **Rule of Thumb:**
* *Reserved Instances* = Long-term financial billing discount (1-year or 3-year commitment), **not** an operational management tool.
* Short-lived developer VM lifecycle $\rightarrow$ **Azure DevTest Labs**. Any other service proposed for this goal is **No**.


## Q24

![Q24](/dump/question-images/q1-50/q24.png)



## Q25

![Q25](/dump/question-images/q1-50/q25.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** Your company has virtual machines (VMs) hosted in Microsoft Azure, all located in a single virtual network named **VNet1**. The company has users who work remotely, and these remote workers require network access to the VMs in VNet1. You need to provide access for these remote workers.


* **Question:** What should you do?


* **A.** Configure a Site-to-Site (S2S) VPN.


* **B.** Configure a VNet-to-VNet VPN.


* **C.** Configure a Point-to-Site (P2S) VPN.


* **D.** Configure DirectAccess on a Windows Server 2012 server VM.


* **E.** Configure a Multi-Site VPN





---

### 2. Correct Answer

* **C: Configure a Point-to-Site (P2S) VPN.**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: C): Correct.**


* The marked answer **C** is accurate because a Point-to-Site (P2S) VPN connection connects individual client devices (such as remote worker laptops) directly and securely to an Azure Virtual Network over the internet.



---

### 4. Official Microsoft Justification

* **Concept:** Azure Virtual Network Gateway Connectivity Topologies (P2S vs. S2S vs. VNet Peering/VNet-to-VNet).
* Under official Microsoft Learn network architecture standards:
* **Point-to-Site (P2S) VPN:** Enables a secure encrypted tunnel from an **individual client computer** back to an Azure virtual network. It is specifically intended for telecommuters, mobile workers, and remote employees connecting from home or external locations without requiring an on-premises VPN hardware appliance.
* **Site-to-Site (S2S) VPN:** Connects an entire on-premises branch office or corporate data center network to an Azure VNet via an edge VPN gateway device, not individual mobile client endpoints.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **A. Configure a Site-to-Site (S2S) VPN:** Used to connect an entire corporate office/location to Azure; it does not connect roaming/work-from-home remote client PCs directly.


* **B. Configure a VNet-to-VNet VPN:** Connects two Azure virtual networks together; it does not provide connectivity for client user devices.


* **D. Configure DirectAccess on a Windows Server 2012 server VM:** Legacy Windows enterprise technology that requires complex on-premises domain infrastructure, adds management overhead, and Windows Server 2012 is past end-of-life.


* **E. Configure a Multi-Site VPN:** A variation of Site-to-Site VPN connecting multiple physical branch office networks to Azure, not individual remote workers.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Look for **"remote workers"**, **"telecommuters"**, or **"individual client computers connecting from home."**


* **Rule of Thumb:**
* Individual client $\rightarrow$ Azure VNet = **Point-to-Site (P2S)**.


* On-premises office/datacenter $\rightarrow$ Azure VNet = **Site-to-Site (S2S)** or **ExpressRoute**.


* Azure VNet $\rightarrow$ Azure VNet = **VNet Peering** (or VNet-to-VNet VPN).


## Q26

![Q26](/dump/question-images/q1-50/q26.png)

### 1. Extracted Question Summary

* **Scenario:** Your company intends to automate server deployment to Azure. There is concern that administrative credentials could be uncovered during this automated deployment process. You must ensure that administrative credentials are encrypted using a suitable Azure solution during deployment.


* **Proposed Solution:** You recommend the use of **Azure Information Protection**.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Correct.**


* Azure Information Protection (AIP) protects documents and emails (unstructured office data), not infrastructure deployment secrets or administrative credentials.



---

### 4. Official Microsoft Justification

* **Concept:** Secret and Key Management vs. Document/Information Protection.
* Under official Microsoft Learn security standards:
* **Azure Key Vault:** The centralized cloud service engineered specifically to securely store, encrypt, and manage application secrets, tokens, passwords, certificates, and API keys. During automated deployments (such as via ARM templates, Bicep, or Terraform), administrative credentials can be retrieved dynamically from Azure Key Vault without being exposed in plaintext scripts or code repositories.
* **Azure Information Protection (AIP / Microsoft Purview Information Protection):** A cloud-based compliance and data-loss prevention solution used to classify, label, and protect sensitive **documents and emails** (e.g., Word files, PDFs, Excel sheets) by applying metadata labels and encryption. It has no capability to store, manage, or inject administrative credentials into server deployment pipelines.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Azure Information Protection cannot safeguard automated CI/CD or template parameters; attempting to use it for administrative passwords fails to meet the operational requirement. The correct service to encrypt and securely pass credentials during deployment is **Azure Key Vault**.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for the words **"administrative credentials"**, **"passwords / connection strings"**, or **"secrets"** during **"automated deployment."**


* **Rule of Thumb:**
* Credentials, secrets, tokens, or encryption keys in deployment pipelines $\rightarrow$ **Azure Key Vault**.
* Document labels, email encryption, and file classification $\rightarrow$ **Azure Information Protection (AIP) / Microsoft Purview**.



## Q27

![Q27](/dump/question-images/q1-50/q27.png)

### 1. Extracted Question Summary

* **Scenario:** Your company intends to automate server deployment to Azure. There is concern that administrative credentials could be uncovered during this automated deployment process. You must ensure that administrative credentials are encrypted using a suitable Azure solution during deployment.


* **Proposed Solution:** You recommend the use of **Azure Information Protection**.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Correct.**


* Azure Information Protection (AIP) protects documents and emails (unstructured office data), not infrastructure deployment secrets or administrative credentials.



---

### 4. Official Microsoft Justification

* **Concept:** Secret and Key Management vs. Document/Information Protection.
* Under official Microsoft Learn security standards:
* **Azure Key Vault:** The centralized cloud service engineered specifically to securely store, encrypt, and manage application secrets, tokens, passwords, certificates, and API keys. During automated deployments (such as via ARM templates, Bicep, or Terraform), administrative credentials can be retrieved dynamically from Azure Key Vault without being exposed in plaintext scripts or code repositories.
* **Azure Information Protection (AIP / Microsoft Purview Information Protection):** A cloud-based compliance and data-loss prevention solution used to classify, label, and protect sensitive **documents and emails** (e.g., Word files, PDFs, Excel sheets) by applying metadata labels and encryption. It has no capability to store, manage, or inject administrative credentials into server deployment pipelines.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Azure Information Protection cannot safeguard automated CI/CD or template parameters; attempting to use it for administrative passwords fails to meet the operational requirement. The correct service to encrypt and securely pass credentials during deployment is **Azure Key Vault**.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for the words **"administrative credentials"**, **"passwords / connection strings"**, or **"secrets"** during **"automated deployment."**


* **Rule of Thumb:**
* Credentials, secrets, tokens, or encryption keys in deployment pipelines $\rightarrow$ **Azure Key Vault**.
* Document labels, email encryption, and file classification $\rightarrow$ **Azure Information Protection (AIP) / Microsoft Purview**.


## Q28
![Q28](/dump/question-images/q1-50/q28.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** The company wants to develop a cloud solution using Azure Government, which is restricted to certain types of clients.


* **Question:** Which of the following are the types of customers that can make use of Azure Government in this situation? (Drag and drop the correct options to the answer area).


* **Available Options:**
* A government contractor from any country.


* A government entity from any country.


* A European government contractor.


* A European government entity.


* A United States government contractor.


* A United States government entity.





---

### 2. Correct Answer

Drag the following two items into the **Answer** area:

* **A United States government entity.**


* **A United States government contractor.**



---

### 3. Verification of Visible Selection / Community Key

* *(No selection is pre-placed in the Answer area in the provided screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Sovereign / Specialized Cloud Offerings (Azure Government).
* Under official Microsoft Learn standards:
* **Azure Government** is a dedicated, physically and logically isolated cloud instance designed specifically to meet the stringent security, compliance, and regulatory standards of the **United States** public sector (such as FedRAMP High, DoD Impact Levels, CJIS, and ITAR).
* Eligibility is strictly restricted to:
1. **US federal, state, local, and tribal government agencies / entities.**
2. **US government commercial contractors and partners** who provide solutions and services to authorized US government entities (subject to validation and screening).


* Entities from other sovereign nations or international governments are not eligible for Azure Government; they use global Azure regions or their respective sovereign/local instances where available (e.g., Azure China 21Vianet).



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **A government contractor / entity from any country:** Incorrect. Foreign governments and foreign contractors cannot access or provision workloads in Azure Government due to strict US legal, jurisdictional, and citizenship-screening requirements.


* **A European government contractor / entity:** Incorrect. European public sector organizations operate in standard public Azure regions adhering to EU data boundaries (or specific local compliance frameworks), not US Azure Government.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Whenever you see **"Azure Government"**, the eligibility is strictly **US-only** (US federal/state/local government entities and their authorized US contractors).


* **Rule of Thumb:**
* *Azure Government* = **United States government entities & US contractors only**.


* *Azure China* = Operated by **21Vianet** (another specialized sovereign cloud commonly tested in AZ-900).



## Q29

![Q29](/dump/question-images/q1-50/q29.png)

### Answer

### 1. Extracted Question Summary

* **Scenario:** Your company has an Azure Active Directory (Azure AD, now Microsoft Entra ID) environment where users occasionally connect via the internet. You are tasked with ensuring that users connecting from an unidentified (unfamiliar/anonymous) IP address are automatically prompted to change their passwords.


* **Proposed Solution:** You configure the use of **Azure AD Identity Protection** (now Microsoft Entra ID Protection).


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **A. Yes**



---

### 3. Verification of Visible Selection / Community Key

* *(No selection or community answer is marked visible in the provided screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Microsoft Entra ID Protection (formerly Azure AD Identity Protection) and Risk-Based Policies.
* Under official Microsoft identity standards:
* **Microsoft Entra ID Protection** utilizes machine learning algorithms and heuristic intelligence to detect anomalies, suspicious sign-in behavior, and potential credential compromises.
* An unfamiliar sign-in property (such as signing in from an unidentified/new IP address or anonymous IP address) generates a **sign-in risk** or **user risk** event.
* Administrators can configure risk-based remediation policies (such as a **User risk policy** or **Sign-in risk policy** via Conditional Access) that automatically trigger a secure password reset and remediation flow when suspicious risk conditions are detected.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option B (No):** Incorrect. Selecting "No" would imply that Identity Protection cannot trigger automated password remediation based on suspicious IP/sign-in risk detection, whereas this automated risk-detection and self-remediation workflow is the primary purpose of Entra ID Protection.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Look for the combination of **"unidentified IP address"**, **"suspicious sign-in"**, or **"anonymous IP"** paired with **"automatically prompted/encouraged to change passwords."**


* **Rule of Thumb:**
* Automated risk detection + forced password change / remediation $\rightarrow$ **Azure AD Identity Protection (Microsoft Entra ID Protection)**.


* Standalone access rules (e.g., block by location, require MFA without risk scoring) $\rightarrow$ **Conditional Access**.


## Q30

![Q30](/dump/question-images/q1-50/q30.png)

### 1. Extracted Question Summary

* **Scenario:** Your company has an Azure Active Directory (Azure AD, now Microsoft Entra ID) environment where users occasionally connect via the internet. You are tasked with ensuring that users connecting from an unidentified IP address are automatically prompted to change their passwords.


* **Proposed Solution:** You configure the use of **Azure AD Privileged Identity Management** (now Microsoft Entra Privileged Identity Management / PIM).


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Correct.**


* The visible selection **B** is accurate because Privileged Identity Management (PIM) manages just-in-time administrative role activation, not risk-based user sign-in detection or automated password change remediation.



---

### 4. Official Microsoft Justification

* **Concept:** Microsoft Entra ID Protection (Risk-Based Policies) vs. Microsoft Entra Privileged Identity Management (PIM).
* Under official Microsoft Learn standards:
* **Privileged Identity Management (PIM):** A service that enables organizations to manage, control, and monitor access to critical Azure and Entra resources. It provides just-in-time (JIT) access, time-bound role assignment, approval workflows, and access reviews for highly privileged administrative accounts. It does not monitor external client IP addresses, evaluate user/sign-in risk levels, or automate password resets.
* **Microsoft Entra ID Protection (formerly Azure AD Identity Protection):** The service that flags anomalous or unidentified IP sign-in events using heuristic machine learning and applies automated remediation policies (such as enforcing a self-service password change upon high user risk).



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Selecting "Yes" conflates identity governance for elevated admin roles (PIM) with threat detection and risk-based access remediation (Identity Protection).



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Notice the distinction across the identity security question pairs:
* Unidentified IP address $\rightarrow$ require password change = **Azure AD Identity Protection** (**Yes** in Question 29).


* Unidentified IP address $\rightarrow$ require password change = **Privileged Identity Management (PIM)** (**No** in Question 30).




* **Rule of Thumb:**
* *PIM* = Just-in-time (JIT) elevation, admin roles, access reviews.
* *Identity Protection* = Risk detection, suspicious/unidentified IPs, automated password reset policies.


## Q31

![Q31](/dump/question-images/q1-50/q31.png)

### 1. Extracted Question Summary

* **Scenario:** You are planning a strategy to deploy numerous web servers and database servers to Azure. This strategy should allow connection types between the web servers and database servers to be controlled.


* **Proposed Solution:** You include **Network Security Groups (NSGs)** in your strategy.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **A. Yes**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: A): Correct.**


* The visible answer is accurate because Network Security Groups (NSGs) are the standard Azure mechanism to filter and control inbound and outbound network traffic based on IP address, port, and protocol between network tiers (such as web and database subnets).



---

### 4. Official Microsoft Justification

* **Concept:** Network Traffic Filtering and Multi-Tier Perimeter Security.
* Under official Microsoft Learn network security standards:
* A **Network Security Group (NSG)** contains security rules that allow or deny inbound network traffic to, or outbound network traffic from, several types of Azure resources (such as virtual network subnets or individual network interfaces / NICs).
* In a standard multi-tier deployment (e.g., web tier and database tier), an NSG applied to the database subnet can be configured with security rules that restrict traffic so that database ports (e.g., TCP port 1433 for SQL Server) only accept inbound connections originating from the web servers' subnet or an Application Security Group (ASG), while denying all other connection types.
* Therefore, using NSGs fulfills the requirement to control the permitted connection types between web servers and database servers.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option B (No):** Incorrect. Saying "No" would imply that NSGs cannot filter or regulate traffic types between internal Azure subnets, whereas packet filtering by 5-tuple (source IP/port, destination IP/port, and protocol) is the core function of NSGs.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Look for phrases like **"control connection types between servers/subnets"** or **"filter traffic within a virtual network."**


* **Rule of Thumb:**
* Filtering traffic / ports between subnets/VMs inside a VNet $\rightarrow$ **Network Security Group (NSG)** (or Application Security Group).


* Advanced Layer 7 stateful threat inspection, URL filtering, or centralized egress firewall across VNets $\rightarrow$ **Azure Firewall**.


## Q32

![Q32](/dump/question-images/q1-50/q32.png)

### 1. Extracted Question Summary

* **Scenario:** You are planning a strategy to deploy numerous web servers and database servers to Azure. This strategy should allow connection types between the web servers and database servers to be controlled.


* **Proposed Solution:** You include a **local network gateway** in your strategy.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Correct.**


* The marked selection **B** is accurate because a local network gateway is a routing configuration object representing an on-premises VPN endpoint, not a security filter for internal Azure subnet-to-subnet traffic.



---

### 4. Official Microsoft Justification

* **Concept:** Hybrid Networking Artifacts vs. Internal Virtual Network Traffic Filtering.
* Under official Microsoft Learn network documentation:
* A **Local Network Gateway** is an Azure resource that represents your on-premises physical location (edge device) in a Site-to-Site (S2S) VPN connection. It defines the on-premises gateway's public IP address and local IP address prefixes/subnets so Azure knows where to route hybrid cross-premises traffic.
* A local network gateway cannot filter, inspect, permit, or deny connection types or protocols between workloads deployed inside Azure virtual networks.
* Controlling connection types and network protocols between internal web and database tiers requires **Network Security Groups (NSGs)** or **Application Security Groups (ASGs)**.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Deploying a local network gateway provides zero firewalling or traffic inspection capabilities between cloud tiers; it only serves as metadata for cross-premises VPN routing.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for variations of the **"control connection types between web servers and database servers"** scenario:


* Strategy uses **Network Security Groups (NSGs)** $\rightarrow$ **Yes** (from Question 31).


* Strategy uses **Local Network Gateway** $\rightarrow$ **No** (Question 32).




* **Rule of Thumb:**
* *Local Network Gateway* = On-premises VPN representation in Azure.
* *Network Security Group (NSG)* = 5-tuple internal packet filter (IP, port, protocol).



## Q33

![Q33](/dump/question-images/q1-50/q33.png)


### 1. Extracted Question Summary

* **Scenario:** Your company's Active Directory forest includes thousands of user accounts. All network resources will be migrated to Azure, after which the on-premises data center will be retired. You are required to employ a strategy that reduces the effect (friction/impact) on users once the migration has been completed.


* **Proposed Solution:** You plan to require **Azure Multi-Factor Authentication (MFA)**.


* **Question:** Does the solution meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **B. No**

---

### 3. Verification of Visible Selection / Community Key

* *(No selection or community answer is marked visible in the provided screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Hybrid Identity Migration vs. Authentication Security Controls.
* Under official Microsoft identity guidelines:
* The objective is to **reduce the disruption and effect on end users** when transitioning thousands of accounts from an on-premises Active Directory forest to Azure. The standard method to achieve this is synchronizing accounts via **Microsoft Entra Connect (Azure AD Connect)** so users retain their existing credentials, UPNs, and passwords.


* **Azure Multi-Factor Authentication (MFA):** A security control that adds a second form of verification (e.g., authenticator app prompt, SMS, or FIDO2 key) during sign-in. While MFA enhances security, it does nothing to migrate or preserve account identities, and requiring it actually adds a step to the user sign-in flow rather than minimizing migration disruption.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option A (Yes):** Incorrect. Enforcing MFA does not establish cloud identities for on-premises AD DS accounts, nor does it reduce user impact during a data center retirement migration.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Contrast this question with **Question 14** from the same series:


* Migrate thousands of on-prem AD users + reduce effect on users $\rightarrow$ **Sync user accounts to Azure AD / Entra ID** = **Yes**.


* Migrate thousands of on-prem AD users + reduce effect on users $\rightarrow$ **Require Azure MFA** = **No**.




## Q34

![Q34](/dump/question-images/q1-50/q34.png)

### 1. Extracted Question Summary

* **Type:** HOTSPOT (Select Yes if the statement is true; otherwise, select No)


* **Statements:**
1. *“A platform as a service (PaaS) solution that hosts web apps in Azure provides full control of the operating systems that host applications.”*


2. *“A platform as a service (PaaS) solution that hosts web apps in Azure provides the ability to scale the platform automatically.”*


3. *“A platform as a service (PaaS) solution that hosts web apps in Azure provides professional development services to continuously add features to custom applications.”*





---

### 2. Correct Answer

| Statements | Yes | No |
| --- | --- | --- |
| A platform as a service (PaaS) solution that hosts web apps in Azure provides full control of the operating systems that host applications.| $\bigcirc$ | **Yes (No)** |
| A platform as a service (PaaS) solution that hosts web apps in Azure provides the ability to scale the platform automatically.| **Yes (Yes)** | $\bigcirc$ |
| A platform as a service (PaaS) solution that hosts web apps in Azure provides professional development services to continuously add features to custom applications.| $\bigcirc$ | **Yes (No)** |

<br>

* **Statement 1:** **No**
* **Statement 2:** **Yes**
* **Statement 3:** **No**

---

### 3. Verification of Visible Selection / Community Key

* *(No selections or radio buttons are filled in the uploaded screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Service Delivery Models (Shared Responsibility Model for PaaS).
* Under official Microsoft Learn definitions:
* **Operating System Management (Statement 1):** In a PaaS offering (such as Azure App Service), the cloud service provider manages the operating system, hardware, virtualization layer, OS patching, and network infrastructure. The consumer is responsible only for their application code and data; they **do not get full control (or root/RDP admin access)** of the underlying host operating system. Full OS control is exclusive to **Infrastructure as a Service (IaaS)**.
* **Automatic Scaling (Statement 2):** PaaS web hosting in Azure natively features **Autoscale** capabilities. You can configure rules to automatically scale compute instances in and out based on demand metrics (e.g., CPU percentage, memory pressure, HTTP queue depth, or schedule).
* **Development Services (Statement 3):** Azure PaaS provides hosting infrastructure, application runtimes, and developer tooling (e.g., CI/CD integration, deployment slots, SDKs). It **does not provide human software developers or managed professional consulting services** to write or continuously build business features for your custom application. That remains entirely the customer's development team's responsibility.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Statement 1 as "Yes":** Incorrect. Believing PaaS gives OS control confuses PaaS with **IaaS (Virtual Machines)**. If you need OS configuration control, custom kernel modules, or administrative RDP access to the base server, you must use IaaS.
* **Statement 3 as "Yes":** Incorrect. Believing PaaS includes human software engineering/consulting confuses cloud infrastructure services with professional outsourced IT consulting or software development agencies.

---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch out for claims attributing **"full operating system control"** to **PaaS** (always **False / No**) or implying that cloud infrastructure tiers provide **"human software developers / coding staff"** (always **False / No**).


* **Rule of Thumb:**
* Full OS control = **IaaS**
* Managed OS + Built-in Autoscale + Application Focus = **PaaS**


* End-user SaaS software / No code management = **SaaS**


## Q35

![Q35](/dump/question-images/q1-50/q35.png)


### 1. Extracted Question Summary

* **Type:** HOTSPOT (Select Yes if the statement is true; otherwise, select No)


* **Statements:**
1. *"Azure provides flexibility between capital expenditure (CapEx) and operational expenditure (OpEx)."*


2. *"If you create two Azure virtual machines that use the B2S size, each virtual machine will always generate the same monthly costs."*


3. *"When an Azure virtual machine is stopped, you continue to pay storage costs associated to the virtual machine."*





---

### 2. Correct Answer

| Statements | Yes | No |
| --- | --- | --- |
| Azure provides flexibility between capital expenditure (CapEx) and operational expenditure (OpEx).

 | **Yes (Yes)** | $\bigcirc$ |
| If you create two Azure virtual machines that use the B2S size, each virtual machine will always generate the same monthly costs.

 | $\bigcirc$ | **Yes (No)** |
| When an Azure virtual machine is stopped, you continue to pay storage costs associated to the virtual machine.

 | **Yes (Yes)** | $\bigcirc$ |

* **Statement 1:** **Yes**
* **Statement 2:** **No**
* **Statement 3:** **Yes**

---

### 3. Verification of Visible Selection / Community Key

* *(No selections or radio buttons are filled in the uploaded screenshot.)*



---

### 4. Official Microsoft Justification

* **Statement 1 (CapEx vs. OpEx Flexibility - Yes):** While public cloud compute defaults to an OpEx (pay-as-you-go) model, Azure allows organizations to balance CapEx and OpEx based on financial strategy. Organizations can leverage CapEx through upfront commitments like **Azure Reserved Virtual Machine Instances** (1-year or 3-year single upfront payment) or **Azure Hybrid Benefit** (applying existing on-premises software capital investments to cloud VMs).
* **Statement 2 (Identical VM Costs - No):** The monthly cost of two identical VM sizes (such as B2S) is not fixed or guaranteed to be identical:
* **Uptime / Runtime hours:** If VM A runs 24/7 (730 hours/month) and VM B runs for 20 hours/month, their compute charges differ drastically.
* **Region:** Deploying a B2S VM in *East US* carries a different hourly rate than deploying the same B2S VM in *Brazil South* or *Australia East*.
* **Storage & Egress Bandwidth:** Disks attached (Standard HDD vs. Premium SSD), disk sizes, outbound data transfer, and static public IP assignments all introduce distinct variable monthly costs.


* **Statement 3 (Storage Costs When VM Stopped - Yes):** Stopping/deallocating an Azure virtual machine releases its compute cores and RAM, stopping compute hourly charges. However, the virtual hard disks (OS disk and any attached data disks) remain provisioned in Azure Storage to retain the VM's state and data, continuing to accrue storage capacity costs.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Statement 1 as "No":** Incorrect. Believing Azure is strictly OpEx ignores procurement flexibility such as upfront reservations, prepay agreements, and enterprise licensing mobility (Azure Hybrid Benefit).
* **Statement 2 as "Yes":** Incorrect. Believing two VMs of the same SKU "always" incur the exact same monthly cost ignores running duration, geographic regional pricing tiers, and associated resource consumption (disks and bandwidth).
* **Statement 3 as "No":** Incorrect. Believing storage ceases upon stopping a VM confuses compute allocation with persisted storage. Data disks must be retained so the VM can boot again; therefore, storage costs always persist until explicitly deleted.

---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch out for the absolute word **"always"** in Statement 2 (*"will always generate the same monthly costs"*). In Azure billing, absolute cost claims are almost universally **No** due to regional rate differences and variable usage/bandwidth hours.


* **Rule of Thumb:**
* Deallocated VM = **Compute stops, Storage continues**.

## Q36

![Q36](/dump/question-images/q1-50/q36.png)


### 1. Extracted Question Summary

* **Scenario:** A sentence completion hotspot asking about user responsibility under the Shared Responsibility Model when implementing a Software as a Service (SaaS) solution.


* **Sentence:** *"When you are implementing a Software as a Service (SaaS) solution, you are responsible for [ dropdown ]"*


* **Dropdown Options:**
* configuring high availability.


* defining scalability rules.


* installing the SaaS solution.


* configuring the SaaS solution.





---

### 2. Correct Answer

* **configuring the SaaS solution.**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (configuring the SaaS solution): Correct.**


* The highlighted box in the screenshot is accurate. Under SaaS, the cloud provider manages infrastructure, high availability, installation, and scaling, while the customer is responsible for configuring application settings, managing access, and handling their data.



---

### 4. Official Microsoft Justification

* **Concept:** The Shared Responsibility Model across Cloud Service Models (IaaS vs. PaaS vs. SaaS).
* Under official Microsoft Learn standards:
* In a **SaaS** model (e.g., Microsoft 365, Dynamics 365), the cloud service provider provisions, installs, patches, secures, maintains, and ensures high availability/scalability for the underlying infrastructure and software runtime.
* The customer's role is strictly limited to managing their data, identities, device access, and **configuring application-level settings** (such as business rules, role assignments, user access permissions, and feature toggles) within the SaaS environment.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **configuring high availability:** Incorrect. High availability (fault tolerance, failover zones, and redundancy) is engineered and guaranteed by the SaaS provider via the service SLA.


* **defining scalability rules:** Incorrect. Auto-scaling and capacity planning are completely abstracted away and managed by the cloud provider; customers cannot set scaling metrics for SaaS applications.


* **installing the SaaS solution:** Incorrect. SaaS solutions are pre-installed, cloud-hosted, and managed centrally by Microsoft/provider; there is no installation phase required by the tenant administrator.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for the combination of **"SaaS"** and **"you are responsible for"**.


* **Rule of Thumb:**
* In SaaS, the customer **always** owns: *Information/Data*, *Devices/Endpoints*, *Accounts/Identities*, and *Application Configuration*.


* The cloud provider **always** owns: *Physical hosts*, *Physical network*, *OS patching*, *Application installation*, and *High Availability/Scaling*.



## Q37

![Q37](/dump/question-images/q1-50/q37.png)

### 1. Extracted Question Summary

* **Scenario:** You have an on-premises network containing several servers and plan to migrate all servers to Azure. You need to recommend a solution to ensure that some of the servers remain available if a single Azure data center goes offline for an extended period.


* **Question:** What should you include in the recommendation?


* **A.** fault tolerance


* **B.** elasticity


* **C.** scalability


* **D.** low latency





---

### 2. Correct Answer

* **A: fault tolerance**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: A): Correct.**


* The visible selection **A** is accurate because designing an architecture to withstand hardware, power, or physical data center outages without user interruption represents fault tolerance.



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Architecture Core Principles (Reliability, Availability, and Fault Tolerance).
* Under official Microsoft Learn definitions:
* **Fault Tolerance:** The ability of a system to remain operational and continue providing service without interruption even when one or more of its underlying hardware, software, or physical datacenter components experience a total failure. Deploying workloads across Azure Availability Zones (separate physical data centers with independent power, cooling, and networking) provides datacenter-level fault tolerance.
* While *high availability* focuses on minimizing overall downtime, *fault tolerance* specifically describes a design where a complete failure of an entire physical facility (data center) allows services to persist without operational disruption.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **B. elasticity:** Incorrect. Elasticity refers to a system's ability to dynamically allocate and de-allocate resources (scaling up/down or in/out automatically) in response to variable workload demands, not surviving physical facility outages.


* **C. scalability:** Incorrect. Scalability is the capability of a system to handle increasing workloads by adding compute, memory, or nodes (vertical or horizontal scale); it does not describe outage resilience.


* **D. low latency:** Incorrect. Low latency describes minimizing network response times and transit delays between clients and servers; it is a performance metric, not an availability mechanism.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for the phrase **"available if a single Azure data center goes offline"** or **"remains operational during a failure."**


* **Rule of Thumb:**
* Surviving hardware/datacenter outages without interruption $\rightarrow$ **Fault Tolerance** (implemented via Availability Zones or paired regions).


* Handling variable user traffic demand dynamically $\rightarrow$ **Elasticity / Scalability**.
* Minimizing network round-trip time $\rightarrow$ **Low Latency**.


## Q38

![Q38](/dump/question-images/q1-50/q38.png)


## Q39

![Q39](/dump/question-images/q1-50/q39.png)

That Gem instruction prompt is exceptionally well-structured. It accomplishes three critical requirements:

1. **Zero-Friction Submission:** The **Silent Image Intake** rule explicitly handles bare screenshots or multi-image questions without prompting you to type filler text.
2. **Defensive Dump Handling:** Section 2 directly attacks the primary hazard of exam dumps—confidently incorrect community keys or pre-highlighted errors.
3. **Structured Architecture Anchors:** The 6-part schema forces every breakdown to link back to official Microsoft standards rather than generic explanations.

---

### 1. Extracted Question Summary

* **Question:** What are two characteristics of the public cloud? Each correct answer presents a complete solution. NOTE: Each correct selection is worth one point.


* **Options:**
* **A.** dedicated hardware


* **B.** unsecured connections


* **C.** limited storage


* **D.** metered pricing


* **E.** self-service management





---

### 2. Correct Answer

* **D: metered pricing**


* **E: self-service management**



---

### 3. Verification of Visible Selection / Community Key

* *(No selection or community answer is marked visible in the provided screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Deployment Models (Public Cloud Characteristics).
* Under official Microsoft Learn cloud fundamentals:
* **Metered Pricing (Pay-as-you-go):** Public cloud services operate on a consumption-based expenditure model where organizations pay only for the compute cycles, storage gigabytes, and bandwidth consumed (metered usage), eliminating massive upfront capital investments.


* **Self-Service Management:** Consumers provision, configure, monitor, scale, and decommission cloud resources on demand using self-service web portals (Azure Portal), command-line tools (Azure CLI, PowerShell), or automation APIs without requiring manual intervention from the cloud provider's staff.


* Public cloud infrastructure is shared across multiple tenants (multi-tenant shared hardware) owned and maintained entirely by the cloud provider (Microsoft).



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **A. dedicated hardware:** Incorrect. Standard public cloud operates on **multi-tenant**, shared physical hardware. Dedicated hardware is a characteristic of a **private cloud** (or specialized single-tenant offerings like Azure Dedicated Host).


* **B. unsecured connections:** Incorrect. Public cloud traffic utilizes industry-standard encryption protocols (TLS/HTTPS, IPsec VPN, MACsec) both in transit and at rest; connections are not inherently unsecured.


* **C. limited storage:** Incorrect. Public cloud architecture provides virtually **unlimited elasticity and storage capacity** that scales dynamically to exabytes as required, contrasting sharply with physical on-premises capacity constraints.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch out for questions asking to contrast **Public Cloud** vs. **Private Cloud** characteristics:


* *Public Cloud* = Multi-tenant, **metered pricing / pay-as-you-go**, **self-service management**, high elasticity/near-limitless storage.


* *Private Cloud* = Single-tenant, **dedicated hardware**, owner responsible for hardware maintenance, limited scalability bound by physical acquisition.



## Q40

![Q40](/dump/question-images/q1-50/q40.png)

### 1. Extracted Question Summary

* **Type:** HOTSPOT (Sentence completion via dropdown selection)


* **Scenario:** *"When planning to migrate a public website to Azure, you must plan to [ dropdown ]"*


* **Dropdown Options:**
* deploy a VPN.


* pay monthly usage costs.


* pay to transfer all the website data to Azure.


* reduce the number of connections to the website.





---

### 2. Correct Answer

* **pay monthly usage costs.**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (pay monthly usage costs): Correct.**


* The highlighted box in the screenshot is accurate. Public cloud adoption transitions IT expenses into an operational expenditure (OpEx) consumption model where you are billed on an ongoing monthly basis for provisioned compute, storage, and egress network bandwidth.



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Financial Models (OpEx vs. CapEx) and Azure Data Ingress/Egress Billing Rules.
* Under official Microsoft Learn pricing and architecture principles:
* **Operational Expenditure (OpEx):** Azure operates predominantly on a consumption/subscription-based model where customers are billed on an ongoing monthly cycle for resource usage (e.g., App Service Plan hosting hours, VM compute uptime, database tiers).


* **Inbound Data Transfer (Ingress):** Data transfer **into** Azure data centers (ingress) is **free of charge**. Therefore, migrating/uploading your website files and initial data into Azure incurs no transfer fee. Charges only apply to outbound data transfer (egress) over the internet.


* **Public Accessibility:** A public-facing website serves external internet users over HTTP/HTTPS; it does not require a Virtual Private Network (VPN) gateway or connection limitations.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **deploy a VPN:** Incorrect. A VPN creates a secure private tunnel to an internal virtual network; it is neither required nor standard for hosting a publicly accessible website on the internet.


* **pay to transfer all the website data to Azure:** Incorrect. Inbound data transfers (ingress) into Azure data centers are free.


* **reduce the number of connections to the website:** Incorrect. Cloud platforms are designed for scalability and elasticity, allowing websites to handle increased or fluctuating traffic automatically rather than throttling or reducing visitors.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch out for the common misconception that Azure charges for *all* data transfers.
* **Rule of Thumb:**
* **Inbound data (Ingress / into Azure)** = **Always FREE** (you never pay to upload data into Azure).


* **Outbound data (Egress / leaving Azure to the internet)** = **Billed per GB** (metered).


## Q41

![Q41](/dump/question-images/q1-50/q41.png)

### 1. Extracted Question Summary

* **Scenario:** Your company plans to migrate all its data and resources to Azure. The company's migration plan specifies that **only Platform as a Service (PaaS) solutions** must be used in Azure. You need to deploy an Azure environment that satisfies this migration plan.


* **Proposed Solution:** You create an **Azure App Service** and **Azure SQL databases**.


* **Question:** Does this meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **A. Yes**



---

### 3. Verification of Visible Selection / Community Key

* *(No selection or community answer is marked visible in the provided screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Service Delivery Models (PaaS vs. IaaS vs. SaaS).
* Under official Microsoft Learn definitions:
* **Azure App Service:** A fully managed Platform as a Service (PaaS) hosting environment for web applications, REST APIs, and mobile back ends. Azure manages the operating system, infrastructure patching, network scaling, and web server configuration.
* **Azure SQL Database:** A fully managed PaaS relational database service running on the latest stable Enterprise Edition of the Microsoft SQL Server database engine. Hardware provisioning, OS patching, backups, and high availability are managed automatically by Microsoft.
* Because **both** components deployed in the solution (Azure App Service and Azure SQL Database) are classified as PaaS, the solution satisfies the requirement that *only* PaaS solutions must be used.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option B (No):** Incorrect. Answering "No" would imply that either Azure App Service or Azure SQL Database falls under Infrastructure as a Service (IaaS) or Software as a Service (SaaS). However, both are flagship Microsoft PaaS services that require zero operating system or database engine infrastructure maintenance.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for questions that demand **"only PaaS solutions"** versus variants that introduce IaaS:


* App Service + Azure SQL Database $\rightarrow$ **PaaS + PaaS = Yes**.


* App Service + SQL Server installed on an **Azure Virtual Machine** $\rightarrow$ **PaaS + IaaS = No** (since VMs are IaaS).
* Azure Virtual Machines + Azure Virtual Network $\rightarrow$ **IaaS = No**.


## Q42

![Q42](/dump/question-images/q1-50/q42.png)





## Q43

![Q43](/dump/question-images/q1-50/q43.png)

### 1. Extracted Question Summary

* **Scenario:** Your company plans to migrate all its data and resources to Azure. The company's migration plan specifies that **only Platform as a Service (PaaS) solutions** must be used in Azure. You need to deploy an Azure environment that satisfies this migration plan.


* **Proposed Solution:** You create an **Azure App Service and Azure Storage accounts**.


* **Question:** Does this meet the goal?


* **A.** Yes


* **B.** No





---

### 2. Correct Answer

* **A: Yes**

---

### 3. Verification of Visible Selection / Community Key

* *(No selection or community answer is marked visible in the provided screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Service Delivery Models (PaaS vs. IaaS Classification).
* Under official Microsoft Learn definitions:
* **Azure App Service:** A fully managed Platform as a Service (PaaS) engine for building and hosting web apps, mobile app back ends, and RESTful APIs without managing infrastructure or operating systems.
* **Azure Storage Accounts (Blob, Files, Queues, Tables):** Classified by Microsoft as a **PaaS offering**. Azure abstracts the underlying physical servers, disk hardware, RAID configurations, operating system maintenance, and storage fabric updates. The user manages only their stored data, security keys, access tiers, and permissions.
* Because **both** Azure App Service and Azure Storage accounts are PaaS services, deploying them adheres strictly to the requirement that *only* PaaS solutions are used.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Option B (No):** Incorrect. Candidates sometimes mistake Azure Storage as IaaS because raw virtual disks (VHDs) used by IaaS Virtual Machines reside inside storage accounts. However, the Azure Storage account service itself—when provisioned for blobs, tables, files, or queues—is fundamentally a managed PaaS platform.

---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch out for the full trio of questions in this exact AZ-900 scenario family:
1. App Service + Azure SQL Database $\rightarrow$ **Yes** (PaaS + PaaS).


2. App Service + Azure Storage Accounts $\rightarrow$ **Yes** (PaaS + PaaS).


3. App Service + Azure Virtual Machines running SQL Server $\rightarrow$ **No** (VMs make it IaaS).



## Q44

![Q44](/dump/question-images/q1-50/q44.png)

### 1. Extracted Question Summary

* **Scenario:** Your company hosts an accounting application named **App1** that is used by all company customers. App1 experiences low usage during the first three weeks of each month and very high usage during the last week of each month.


* **Question:** Which benefit of Azure Cloud Services supports cost management for this type of usage pattern?


* **Options:**
* **A.** high availability


* **B.** high latency


* **C.** elasticity


* **D.** load balancing





---

### 2. Correct Answer

* **C: elasticity**



---

### 3. Verification of Visible Selection / Community Key

* *(No selection or community answer is marked visible in the provided screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Economics and Elasticity vs. Static Provisioning.
* Under official Microsoft Learn cloud fundamentals:
* **Elasticity:** The ability of a cloud platform to dynamically provision and de-provision computing resources automatically (scaling out/in or up/down) in direct response to fluctuating workload demands.
* For cyclical or bursty workloads—such as end-of-month accounting reconciliations—elasticity supports cost management by ensuring you only pay for high-capacity compute resources during peak demand (the last week) and automatically scale down to minimal capacity during idle periods (the first three weeks), preventing wasted expenditure on over-provisioned idle infrastructure.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **A. high availability:** Incorrect. High availability ensures that an application remains accessible with minimal downtime regardless of hardware failures, but it does not automatically resize resources to optimize spend based on variable demand cycles.


* **B. high latency:** Incorrect. High latency is a network delay performance degradation, not a cloud benefit or cost management mechanism.


* **D. load balancing:** Incorrect. Load balancing distributes incoming network traffic evenly across a backend pool of healthy servers, but load balancers do not by themselves dynamically add or tear down resources to optimize monthly cost.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Look for cyclical or variable workload descriptions like **"low usage during the first three weeks... very high usage during the last week"** or **"spikes during business hours and drops off at night"** paired with **"cost management."**


* **Rule of Thumb:**
* Dynamic scaling to match changing load and reduce idle cost $\rightarrow$ **Elasticity**.


* Ability to grow to handle larger total workloads over time $\rightarrow$ **Scalability**.
* Ensuring near-zero downtime $\rightarrow$ **High Availability**.



## Q45

![Q45](/dump/question-images/q1-50/q45.png)

### 1. Extracted Question Summary

* **Scenario:** You plan to migrate a web application to Azure. The web application is accessed by external users. You need to recommend a cloud deployment solution to minimize the amount of administrative effort used to manage the web application.


* **Question:** What should you include in the recommendation?


* **Options:**
* **A.** Software as a Service (SaaS)


* **B.** Platform as a Service (PaaS)


* **C.** Infrastructure as a Service (IaaS)


* **D.** Database as a Service (DaaS)





---

### 2. Correct Answer

* **B: Platform as a Service (PaaS)**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (Answer: B): Correct.**


* The visible answer is accurate because you are migrating your own custom web application code, making **PaaS** (e.g., Azure App Service) the optimal tier to eliminate OS management, patching, and hardware overhead while maintaining ownership of the app.



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Service Delivery Models & Shared Responsibility (IaaS vs. PaaS vs. SaaS).
* Under official Microsoft Learn standards:
* When migrating an existing custom web application to Azure, **Platform as a Service (PaaS)** minimizes administrative effort by offloading the operating system, web server runtime (IIS, Apache, NGINX), patching, scaling, and physical hardware management to Microsoft.
* The organization only manages the application code and deployment configurations.
* Compared to **IaaS** (where the customer must install updates, patch the OS, and manage virtual network security), PaaS drastically reduces ongoing maintenance and administrative overhead.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **A. Software as a Service (SaaS):** Incorrect. SaaS delivers complete end-user software (like Microsoft 365 or Salesforce). You cannot "migrate" your own custom proprietary web application code directly into a SaaS model; SaaS replaces custom software rather than hosting it.


* **C. Infrastructure as a Service (IaaS):** Incorrect. While you can host a web app on Azure VMs, IaaS requires the *highest* level of ongoing administrative effort (managing OS updates, security patches, backups, and firewall configurations).


* **D. Database as a Service (DaaS):** Incorrect. DaaS handles managed database engines (e.g., Azure SQL Database), not the hosting and execution environment for web applications.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for the phrase **"migrate a [custom] web application"** paired with **"minimize administrative effort."**


* **Rule of Thumb:**
* Migrate custom web app + minimize management $\rightarrow$ **PaaS (Azure App Service)**.


* Need full control of OS / custom server software $\rightarrow$ **IaaS (Azure VMs)**.
* Purchase off-the-shelf software with zero infra/code management $\rightarrow$ **SaaS**.



## Q46

![Q46](/dump/question-images/q1-50/q46.png)

### 1. Extracted Question Summary

* **Type:** HOTSPOT (Select the appropriate cloud service model for each listed Azure service via dropdowns).


* **Question:** Which cloud deployment solution is used for Azure virtual machines and Azure SQL databases?


* **Dropdown Items:**
1. **Azure virtual machines:**
* Infrastructure as a service (IaaS)


* Platform as a service (PaaS)


* Software as a service (SaaS)




2. **Azure SQL databases:**
* Infrastructure as a service (IaaS)


* Platform as a service (PaaS)


* Software as a service (SaaS)







---

### 2. Correct Answer

* **Azure virtual machines:** **Infrastructure as a service (IaaS)**


* **Azure SQL databases:** **Platform as a service (PaaS)**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key:** **Correct.**


* Both boxed dropdown selections in the screenshot accurately reflect Microsoft's official classification: VMs are IaaS, while Azure SQL Database is PaaS.



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Service Delivery Models & The Shared Responsibility Model.
* Under official Microsoft Learn standards:
* **Azure Virtual Machines (IaaS):** Provides raw computing infrastructure (virtualized CPU, memory, storage, and networking). The customer maintains complete administrative control over the guest operating system, runtime installation, security patching, and application stacks.


* **Azure SQL Database (PaaS):** An intelligent, fully managed relational database engine hosted on cloud infrastructure. Microsoft manages OS patching, hardware provisioning, automated backups, and high availability, allowing the user to manage solely the database schemas, tables, and data without server-level administrative burdens.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Azure virtual machines as PaaS/SaaS:** Incorrect. Virtual machines do not abstract the operating system (which excludes PaaS) nor do they represent finished end-user software (which excludes SaaS).


* **Azure SQL databases as IaaS:** Incorrect. If you install SQL Server manually inside an Azure Virtual Machine, that configuration is IaaS. However, the standalone managed offering **Azure SQL Database** abstracts the server completely, making it PaaS.


* **Azure SQL databases as SaaS:** Incorrect. A database platform requires database design, SQL querying, and application integration; it is not a ready-to-use software application delivered to business end users (such as Microsoft 365 or Dynamics 365).



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch out for the crucial phrasing difference between **SQL on Azure VMs** vs. **Azure SQL Database**:


* *SQL Server running on an Azure VM* = **IaaS** (you manage the VM OS and SQL Server installation).
* *Azure SQL Database* (or Azure SQL Managed Instance) = **PaaS** (fully managed by Microsoft).



## Q47

![Q47](/dump/question-images/q1-50/q47.png)

### 1. Extracted Question Summary

* **Scenario:** You have an on-premises network containing 100 servers. You need to recommend a solution that provides additional resources to your users while minimizing both capital expenditure (CapEx) and operational expenditure (OpEx) costs.


* **Question:** What should you include in the recommendation?


* **Options:**
* **A.** a complete migration to the public cloud


* **B.** an additional data center


* **C.** a private cloud


* **D.** a hybrid cloud





---

### 2. Correct Answer

* **D: a hybrid cloud**



---

### 3. Verification of Visible Selection / Community Key

* *(No selection or community key is marked visible in the provided screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Deployment Models (Public vs. Private vs. Hybrid Cloud Economics).
* Under official Microsoft Learn fundamentals:
* **Hybrid Cloud:** Combines an existing on-premises infrastructure (private environment) with public cloud services.
* The organization already has 100 operational servers representing existing capital investments. Rather than purchasing new physical servers/data centers (incurring heavy CapEx) or undertaking an expensive, immediate full-scale re-architecture and migration of all 100 existing servers (incurring massive immediate migration and migration OpEx costs), adopting a **hybrid cloud** allows the organization to keep existing workloads on-premises while bursting or expanding **only the additional required capacity** into the public cloud on a pay-as-you-go basis.


* This minimizes new CapEx (zero new on-premises hardware purchases) and optimizes OpEx (paying only for the marginal additional cloud resources).





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **A. a complete migration to the public cloud:** Incorrect. Completely abandoning 100 working on-premises servers writes off existing, usable hardware assets prematurely and introduces immediate, extensive migration OpEx (re-engineering, downtime, migration tooling, and moving all 100 workloads).


* **B. an additional data center:** Incorrect. Building or leasing an entire new data center incurs enormous upfront capital costs (CapEx for physical real estate, power, cooling, network gear) and high ongoing facility operational costs (OpEx).


* **C. a private cloud:** Incorrect. Deploying a private cloud requires purchasing, racking, and managing additional physical servers and virtualization infrastructure locally, generating significant capital expenditure (CapEx).



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for the combination of **"existing on-premises servers"** + **"need additional resources"** + **"minimize capital and operational expenditure."**


* **Rule of Thumb:**
* Expand existing on-prem capacity with minimal new hardware cost $\rightarrow$ **Hybrid Cloud** (extend to public cloud without discarding current hardware).


* Complete elimination of all on-prem hardware $\rightarrow$ **Public Cloud**.
* Strict compliance/data isolation on dedicated hardware $\rightarrow$ **Private Cloud**.


## Q48

![Q48](/dump/question-images/q1-50/q48.png)


## Q49

![Q49](/dump/question-images/q1-50/q49.png)


### 1. Extracted Question Summary

* **Scenario:** You plan to migrate several servers from an on-premises network to Azure.


* **Question:** What is an advantage of using a public cloud service for the servers over an on-premises network?


* **Options:**
* **A.** The public cloud is owned by the public, NOT a private corporation


* **B.** The public cloud is a crowd-sourcing solution that provides corporations with the ability to enhance the cloud


* **C.** All public cloud resources can be freely accessed by every member of the public


* **D.** The public cloud is a shared entity whereby multiple corporations each use a portion of the resources in the cloud





---

### 2. Correct Answer

* **D: The public cloud is a shared entity whereby multiple corporations each use a portion of the resources in the cloud**



---

### 3. Verification of Visible Selection / Community Key

* **Visible Key (D): Correct.**


* The highlighted box in the screenshot is accurate because public cloud infrastructure relies on multi-tenancy and pooled resources, allowing organizations to consume only what they need without procuring entire dedicated data centers.



---

### 4. Official Microsoft Justification

* **Concept:** Public Cloud Multi-Tenancy and Economies of Scale.
* Under official Microsoft Learn fundamentals:
* In a **public cloud** deployment model, the physical hardware, network, and datacenter facilities are owned, operated, and maintained by a third-party cloud service provider (such as Microsoft).
* The infrastructure is a **multi-tenant environment** where multiple organizations (tenants) share a common pool of compute, storage, and networking resources.


* This resource pooling provides an economic advantage over on-premises networks because customers do not need to buy, house, power, or maintain idle physical hardware; they only provision and pay for the specific slice of resources they require, benefiting from massive economies of scale.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **A. The public cloud is owned by the public, NOT a private corporation:** Incorrect. Public cloud platforms are commercial entities owned and managed by private corporations (e.g., Microsoft, Amazon, Google).


* **B. The public cloud is a crowd-sourcing solution that provides corporations with the ability to enhance the cloud:** Incorrect. Cloud computing is not a crowdsourced platform; infrastructure, platform services, and feature rollouts are managed entirely by the cloud service provider.


* **C. All public cloud resources can be freely accessed by every member of the public:** Incorrect. "Public" refers to infrastructure availability for general commercial use, not open public access to your data or workloads. Resources remain secured, private, and access-restricted via identity and access management (e.g., Microsoft Entra ID).



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Do not let the everyday word **"public"** mislead you into thinking it means "government/publicly owned" or "accessible to anyone without authentication."


* **Rule of Thumb:**
* *Public Cloud* = Owned by a third-party vendor (Microsoft), multi-tenant (shared infrastructure among multiple organizations), access controlled securely by tenant.


* *Private Cloud* = Single-tenant, dedicated exclusively to one organization.

## Q50

![Q50](/dump/question-images/q1-50/q50.png)

### 1. Extracted Question Summary

* **Type:** HOTSPOT (Sentence completion via dropdown selection)


* **Scenario:** *"Azure Site Recovery provides [ dropdown ] for virtual machines."*


* **Dropdown Options:**
* fault tolerance


* disaster recovery


* elasticity


* high availability





---

### 2. Correct Answer

* **disaster recovery**



---

### 3. Verification of Visible Selection / Community Key

* *(No option is pre-selected or highlighted in the uploaded screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Business Continuity and Disaster Recovery (BCDR) in Azure.
* Under official Microsoft Learn standards:
* **Azure Site Recovery (ASR):** Microsoft’s native **Disaster Recovery as a Service (DRaaS)**. It orchestrates replication, failover, and failback of physical servers and virtual machines across regions (Azure-to-Azure) or from on-premises environments (VMware/Hyper-V) to Azure.


* When an outage or regional catastrophe occurs, ASR brings workloads back online in a secondary location according to predefined Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO), making it a dedicated **disaster recovery** service.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **fault tolerance:** Incorrect. Fault tolerance ensures continuous operation without interruption during a failure (typically through active duplication, redundant hardware, or multi-zone clusters). ASR involves a failover sequence during an outage, which entails brief downtime and recovery steps rather than zero-interruption redundancy.


* **elasticity:** Incorrect. Elasticity refers to dynamically scaling compute resources up/down or in/out based on changing workload demand (handled by Virtual Machine Scale Sets or Autoscale).


* **high availability:** Incorrect. High availability keeps applications reachable and resilient within a region during routine component disruptions (implemented using Availability Sets, Availability Zones, and load balancers). Site Recovery is invoked when a major disruption or disaster exceeds standard local high availability mechanisms.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Do not confuse **Disaster Recovery (DR)** with **High Availability (HA)** or **Fault Tolerance (FT)**:


* Keep running continuously within a datacenter/region $\rightarrow$ **High Availability / Fault Tolerance** (Availability Sets / Zones).


* Replicate to a secondary location/region to restore operations after a major disaster $\rightarrow$ **Disaster Recovery (Azure Site Recovery)**.



## Q51

![Q51](/dump/question-images/q51-100/q51.png)

## Q52

![Q52](/dump/question-images/q51-100/q52.png)



## Q53

![Q53](/dump/question-images/q51-100/q53.png)


## Q54

![Q54](/dump/question-images/q51-100/q54.png)


### 1. Extracted Question Summary

* **Type:** DRAG DROP (Match Azure service benefits to their correct descriptions).


* **Answer Options (Left Column):**
* Disaster recovery


* Fault tolerance


* Low latency


* Dynamic scalability




* **Descriptions (Right Column / Answer Area):**
1. *“A cloud service that remains available after a failure occurs”*


2. *“A cloud service that can be recovered after a failure occurs”*


3. *“A cloud service that performs quickly when demand increases”*


4. *“A cloud service that can be accessed quickly from the Internet”*





---

### 2. Correct Answer

| Description | Matched Benefit |
| --- | --- |
| A cloud service that remains available after a failure occurs| **Fault tolerance** |
| A cloud service that can be recovered after a failure occurs| **Disaster recovery** |
| A cloud service that performs quickly when demand increases| **Dynamic scalability** |
| A cloud service that can be accessed quickly from the Internet| **Low latency** |

---

### 3. Verification of Visible Selection / Community Key

* *(No options or drop targets are filled in the uploaded screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Core Cloud Architecture Principles & Benefits.
* Under official Microsoft Learn fundamentals:
* **Fault tolerance:** A design principle where a service continues operating without downtime or noticeable interruption when an underlying component fails (it *remains available* throughout the failure event).
* **Disaster recovery:** A business continuity process focused on bringing services back online (*recovered*) after an outage or catastrophic failure event occurs.
* **Dynamic scalability:** The automated or programmatic ability to expand compute/capacity resources in response to rising traffic, ensuring consistent performance (*performs quickly when demand increases*).
* **Low latency:** The minimization of transit and response delays across the network, enabling users to interact with and access services with minimal delay (*accessed quickly from the Internet*).



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **"Remains available" vs. "Can be recovered":**
* Choosing *Disaster recovery* for the first item is incorrect; disaster recovery implies an outage or interruption followed by restoration, whereas *Fault tolerance* prevents the outage from taking down the service.


* **"Performs quickly when demand increases" vs. "Accessed quickly from the Internet":**
* High load/demand performance relates to resource scaling (*Dynamic scalability*), whereas general network transport speed across the web reflects network round-trip delay (*Low latency*).



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch the verb pairing in the first two items: **"remains available"** vs. **"can be recovered"**.


* **Rule of Thumb:**
* *Remains available* during failure = **Fault tolerance**.


* *Recovered* after failure = **Disaster recovery**.


* Spiking load/demand = **Scalability**.


* Speed over network/Internet = **Low latency**.



## Q55

![Q55](/dump/question-images/q51-100/q55.png)



## Q56

![Q56](/dump/question-images/q51-100/q56.png)



## Q57

![Q57](/dump/question-images/q51-100/q57.png)


## Q58

![Q58](/dump/question-images/q51-100/q58.png)


### 1. Extracted Question Summary

* **Type:** HOTSPOT (Select Yes if the statement is true; otherwise, select No).


* **Statements:**
1. *"Azure Pay-As-You-Go pricing is an example of CapEx."*


2. *"Paying electricity for your datacenter is an example of OpEx."*


3. *"Deploying your own datacenter is an example of CapEx."*





---

### 2. Correct Answer

| Statements | Yes | No |
| --- | --- | --- |
| Azure Pay-As-You-Go pricing is an example of CapEx.| $\bigcirc$ | **No** |
| Paying electricity for your datacenter is an example of OpEx.| **Yes** | $\bigcirc$ |
| Deploying your own datacenter is an example of CapEx.| **Yes** | $\bigcirc$ |


<br>

* **Statement 1:** **No**
* **Statement 2:** **Yes**
* **Statement 3:** **Yes**

---

### 3. Verification of Visible Selection / Community Key

* **Visible Key in Screenshot:** Shows **No, No, Yes**.


* **Verdict:** **Incorrect / Flawed Key.**
* The second statement is marked **No** in the screenshot, which is **incorrect**. Electricity and utility bills for a datacenter are recurring day-to-day operating expenses, making them an official example of **OpEx (Yes)**.





---

### 4. Official Microsoft Justification

* **Concept:** Cloud Economics — Capital Expenditure (CapEx) vs. Operational Expenditure (OpEx).
* Under official Microsoft Learn standards:
* **Capital Expenditure (CapEx):** Upfront spending on physical infrastructure and assets that have residual value and are capitalized/depreciated over time on financial balance sheets.
* *Statement 3 (Deploying your own datacenter – Yes):* Purchasing physical land, erecting buildings, procuring servers, and installing cooling/power plants are massive upfront physical capital investments (CapEx).


* *Statement 1 (Azure Pay-As-You-Go is CapEx – No):* Pay-As-You-Go cloud consumption carries no upfront equipment purchase; it is billed on consumption and is classified as OpEx, not CapEx.




* **Operational Expenditure (OpEx):** Ongoing, recurring operational expenses incurred during day-to-day business execution.
* *Statement 2 (Electricity for your datacenter – Yes):* Ongoing operational costs such as electricity bills, cooling power, facility maintenance, and recurring software licensing are ongoing operational costs categorized under OpEx.







---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Statement 1 marked "Yes":** Incorrect. Conflates cloud consumption billing with upfront physical asset acquisition.
* **Statement 2 marked "No":** Incorrect (Dump Error). Datacenter electricity is a recurring utility bill consumed to keep infrastructure operating; it possesses zero capital asset value and is a direct operational cost (OpEx).


* **Statement 3 marked "No":** Incorrect. Building out physical datacenter infrastructure is one of Microsoft's textbook definitions of Capital Expenditure (CapEx).



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch out for dumps mislabeling **datacenter utilities/running costs** as CapEx simply because they occur on-premises.
* **Rule of Thumb:**
* Upfront physical assets (hardware, servers, datacenter facilities) = **CapEx**.


* Day-to-day operating costs (electricity, facility rent, cloud pay-as-you-go bills) = **OpEx**.


## Q59

![Q59](/dump/question-images/q51-100/q59.png)



## Q60

![Q60](/dump/question-images/q51-100/q60.png)

### 1. Extracted Question Summary

* **Question:** To which cloud models can you deploy physical servers?


* **Options:**
* **A.** private cloud and hybrid cloud only


* **B.** private cloud only


* **C.** private cloud, hybrid cloud and public cloud


* **D.** hybrid cloud only





---

### 2. Correct Answer

* **A: private cloud and hybrid cloud only**



---

### 3. Verification of Visible Selection / Community Key

* *(No selection or community answer is marked visible in the provided screenshot.)*



---

### 4. Official Microsoft Justification

* **Concept:** Cloud Deployment Models & Physical Hardware Management.
* Under official Microsoft Learn fundamentals:
* In a **public cloud**, all physical hardware and servers are owned, deployed, and managed exclusively by the cloud provider (Microsoft). The customer has no ability or authorization to physically provision, install, or rack bare-metal physical servers.


* In a **private cloud**, an organization owns or controls the dedicated physical infrastructure, meaning the organization itself purchases, racks, and deploys physical host servers into the environment.
* In a **hybrid cloud**, the architecture combines public cloud services with an organization’s on-premises/private infrastructure. Because the organization manages and maintains the on-premises private footprint of the hybrid architecture, it can deploy physical servers to that portion of the environment.


* Therefore, deploying physical servers is possible only in **private cloud and hybrid cloud** environments.





---

### 5. Distractor Analysis (Why Others Are Wrong)

* **B. private cloud only:** Incorrect. This ignores the hybrid model, where the on-premises segment of the hybrid infrastructure permits the customer to deploy and operate physical host servers.


* **C. private cloud, hybrid cloud and public cloud:** Incorrect. Physical servers cannot be deployed by customers to a public cloud. In public cloud architectures, the provider abstracts and maintains physical host hardware; customers deploy virtualized compute instances (VMs, containers, App Services).


* **D. hybrid cloud only:** Incorrect. A private cloud operates entirely on customer-managed or dedicated host infrastructure, making physical server deployment a primary capability of private clouds as well.



---

### 6. Exam Keyword / Trap Alert

* **Trap / Trigger:** Watch for the keyword **"physical servers"** vs. "virtual machines".


* **Rule of Thumb:**
* Customer deploys **physical hardware / bare metal** $\rightarrow$ **Private and Hybrid only**.


* Hardware completely owned and provisioned by the third-party provider $\rightarrow$ **Public cloud**.




## Q61

![Q61](/dump/question-images/q51-100/q61.png)



## Q62

![Q62](/dump/question-images/q51-100/q62.png)


The selections marked in the image are all correct:

1. A company can extend a private cloud by adding its own physical servers to the public cloud. — No
2. To build a hybrid cloud, you must deploy resources to the public cloud. — Yes
3. A private cloud must be disconnected from the internet. — No

Detailed Breakdown

⚬ Statement 1: No
  ⚬ In a public cloud model (such as Microsoft Azure), the underlying physical hardware and datacenters are entirely owned, operated, and maintained by the cloud provider. A customer cannot ship or install their own physical server hardware into Microsoft's public datacenters to expand cloud capacity.
⚬ Statement 2: Yes
  ⚬ By definition, a hybrid cloud combines at least one private environment (on-premises datacenter or private cloud) with at least one public cloud service (like Azure), connected via technologies such as VPN or Azure ExpressRoute. Without resources deployed in a public cloud, the architecture remains purely a private cloud/on-premises deployment.
⚬ Statement 3: No
  ⚬ A private cloud is dedicated to a single organization, but it does not need to be air-gapped or disconnected from the internet. Private clouds routinely connect to the internet to host customer-facing web applications, enable remote employee access via secure VPNs, receive software updates, and communicate with external services.


  ## Q63

  ![Q63](/dump/question-images/q51-100/q63.png)



  ## Q64

  ![Q64](/dump/question-images/q51-100/q64.png)



  ## Q65

  ![Q65](/dump/question-images/q51-100/q65.png)


  ## Q66

  ![Q66](/dump/question-images/q51-100/q66.png)



  ## Q67

  ![Q67](/dump/question-images/q51-100/q67.png)



  ## Q68

  ![Q68](/dump/question-images/q51-100/q68.png)



  ## Q69

  ![Q69](/dump/question-images/q51-100/q69.png)


  ### 1. Extracted Question Summary

* **Scenario:** Question 69 (HOTSPOT) asks to evaluate three statements and select **Yes** if the statement is true, or **No** if the statement is false:


* **Statement 1:** With software as a service (SaaS), you must apply software updates.


* **Statement 2:** With infrastructure as a service (IaaS), you must install the software that you want to use.


* **Statement 3:** Azure Backup is an example of platform as a service (PaaS).





---

### 2. Correct Answer

* **Statement 1:** **No**
* **Statement 2:** **Yes**
* **Statement 3:** **No**

---

### 3. Verification of Visible Selection / Community Key

* **Statement 1:** Marked **No** — **Correct**. The cloud service provider handles application updates and maintenance in SaaS.


* **Statement 2:** Marked **Yes** — **Correct**. With IaaS, the customer is responsible for configuring the OS and installing/maintaining all application software.


* **Statement 3:** Marked **Yes** — **Incorrect / Disputed**. Azure Backup is provided as a fully managed backup service, categorized under **SaaS / Backup as a Service (BaaS)**, not PaaS.



---

### 4. Official Microsoft Justification

* **Shared Responsibility Model:**
* Under **SaaS**, the cloud provider manages the physical infrastructure, network, operating system, runtime, and the application itself—including patching and software upgrades.
* Under **IaaS**, the cloud provider manages physical hardware, virtualization, and physical networking, while the consumer maintains the operating system, middleware, runtime, and installed software applications.


* **Azure Service Categorization:** **Azure Backup** is a turnkey, cloud-based storage and backup management solution provided as a ready-to-use software service (SaaS / BaaS) requiring zero application deployment or environment runtime configuration by the user.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Statement 1 ("Yes" is wrong):** If you had to install and maintain software updates, the model would fall under IaaS or PaaS; SaaS completely offloads version management and patching to the vendor.
* **Statement 2 ("No" is wrong):** IaaS delivers raw compute (VMs, storage, networking); the consumer is entirely responsible for provisioning software runtimes, dependencies, and application packages.
* **Statement 3 ("Yes" is wrong):** PaaS provides an application development and deployment environment (such as Azure App Service or Azure SQL Database) where developers build and deploy custom application code without managing the infrastructure. Azure Backup is not an application hosting/development platform; it is a turnkey data protection service (SaaS).

---

### 6. Exam Keyword / Trap Alert

* **Trap:** Community dumps frequently misclassify built-in management or data protection tools like Azure Backup or Azure Site Recovery as PaaS. Remember: if it is a pre-built, ready-to-consume service with no developer runtime or code deployment needed, Microsoft classifies it as **SaaS**.




## Q70

![Q70](/dump/question-images/q51-100/q70.png)



## Q71

![Q71](/dump/question-images/q51-100/q71.png)



## Q72

![Q72](/dump/question-images/q51-100/q72.png)



## Q73

![Q73](/dump/question-images/q51-100/q73.png)


## Q74 

![Q74](/dump/question-images/q51-100/q74.png)



## Q75

![Q75](/dump/question-images/q51-100/q75.png)

## Q76

![Q76](/dump/question-images/q51-100/q76.png)


## Q77

![Q77](/dump/question-images/q51-100/q77.png)


### 1. Extracted Question Summary

**Question 77:** What is the first stage in the Microsoft Cloud Adoption Framework for Azure?

* **A.** Adopt the cloud.


* **B.** Make a plan.


* **C.** Ready your organization.


* **D.** Define your strategy.



---

### 2. Correct Answer

**D: Define your strategy.**

---

### 3. Verification of Visible Selection / Community Key

**Correct.** The highlighted box and provided answer key designate **D**, which accurately represents the initial methodology stage of the Cloud Adoption Framework (CAF).

---

### 4. Official Microsoft Justification

The **Microsoft Cloud Adoption Framework for Azure (CAF)** provides structured guidance to create and implement business and technology strategies for cloud adoption. The framework structures the iterative lifecycle into distinct sequential phases:

1. **Strategy (Define strategy):** Clarify business motivations, documented expected business outcomes, establish financial models, and validate technical/business feasibility.


2. **Plan:** Align people, mapping digital estates, organizational alignment, and skills readiness.


3. **Ready:** Prepare the cloud environment using landing zones and foundational governance.


4. **Adopt:** Migrate workloads or innovate by building cloud-native solutions.



* Supported continuously throughout by **Govern** and **Manage** disciplines.



According to Microsoft Learn documentation for AZ-900 management and governance tools, cloud adoption begins with aligning business objectives and defining motivations before technical implementation or planning starts.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **A. Adopt the cloud:** This represents the execution phase (split into *Migrate* and *Innovate*), occurring only after strategy, planning, and landing zone readiness have been established.


* **B. Make a plan:** Planning (*Plan*) is the second stage, which translates motivations defined during the strategy stage into actionable adoption plans and digital estate assessments.


* **C. Ready your organization:** Readiness (*Ready*) is the third stage, focusing on preparing the landing zone and technical infrastructure in Azure.



---

### 6. Exam Keyword / Trap Alert

Look for **"first stage"** or **"initial step"** alongside **Cloud Adoption Framework (CAF)**. Microsoft exam questions test whether you recognize that business justification and motivations (**Strategy**) must always precede technical setup (**Ready**) or workload migration (**Adopt**).


Here is an overview and a visual architecture of the **Microsoft Cloud Adoption Framework (CAF) for Azure**.

---

### Cloud Adoption Framework (CAF) Lifecycle Diagram

```text
       ========================================================================
                                 BUSINESS ALIGNMENT
       ========================================================================
       +-------------------+       +-------------------+       +-------------------+
       |    1. STRATEGY    | ----> |     2. PLAN       | ----> |     3. READY      |
       |                   |       |                   |       |                   |
       | • Motivations     |       | • Digital estate  |       | • Azure setup     |
       | • Business value  |       | • Org alignment   |       | • Landing zones   |
       | • Financial model |       | • Skills readiness|       | • Best practices  |
       +-------------------+       +-------------------+       +-------------------+
                                                                         |
                                                                         v
       ========================================================================
                                 TECHNICAL IMPLEMENTATION
       ========================================================================
                                                           +-----------------------+
                                                           |       4. ADOPT        |
                                                           | --------------------- |
                                                           | Migrate   |  Innovate |
                                                           | (Lift &   |  (Cloud   |
                                                           |  Shift)   |   Native) |
                                                           +-----------------------+
                                                                         |
       ========================================================================
                             CROSS-CUTTING DISCIPLINES
       ========================================================================
       +-----------------------------------------------------------------------+
       |                              5. GOVERN                                |
       |        Corporate policy • Cost management • Security • Compliance      |
       +-----------------------------------------------------------------------+
       |                              6. MANAGE                                |
       |         Operations baseline • Business commitments • Service ops      |
       +-----------------------------------------------------------------------+

```

---

### Deep Dive into the CAF Methodologies

The Cloud Adoption Framework is Microsoft’s set of documentation, guidance, and best practices intended to help organizations create and implement business and technology strategies necessary to succeed in the cloud. It is divided into **sequential phases** supported by **ongoing baseline disciplines**:

#### 1. Define Strategy (Why are we moving?)

* **Core Focus:** Align business motivations with measurable outcomes.
* **Key Deliverables:**
* Establishing the **"Why"** (e.g., cost savings, market expansion, operational agility).
* Defining financial models (CapEx vs. OpEx, ROI, TCO).
* Validating business justifications with key stakeholders.



#### 2. Plan (How will we organize?)

* **Core Focus:** Translating business goals into an actionable technical roadmap.
* **Key Deliverables:**
* **Digital Estate Assessment:** Inventorying existing on-premises servers, VMs, databases, and apps.
* **Organizational Alignment:** Establishing cloud governance teams, cloud centers of excellence (CCoE), and project owners.
* **Cloud Adoption Plan & Skills Readiness:** Identifying training needs for staff.



#### 3. Ready (Where will workloads live?)

* **Core Focus:** Preparing the cloud environment to host workloads securely and compliantly.
* **Key Deliverables:**
* **Azure Landing Zones:** Pre-configured environments with networking, identity, logging, and security boundaries.
* Subscription organization, resource group conventions, and core networking topology (e.g., Hub-and-Spoke).



#### 4. Adopt (The actual transformation)

* **Core Focus:** Moving or building systems in Azure. This breaks down into two paths:
* **Migrate:** Rehosting (lift-and-shift), refactoring, or re-architecting existing workloads using tools like *Azure Migrate*.
* **Innovate:** Building cloud-native applications, utilizing microservices (AKS, Container Apps), AI/ML, and serverless architectures (Azure Functions).



---

### The Continuous Disciplines (Govern & Manage)

Unlike the sequential stages above, **Govern** and **Manage** run continuously across every stage:

* **Govern:**
* Enforces compliance, security postures, naming conventions, and budget thresholds.
* Implemented using tools like **Azure Policy**, **Azure Blueprints / Template Specs**, and **Microsoft Defender for Cloud**.


* **Manage:**
* Ensures operational reliability once workloads are in production.
* Covers backup/disaster recovery (**Azure Backup**, **Azure Site Recovery**), monitoring (**Azure Monitor**, **Log Analytics**), and SLA tracking.



---

### Quick AZ-900 Exam Takeaways

* **Strategy always precedes Ready/Plan:** If an exam question asks what happens before touching Azure tools or building landing zones, the answer is always **Define Strategy**.
* **Ready = Landing Zones:** Whenever a scenario mentions establishing the foundation, baseline subscriptions, or landing zones, think of the **Ready** phase.
* **Govern & Manage are transversal:** They do not belong to a single step; they span the entire cloud lifecycle.



## Q78

![Q78](/dump/question-images/q51-100/q78.png)


## Q79

![Q79](/dump/question-images/q51-100/q79.png)

## Q80

![Q80](/dump/question-images/q51-100/q80.png)


## Q81
![Q81](/dump/question-images/q51-100/q81.png)

### 1. Extracted Question Summary

**Question 81 (HOTSPOT):**

Select the answer that correctly completes the sentence.

* **Sentence:** "Azure Site Recovery provides [ drop-down ] for virtual machines"


* **Drop-down Options:**
* fault tolerance


* disaster recovery


* elasticity


* high availability





---

### 2. Correct Answer

**disaster recovery**

* Completed sentence: "Azure Site Recovery provides **disaster recovery** for virtual machines."



---

### 3. Verification of Visible Selection / Community Key

**Correct.** The option highlighted inside the red rectangle in the screenshot is **disaster recovery**, which matches Microsoft's official classification of Azure Site Recovery (ASR).

---

### 4. Official Microsoft Justification

**Azure Site Recovery (ASR)** is a native **Disaster Recovery as a Service (DRaaS)** solution in Azure. It coordinates the replication, failover, and failback of workloads running on physical machines or virtual machines (Azure VMs, on-premises Hyper-V, and VMware) to a secondary location (e.g., another Azure region or secondary datacenter). Its primary function is to maintain business continuity and minimize Recovery Time Objective (RTO) and Recovery Point Objective (RPO) during catastrophic events or regional outages.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **fault tolerance:** Refers to the architectural capability of a system to continue operating without interruption even if one or more hardware/software components fail (e.g., redundant power supplies, RAID, or multi-node clustering), which is an inherent hardware/platform architectural property rather than a replication/failover service like ASR.


* **elasticity:** Refers to the dynamic ability to automatically scale computing resources up or down in response to real-time workload fluctuations (e.g., Virtual Machine Scale Sets).


* **high availability:** Refers to designing systems with minimal downtime during normal operations within a region or datacenter (achieved via Availability Sets, Availability Zones, and load balancers), whereas disaster recovery specifically addresses surviving full site-level or regional failures via secondary location failover.



---

### 6. Exam Keyword / Trap Alert

Associate **Site Recovery (ASR)** directly with **Disaster Recovery (DR)** and **business continuity / regional failover**. Do not confuse it with **Azure Backup** (which handles point-in-time data backup and restoration) or **Availability Zones** (which provide **High Availability** within a region).


## Q82

![Q82](/dump/question-images/q51-100/q82.png)



## Q83

![Q83](/dump/question-images/q51-100/q83.png)



## Q84

![Q84](/dump/question-images/q51-100/q84.png)


## Q85

![Q85](/dump/question-images/q51-100/q85.png)


## Q86

![Q86](/dump/question-images/q51-100/q86.png)


## Q87

![Q87](/dump/question-images/q51-100/q87.png)



## Q88

![Q88](/dump/question-images/q51-100/q88.png)



## Q89

![Q89](/dump/question-images/q51-100/q89.png)


## Q90

![Q90](/dump/question-images/q51-100/q90.png)



## Q91

![Q91](/dump/question-images/q51-100/q91.png)



## Q92

![Q92](/dump/question-images/q51-100/q92.png)


## Q93

![Q93](/dump/question-images/q51-100/q93.png)



## Q94

![Q94](/dump/question-images/q51-100/q94.png)



## Q95

![Q95](/dump/question-images/q51-100/q95.png)



## Q96

![Q96](/dump/question-images/q51-100/q96.png)



## Q97

![Q97](/dump/question-images/q51-100/q97.png)

### 1. Extracted Question Summary

**Question 97 (HOTSPOT):**

You plan to extend your company's network to Azure.

The network contains a VPN appliance that uses an IP address of `131.107.200.1`.

You need to create an Azure resource that defines the VPN appliance in Azure.

Which Azure resource should you create? To answer, select the appropriate resource in the answer area.

**Available Options (Services):**

* NAT gateways


* Application gateways


* Local network gateways


* Virtual network gateways


* On-premises Data Gateways


* Azure Data Box Gateway


* Azure Stack Edge / Data Box Gateway


* Web Application Firewall policies



---

### 2. Correct Answer

**Local network gateways**

---

### 3. Verification of Visible Selection / Community Key

*(No specific option is highlighted or selected in the screenshot.)*

---

### 4. Official Microsoft Justification

In a Site-to-Site (S2S) VPN setup connecting an on-premises network to an Azure Virtual Network:

* The **Local Network Gateway** is the Azure resource that represents and defines your on-premises edge device (the VPN appliance). It holds the on-premises VPN device's public IP address (such as `131.107.200.1`) and the on-premises IP address prefixes that will be routed across the tunnel.


* The **Virtual Network Gateway** (VPN type) represents the software VPN router deployed inside an Azure VNet's dedicated `GatewaySubnet`.
* When configuring the connection, Azure links the **Virtual Network Gateway** (the Azure end) to the **Local Network Gateway** (the on-premises appliance end).

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Virtual network gateways:** Represents the gateway deployed *inside* your Azure virtual network, not the resource that defines the external/on-premises VPN appliance.


* **NAT gateways:** Provides outbound-only internet connectivity for virtual network subnets without accepting inbound connections; does not establish VPN tunnels.


* **Application gateways:** A Layer 7 (HTTP/HTTPS) reverse proxy and load balancer, not a network-level VPN appliance representation.


* **On-premises Data Gateways:** A bridge used by Power BI, Power Apps, and Azure Logic Apps to query on-premises data sources (like SQL Server) without exposing them to the public internet, rather than a network VPN endpoint.


* **Azure Data Box Gateway / Azure Stack Edge:** Storage appliance solutions for transferring data to Azure Storage over the network, unrelated to network-level VPN definitions.


* **Web Application Firewall policies:** Security rule sets for inspecting HTTP/HTTPS traffic on Layer 7 resources (like Azure Front Door or Application Gateway).



---

### 6. Exam Keyword / Trap Alert

* **"Defines/represents the on-premises VPN appliance or edge device"** $\rightarrow$ **Local Network Gateway**


* **"Azure endpoint / Azure gateway deployed in GatewaySubnet"** $\rightarrow$ **Virtual Network Gateway**



Connecting an on-premises network to Azure via a VPN appliance involves setting up an IPsec/IKE Site-to-Site (S2S) VPN. This requires configuring specific Azure resources to represent both sides of the link and establishing the tunnel on the physical/virtual on-premises appliance.

---

### High-Level Architecture

```text
[ On-Premises Network ]
        |
  (Subnet: 192.168.1.0/24)
        |
[ On-Premises VPN Appliance ] (Public IP: 131.107.200.1)
        |
        |======= Encrypted IPsec / IKE Tunnel (Internet) =======
        |
[ Azure VNet Gateway ] (GatewaySubnet: 10.0.255.0/27)
        |
  (Subnet: 10.0.1.0/24)
        |
[ Azure Virtual Network ]

```

---

### Step-by-Step Implementation

#### Phase 1: Azure-Side Configuration

1. **Create the Virtual Network (VNet) and `GatewaySubnet`:**
* Within the target VNet (e.g., address space `10.0.0.0/16`), create a dedicated subnet named strictly **`GatewaySubnet`**.
* Azure requires this exact name for deploying gateway infrastructure. A prefix of `/27` or `/28` is typically recommended.


2. **Deploy the Virtual Network Gateway:**
* **Gateway type:** Select **VPN**.
* **VPN type:** Select **Route-based** (supported by most modern hardware firewalls and required for features like BGP and dynamic routing).
* **SKU:** Select based on throughput and tunnel requirements (e.g., `VpnGw1`, `VpnGw2`).
* **Virtual network:** Associate it with the VNet prepared in Step 1.
* **Public IP address:** Create or select a Standard Public IP resource for the gateway. Azure assigns an external IP to this endpoint once provisioning completes (note: provisioning typically takes 20 to 45 minutes).


3. **Create the Local Network Gateway:**
* This resource tells Azure about the on-premises environment:
* **IP address / FQDN:** Enter the public-facing static IP of the on-premises VPN appliance (e.g., `131.107.200.1`).
* **Address Space(s):** Specify the internal on-premises IP subnets (e.g., `192.168.1.0/24`) that need to route to Azure.




4. **Create the Connection Resource:**
* In Azure, navigate to the **Virtual Network Gateway** $\rightarrow$ **Connections** $\rightarrow$ **Add**.
* **Connection type:** Select **Site-to-site (IPsec)**.
* **Virtual network gateway:** Select the gateway created in Step 2.
* **Local network gateway:** Select the resource created in Step 3.
* **Shared Key (PSK):** Enter an alphanumeric pre-shared key (this must match identically on the on-premises appliance).
* **IKE Protocol:** Select **IKEv2**.



---

### Phase 2: On-Premises Appliance Configuration

On the edge device (e.g., Fortinet, Cisco ASA/ISR, Palo Alto, pfSense, or Windows Server RRAS):

1. **Define the Remote Gateway (Azure):**
* Configure the remote peer using the public IP address allocated to the Azure Virtual Network Gateway.


2. **Phase 1 IPsec Parameters (IKE SA):**
* **Version:** IKEv2.
* **Authentication:** Pre-Shared Key (enter the exact key defined in the Azure Connection).
* **Encryption / Integrity:** Standard suites such as AES-256 with SHA-256.
* **Diffie-Hellman (DH) Group:** Group 14 (2048-bit) or Group 24.
* **SA Lifetime:** Typically 28,800 seconds (8 hours).


3. **Phase 2 IPsec Parameters (IPsec SA):**
* **Encryption / Hash:** AES-256 with SHA-256.
* **PFS (Perfect Forward Secrecy):** Enabled (e.g., Group 14 or None, matching policy).
* **Traffic Selectors / Cryptomap:**
* *Local Subnets:* On-premises CIDR block (e.g., `192.168.1.0/24`).
* *Remote Subnets:* Azure VNet CIDR block (e.g., `10.0.0.0/16`).


* **SA Lifetime:** Typically 3,600 seconds (1 hour).


4. **Firewall Access Rules & NAT:**
* **Open Outer Ports (Edge):** Ensure the perimeter allows inbound/outbound **UDP 500** (IKE) and **UDP 4500** (NAT-T), as well as IP Protocol **50 (ESP)**.
* **Bypass NAT / NAT Exemption:** Create a NAT exemption (no-NAT) rule for traffic passing between internal subnets and the Azure VNet subnets so packet headers preserve their original private IPs.



---

### Phase 3: Verification & Routing

1. **Check Azure Status:**
* In the Azure Portal, open the **Connection** resource. Once the tunnel negotiates successfully, the status changes from **Connecting** to **Connected**.


2. **Ping / Traceroute Validation:**
* From an on-premises machine, run a ping or TCP port test to an Azure VM's private IP.
* Verify that Network Security Groups (NSGs) attached to Azure VM subnets permit incoming traffic from the on-premises CIDR block on required ports.



## Q98

![Q98](/dump/question-images/q51-100/q98.png)

### 1. Extracted Question Summary

**Question 98 (Repeated Scenario / Yes-No Series):**

You plan to deploy several Azure virtual machines.

You need to **ensure that the services running on the virtual machines are available if a single data center fails**.

**Solution:** You deploy the virtual machines to two or more resource groups.

**Does this meet the goal?**

* **A.** Yes


* **B.** No



---

### 2. Correct Answer

**B: No**

---

### 3. Verification of Visible Selection / Community Key

**Correct.** The red box highlights **B. No**, which accurately reflects that resource groups do not provide physical fault isolation or high availability.

---

### 4. Official Microsoft Justification

* A **Resource Group** is strictly a **logical container** used for lifecycle management, billing, role-based access control (RBAC), and organizing Azure resources. It has no physical boundaries and does not influence where the actual hardware or virtual machine hosts are located.
* To protect workloads against a **single datacenter failure**, virtual machines must be distributed across two or more **Availability Zones** within an Azure region. Each Availability Zone consists of one or more physically separate datacenters with independent power, cooling, and networking infrastructure.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **A. Yes:** Incorrect because distributing VMs across multiple resource groups does not separate their underlying physical hardware. All resource groups and their contained VMs could reside on physical racks within the exact same datacenter; if that datacenter fails, all VMs fail regardless of resource group allocation.

---

### 6. Exam Keyword / Trap Alert

* **"Available if a single data center fails"** always points to **Availability Zones** (or deploying to separate regions).


* **Resource Groups** are solely **logical boundaries**; they never provide redundancy, fault tolerance, or high availability.



## Q99

![Q99](/dump/question-images/q51-100/q99.png)



## Q100

![Q100](/dump/question-images/q51-100/q100.png)

### 1. Extracted Question Summary

**Question 100 (HOTSPOT):**

For each of the following statements, select **Yes** if the statement is true. Otherwise, select **No**.

Note: The question references Azure Active Directory (Azure AD), now known as Microsoft Entra ID.

* **Statement 1:** An Azure subscription can be associated to multiple Azure Active Directory (Azure AD) tenants.


* **Statement 2:** You can change the Azure Active Directory (Azure AD) tenant to which an Azure subscription is associated.


* **Statement 3:** When an Azure subscription expires, the associated Azure Active Directory (Azure AD) tenant is deleted automatically.



---

### 2. Correct Answer

* **An Azure subscription can be associated to multiple Azure Active Directory (Azure AD) tenants:** **No**
* **You can change the Azure Active Directory (Azure AD) tenant to which an Azure subscription is associated:** **Yes**
* **When an Azure subscription expires, the associated Azure Active Directory (Azure AD) tenant is deleted automatically:** **No**

---

### 3. Verification of Visible Selection / Community Key

(No selections or answers are marked in the uploaded screenshot; all radio buttons are unselected.)

---

### 4. Official Microsoft Justification

* **Statement 1 (No):** In the trust hierarchy between subscriptions and directories, an Azure subscription trusts **only one** Microsoft Entra ID (Azure AD) tenant at any given time. Conversely, a single directory tenant can trust and manage multiple subscriptions (a 1:N tenant-to-subscription relationship).
* **Statement 2 (Yes):** An administrator can change the directory associated with an Azure subscription by transferring or re-associating the subscription to another tenant using the **Change directory** function in the Azure portal, provided they have appropriate administrative privileges (e.g., Subscription Owner).
* **Statement 3 (No):** Subscriptions and Microsoft Entra ID tenants have separate, independent lifecycles. A tenant is an identity container that can host users, groups, application registrations, and multiple other subscriptions (or Microsoft 365 services). When an individual subscription expires or is canceled, only the resources within that subscription are affected; the directory tenant itself remains intact.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **If Statement 1 were "Yes":** This confuses the relationship direction. Multiple subscriptions can associate with one tenant, but a subscription cannot simultaneously associate with multiple tenants.
* **If Statement 2 were "No":** This overlooks the native "Change directory" administrative feature used during mergers, acquisitions, or restructuring.
* **If Statement 3 were "Yes":** This incorrectly treats the directory as a child of the subscription. The tenant exists independently at the root identity layer, above the subscription.

---

### 6. Exam Keyword / Trap Alert

* **Relationship rule:** Tenant-to-Subscription is **One-to-Many ($1:N$)**, never Many-to-Many.
* **Lifecycle independence:** A subscription cancellation **never deletes** the directory/tenant.



## Q101

![Q101](/dump/question-images/q101-150/q101.png)


### 1. Extracted Question Summary

**Question 101:**

This question requires that you evaluate the underlined text to determine if it is correct.

"Resource groups provide organizations with the ability to manage the compliance of Azure resources across multiple subscriptions."

Instructions: Review the underlined text. If it makes the statement correct, select `No change is needed`. If the statement is incorrect, select the answer choice that makes the statement correct.

* **A.** No change is needed


* **B.** Management groups


* **C.** Azure policies


* **D.** Azure App Service plans



---

### 2. Correct Answer

**B: Management groups**

---

### 3. Verification of Visible Selection / Community Key

**Correct.** The visible answer key at the bottom begins with **B**, which correctly identifies that **Management groups** provide governance and compliance management across multiple subscriptions.

---

### 4. Official Microsoft Justification

In the Azure resource management hierarchy:


$$\text{Management Groups} \longrightarrow \text{Subscriptions} \longrightarrow \text{Resource Groups} \longrightarrow \text{Resources}$$

* **Management Groups** are containers positioned above subscriptions to manage access, policy, and compliance across **multiple subscriptions** efficiently.
* Governance conditions (such as Azure Policy assignments and Azure RBAC roles) applied at the management group level automatically inherit downward to all subscriptions and child resources within that management group hierarchy.
* A resource group exists strictly *inside* a single subscription and cannot span across or govern multiple subscriptions.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **A. No change is needed:** Incorrect because a **Resource Group** is scoped strictly to a single subscription; it cannot manage resources or compliance across multiple subscriptions.


* **C. Azure policies:** While Azure Policy evaluates compliance, policies are rule definitions and assignments that must be targeted to a scope (such as a management group, subscription, or resource group). The sentence tests the organizational container structure that enables centralized governance across multiple subscriptions (Management groups).


* **D. Azure App Service plans:** Represents the underlying compute infrastructure (VM instances, CPU, memory, pricing tier) used to host Azure Web Apps and API apps; it has no governance or compliance function.



---

### 6. Exam Keyword / Trap Alert

Whenever you see the exact phrase **"across multiple subscriptions"** in governance questions, the answer is almost always **Management groups**. Remember the hierarchy order: Management groups contain subscriptions, and subscriptions contain resource groups.




## Q102

![Q102](/dump/question-images/q101-150/q102.png)

### 1. Extracted Question Summary

**Question 102:**

Your company plans to migrate to Azure.

The company has several departments. All the Azure resources used by each department will be managed by a department administrator.

What are two possible techniques to segment Azure for the departments? Each correct answer presents a complete solution.

NOTE: Each correct selection is worth one point.

* **A.** multiple subscriptions


* **B.** multiple Azure Active Directory (Azure AD) directories


* **C.** multiple regions


* **D.** multiple resource groups



---

### 2. Correct Answer

* **A: multiple subscriptions**


* **D: multiple resource groups**



---

### 3. Verification of Visible Selection / Community Key

**Correct.** The visible boxes in the screenshot select **A (multiple subscriptions)** and **D (multiple resource groups)**, which accurately represent the two standard management and administrative boundary scopes in Azure.

---

### 4. Official Microsoft Justification

In Azure governance and Role-Based Access Control (Azure RBAC), administrative boundaries can be established at different levels in the resource hierarchy:

* **Subscriptions (A):** An Azure subscription serves as both a billing boundary and an access/administrative boundary. Assigning a dedicated subscription to each department allows the department administrator to have full administrative permissions (such as Owner or Contributor) scoped solely to their department's workloads.
* **Resource Groups (D):** A resource group is a logical container for resources deployed within a subscription. Azure RBAC allows permissions to be assigned directly at the resource group scope, granting department administrators management rights over only their department's resource group without granting access to other groups.

Both approaches provide complete isolation of administrative control per department.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **B. multiple Azure Active Directory (Azure AD / Microsoft Entra ID) directories:** Creating multiple tenant directories fragments identity management, user accounts, and enterprise Single Sign-On (SSO). Organizations typically maintain a single directory tenant and delegate administration within it using RBAC, rather than creating separate tenants for departments.


* **C. multiple regions:** Azure regions are geographic locations for deploying resources to ensure low latency and high availability. Regions do not serve as administrative, security, or RBAC delegation boundaries.



---

### 6. Exam Keyword / Trap Alert

When a question asks how to **segment resources for administrative control / delegation**, look for standard RBAC hierarchy scopes: **Management Groups**, **Subscriptions**, or **Resource Groups**. Do not select geographic components (regions) or separate identity tenants (Entra ID / Azure AD directories) for department segmentation.



## Q103

![Q103](/dump/question-images/q101-150/q103.png)

### 1. Extracted Question Summary

**Question 103 (HOTSPOT):**

For each of the following statements, select **Yes** if the statement is true. Otherwise, select **No**.

NOTE: Each correct selection is worth one point.

* **Statement 1:** A single Microsoft account can be used to manage multiple Azure subscriptions.


* **Statement 2:** Two Azure subscriptions can be merged into a single subscription.


* **Statement 3:** A company can use resources from multiple subscriptions.



---

### 2. Correct Answer

* **A single Microsoft account can be used to manage multiple Azure subscriptions:** **Yes**
* **Two Azure subscriptions can be merged into a single subscription:** **No**
* **A company can use resources from multiple subscriptions:** **Yes**

---

### 3. Verification of Visible Selection / Community Key

**Correct.** The visible selections in the screenshot mark:

* Statement 1: **Yes**


* Statement 2: **No**


* Statement 3: **Yes**


All three selections accurately reflect Microsoft Azure subscription architecture and lifecycle rules.

---

### 4. Official Microsoft Justification

* **Statement 1 (Yes):** An identity (whether a personal Microsoft Account [MSA] or a Microsoft Entra ID organizational work/school account) can be granted administrative or RBAC roles (such as Owner, Contributor, or Reader) across multiple independent Azure subscriptions. When signing in to the Azure Portal, that user account can switch between and manage all associated subscriptions.


* **Statement 2 (No):** In Azure, subscriptions are distinct billing, identity boundary, and quota containers. You cannot merge or combine two Azure subscriptions into one. While you can move resources individually or in bulk from one subscription to another, the subscriptions themselves remain separate entities and cannot be merged.


* **Statement 3 (Yes):** An enterprise organization typically deploys a multi-subscription topology (e.g., separating Production, Development, Testing, or different departments) structured under Management Groups. Workloads and users within the company routinely utilize and interact with resources residing across multiple subscriptions (for example, peering virtual networks across subscriptions or consuming shared services).



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **If Statement 1 were "No":** This would imply a 1:1 limit between an administrator identity and a subscription, which is incorrect. A single account can manage many subscriptions simultaneously.


* **If Statement 2 were "Yes":** This confuses **moving resources between subscriptions** with **merging subscriptions**. Subscriptions cannot be fused together; consolidating workloads requires migrating resources to the destination subscription and canceling/deleting the empty source subscription.


* **If Statement 3 were "No":** This would falsely assume an organization is strictly limited to deploying and consuming resources within a single subscription boundary, contradicting the Cloud Adoption Framework enterprise landing zone recommendations.



---

### 6. Exam Keyword / Trap Alert

* **"Merged into a single subscription"** is always **No / False** in Azure exams. Azure supports **resource movement** (`az resource move`), but **subscription merging does not exist**.




## Q104

![Q104](/dump/question-images/q101-150/q104.png)


## Q105

![Q105](/dump/question-images/q101-150/q105.png)


## Q106

![Q106](/dump/question-images/q101-150/q106.png)


## Q107

![Q107](/dump/question-images/q101-150/q107.png)

### 1. Extracted Question Summary

**Question 107 (HOTSPOT):**

For each of the following statements, select **Yes** if the statement is true. Otherwise, select **No**.

NOTE: Each correct selection is worth one point.

* **Statement 1:** Each Azure subscription can contain multiple account administrators.


* **Statement 2:** Each Azure subscription can be managed by using a Microsoft account only.


* **Statement 3:** An Azure resource group contains multiple Azure subscriptions.



---

### 2. Correct Answer

* **Each Azure subscription can contain multiple account administrators:** **No**
* **Each Azure subscription can be managed by using a Microsoft account only:** **No**
* **An Azure resource group contains multiple Azure subscriptions:** **No**

---

### 3. Verification of Visible Selection / Community Key

(No selections or answers are marked in the uploaded screenshot; all radio buttons are unselected.)

---

### 4. Official Microsoft Justification

* **Statement 1 (No):** In classic subscription management and Azure billing hierarchy, an Azure subscription can have **only one Account Administrator** (the identity responsible for billing ownership and the primary subscription account). While multiple users can be assigned the modern Azure RBAC **Owner** role or classic **Co-Administrator** role, the dedicated **Account Administrator** role is strictly limited to one identity per subscription.
* **Statement 2 (No):** Azure subscriptions can be managed by both personal **Microsoft accounts (MSA)** (e.g., `@outlook.com`, `@live.com`) and enterprise organizational/work accounts backed by **Microsoft Entra ID** (formerly Azure AD). Management is not restricted to personal Microsoft accounts *only*.
* **Statement 3 (No):** In the Azure resource management hierarchy:

$$\text{Management Groups} \longrightarrow \text{Subscriptions} \longrightarrow \text{Resource Groups} \longrightarrow \text{Resources}$$



A subscription contains resource groups, **not** the other way around. A resource group exists strictly inside a single subscription and cannot contain or span subscriptions.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **If Statement 1 were "Yes":** This confuses the modern RBAC **Owner** role (which can have multiple assignees) with the classic/billing **Account Administrator** role (which is strictly 1 per subscription).
* **If Statement 2 were "Yes":** This disregards the standard enterprise model where subscriptions are managed via Microsoft Entra ID corporate/organizational accounts.
* **If Statement 3 were "Yes":** This reverses the core ARM hierarchy order. Subscriptions contain resource groups; resource groups never contain subscriptions.

---

### 6. Exam Keyword / Trap Alert

* **"Account Administrator" vs. "Owner":** Only **1** Account Administrator per subscription; multiple Owners are allowed via RBAC.
* Watch for the restrictive word **"only"** in account statements: subscriptions support both **Microsoft Accounts (MSA)** and **Microsoft Entra ID** work/school accounts.



## Q108

![Q108](/dump/question-images/q101-150/q108.png)

### 1. Extracted Question Summary

**Question 108 (HOTSPOT):**

For each of the following statements, select **Yes** if the statement is true. Otherwise, select **No**.

NOTE: Each correct selection is worth one point.

* **Statement 1:** Availability zones can be implemented in all Azure regions.


* **Statement 2:** Only virtual machines that run Windows Server can be created in availability zones.


* **Statement 3:** Availability zones are used to replicate data and applications to multiple regions.



---

### 2. Correct Answer

* **Availability zones can be implemented in all Azure regions:** **No**
* **Only virtual machines that run Windows Server can be created in availability zones:** **No**
* **Availability zones are used to replicate data and applications to multiple regions:** **No**

---

### 3. Verification of Visible Selection / Community Key

(No selections or answers are marked in the uploaded screenshot; all radio buttons are unselected.)

---

### 4. Official Microsoft Justification

* **Statement 1 (No):** Availability Zones are not available in every Azure region. While Microsoft has built zones across all major flagship geographies, some smaller, legacy, specialized, or sovereign regions (e.g., certain government regions or emerging data center locations) do not have multiple physical zones.
* **Statement 2 (No):** Availability Zones are platform-level infrastructure constructs and are completely agnostic to the guest operating system. You can deploy Linux virtual machines (Ubuntu, Red Hat, Debian, SUSE, etc.) into Availability Zones just as easily as Windows Server virtual machines.
* **Statement 3 (No):** Availability Zones exist **within a single Azure region**. They provide resiliency and redundancy against data center failures *inside* that specific region. Replicating data and workloads across **multiple regions** is handled by cross-region services, Azure Region Pairs, or Geo-redundant storage (GRS), not by Availability Zones.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **If Statement 1 were "Yes":** This assumes universal parity across all global geographies. In Azure architecture, availability of features—including zones—varies by region type.
* **If Statement 2 were "Yes":** This introduces an arbitrary OS restriction. Microsoft Azure does not limit high-availability infrastructure features like zones or availability sets to Windows Server workloads.
* **If Statement 3 were "Yes":** This confuses **intra-region** redundancy with **inter-region / cross-region** redundancy. Availability Zones operate strictly within local regional latency boundaries ($<2\text{ ms}$).

---

### 6. Exam Keyword / Trap Alert

* Watch for absolute terms like **"all Azure regions"** and **"Only Windows Server"**—these are almost always false.


* **Availability Zones = within a single region (intra-region)**.


* **Replication across multiple regions = Region Pairs / Cross-region / Geo-redundant (inter-region)**.



## Q109

![Q109](/dump/question-images/q101-150/q109.png)

### 1. Extracted Question Summary

**Question 109 (HOTSPOT):**

You plan to create an Azure virtual machine.

You need to identify which storage service must be used to store the unmanaged data disks of the virtual machine.

What should you identify? To answer, select the appropriate service in the answer area.

**Available Options (Storage Services shown in Answer Area):**

* **Containers** (Scalable, cost-effective storage for unstructured data)


* **File shares** (Serverless SMB file shares)


* **Tables** (Tabular data storage)


* **Queues** (Effectively scale apps according to traffic)



---

### 2. Correct Answer

**Containers** (Azure Blob Storage)

---

### 3. Verification of Visible Selection / Community Key

*(No selections or answers are marked in the uploaded screenshot; all option cards are unselected.)*

---

### 4. Official Microsoft Justification

* Unmanaged disks in Azure are stored as **Page Blobs** (`.vhd` files) inside a user-managed **Azure Storage Account** container.


* While modern architectures strongly recommend **Managed Disks** (where Azure automatically provisions and manages the underlying storage account), **unmanaged disks** require the customer to create an Azure Storage Account and store the VHD files inside a **Blob Container**.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **File shares:** Provides managed SMB/NFS file shares for mounting across multiple virtual machines or on-premises systems simultaneously; it does not host virtual machine unmanaged VHD disks.


* **Tables:** A NoSQL key-value datastore for schemaless, structured datasets; it cannot store binary disk images.


* **Queues:** A messaging store for asynchronous message queuing between decoupled application components, having no capability to store disk images.



---

### 6. Exam Keyword / Trap Alert

* Whenever AZ-900 references **"unmanaged disks"** or **"VHD storage"**, the answer is always **Containers / Blob storage (specifically page blobs)**.


* Contrast this with **Azure Files**, which is signaled by keywords like **"shared file system"**, **"SMB / NFS"**, or **"lift-and-shift file servers"**.


The distinction between **Managed Disks** and **Unmanaged Disks** comes down to **who owns and administrates the underlying Azure Storage Account**.

---

### What Does "Managed" Actually Mean?

In cloud infrastructure, "managed" means the cloud provider abstracts and handles the underlying administrative, scaling, and hardware lifecycle tasks:

* **Unmanaged Disks (You manage the container and account):**
* The disk is simply a standard Virtual Hard Disk (`.vhd`) file stored as a **Page Blob** inside a regular Azure Storage Account that **you** create and maintain.
* You are responsible for storage account limits, scaling boundaries, security keys, and distributing disks across different accounts to prevent IOPS bottlenecks.


* **Managed Disks (Azure manages the infrastructure):**
* The disk is a first-class Azure Resource (`Microsoft.Compute/disks`).
* Behind the scenes, Azure creates, secures, and maintains the storage fabric. You never see, configure, or manage a storage account. You simply specify the disk type, disk size (GiB), and performance tier, and Azure handles the rest.



---

### Core Architectural Differences

| Feature | Managed Disks (Modern Standard) | Unmanaged Disks (Legacy) |
| --- | --- | --- |
| **Azure Resource Type** | `Microsoft.Compute/disks` | Page Blob inside `Microsoft.Storage/storageAccounts` |
| **Storage Account Needed?** | **No** (Fully abstracted by Azure) | **Yes** (Customer must provision and manage it) |
| **IOPS / Throttling Risk** | Dedicated performance per disk; no shared account limits | Max 20,000 IOPS per standard storage account (noisy neighbors) |
| **Availability Zone Support** | Native support (ZRS disks, cross-zone distribution) | No native Availability Zone integration |
| **Availability Set Alignment** | Disks automatically align with VM Fault Domains | Disks can land on the same storage cluster (Single Point of Failure) |
| **Snapshots & Images** | First-class ARM resources with incremental snapshots | Manual blob copies using AzCopy or REST API |
| **Role-Based Access (RBAC)** | Granular access per individual disk | Access scoped to the entire storage account or container |

---

### Why Unmanaged Disks Were Problematic

1. **Storage Account IOPS Limits:**
A standard Azure Storage Account has a shared throughput ceiling (typically 20,000 IOPS). If you placed several active VM `.vhd` files in the same storage account, a single high-traffic database disk could saturate the entire account and throttle neighboring VMs.
2. **Availability Set Failure Risk:**
When placing VMs in an Availability Set across different hardware racks (Fault Domains), unmanaged disks could still end up stored on the **same physical storage cluster**. If that storage rack failed, all VMs went offline simultaneously, defeating the purpose of the Availability Set. Managed Disks eliminate this by aligning disk storage with the VM's compute fault domain automatically.

---

### How to Provision Each

#### 1. Managed Disks (Recommended Default)

You can provision a managed disk directly through the CLI, Portal, or ARM/Bicep template without creating a storage account:

```bash
az disk create \
  --resource-group rg-workloads \
  --name disk-data-01 \
  --size-gb 128 \
  --sku Premium_LRS

```

Or attach it directly during VM creation:

```bash
az vm create \
  --resource-group rg-workloads \
  --name vm-app-01 \
  --image Ubuntu2204 \
  --data-disk-sizes-gb 128

```

#### 2. Unmanaged Disks (Legacy Workflow)

Provisioning an unmanaged disk requires a multi-step workflow:

1. Create a general-purpose **Azure Storage Account**.
2. Create a **Blob Container** (e.g., named `vhds`).
3. Deploy the VM using legacy ARM properties or scripts specifying the full Blob URI (e.g., `[https://mystorageacct.blob.core.windows.net/vhds/disk1.vhd](https://mystorageacct.blob.core.windows.net/vhds/disk1.vhd)`) as a Page Blob.

---

### When Should You Use Each?

#### Use **Managed Disks** for:

* **Virtually all new deployments:** This has been Microsoft's official best practice since 2017.
* **Production Enterprise Workloads:** Essential for High Availability (Availability Sets and Availability Zones).
* **High I/O Performance:** When using Premium SSD, Premium SSD v2, or Ultra Disks.
* **Security & Compliance:** Simplified disk encryption (Azure Disk Encryption, Customer-Managed Keys / CMK) and granular RBAC delegation.

#### Use **Unmanaged Disks** only for:

* **Legacy Archival / Retrofitting:** Rare legacy automation scripts or custom deployment systems that depend directly on raw VHD blob URLs.
* **Custom On-Premises VHD Staging:** Temporarily uploading raw `.vhd` images from on-premises environments before converting them to Managed Disks or Azure Compute Gallery images.
* **Direct Blob Manipulation:** Obsolete scenarios requiring direct byte-level manipulation of a VHD file through Blob storage APIs without mounting it to a VM.

---

### AZ-900 Exam Takeaways

* If a question asks what storage service backs **unmanaged disks**, the answer is always **Blob Storage / Containers (Page Blobs)**.
* If a question asks how to simplify storage management, improve fault tolerance in Availability Sets, or eliminate storage account limits for VMs, the answer is always **Managed Disks**.




## Q110

![Q110](/dump/question-images/q101-150/q110.png)


## Q111

![Q111](/dump/question-images/q101-150/q111.png)


## Q112

![Q112](/dump/question-images/q101-150/q112.png)



### 1. Extracted Question Summary

**Question 112 (HOTSPOT):**

You plan to implement an Azure database solution.

You need to implement a database solution that meets the following requirements:

* Can add data concurrently from multiple regions


* Can store JSON documents



Which database service should you deploy? To answer, select the appropriate service in the answer area.

**Available Options (DATABASES):**

* Azure Cosmos DB


* SQL databases


* Azure Database for MySQL servers


* Azure Database for PostgreSQL servers


* Azure Database for MariaDB servers


* SQL servers


* SQL Data warehouses


* Azure Database Migration Services


* Azure Cache for Redis


* SQL Server stretch databases


* Data factories


* SQL elastic pools


* Virtual Clusters


* Managed databases


* Elastic Job agents


* SQL managed instances



---

### 2. Correct Answer

**Azure Cosmos DB**

---

### 3. Verification of Visible Selection / Community Key

*(No options are highlighted or selected in the uploaded screenshot; the list of database services is unselected.)*

---

### 4. Official Microsoft Justification

* **Azure Cosmos DB** is Microsoft's globally distributed, multi-model NoSQL database service designed for high availability and low latency.
* It natively supports **multi-region writes** (allowing applications to write and add data concurrently across multiple Azure regions with automatic conflict resolution).


* It natively stores semi-structured data as **JSON documents** via its core NoSQL API (formerly SQL API).



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **SQL databases / SQL managed instances / SQL servers:** Relational database management systems (RDBMS) optimized for tabular structured data (rows and columns) rather than native document stores, and standard geo-replication is read-only (active geo-replication supports writes in a single primary region only).


* **Azure Database for MySQL / PostgreSQL / MariaDB:** Managed open-source relational databases that use a single-write-region primary architecture, not native multi-region concurrent write engines.


* **Azure Cache for Redis:** An in-memory data store used for caching and session state, not a persistent multi-region concurrent document database.


* **SQL Data warehouses (Azure Synapse Analytics):** An enterprise analytics and data warehousing engine for massively parallel processing (MPP) of structured analytical workloads, not an operational multi-region document store.


* **Data factories:** An ETL/ELT data integration and orchestration service, not a database.



---

### 6. Exam Keyword / Trap Alert

* **"JSON documents"** + **"multiple regions (concurrent writes / globally distributed)"** is the direct signature trigger for **Azure Cosmos DB**.


## Q113

![Q113](/dump/question-images/q101-150/q113.png)



## Q114

![Q114](/dump/question-images/q101-150/q114.png)

### 1. Extracted Question Summary

**Question (HOTSPOT):**

For each of the following statements, select **Yes** if the statement is true. Otherwise, select **No**.

* **Statement 1:** All the Azure resources deployed to a resource group must use the same Azure region.


* **Statement 2:** If you assign a tag to a resource group, all the Azure resources in that resource group are assigned to the same tag.


* **Statement 3:** If you assign permissions for a user to manage a resource group, the user can manage all the Azure resources in that resource group.



---

### 2. Correct Answer

* **All the Azure resources deployed to a resource group must use the same Azure region:** **No**
* **If you assign a tag to a resource group, all the Azure resources in that resource group are assigned to the same tag:** **No**
* **If you assign permissions for a user to manage a resource group, the user can manage all the Azure resources in that resource group:** **Yes**

---

### 3. Verification of Visible Selection / Community Key

**Incorrect / Flawed Key.** The visible selections in the screenshot mark:

* Statement 1: **Yes** (Incorrect)


* Statement 2: **No** (Correct)


* Statement 3: **No** (Incorrect)



Statements 1 and 3 are marked incorrectly in the dump.

---

### 4. Official Microsoft Justification

* **Statement 1 (No):** A resource group has its own location to store its metadata, but the resources placed inside it **do not need to be in the same region** as the resource group or each other. You can deploy a virtual machine in East US and a storage account in West Europe into the exact same resource group.
* **Statement 2 (No):** Tags applied to a resource group **are not inherited** by the resources inside that resource group by default. To replicate tags from a resource group to child resources, an organization must implement an automated remediation policy using **Azure Policy**.


* **Statement 3 (Yes):** Azure Role-Based Access Control (Azure RBAC) permissions follow strict hierarchical inheritance:



$$\text{Management Group} \longrightarrow \text{Subscription} \longrightarrow \text{Resource Group} \longrightarrow \text{Resource}$$



When you assign a user permissions at the resource group level (e.g., Contributor or Owner), those permissions are **automatically inherited** by all child resources contained within that resource group.



---

### 5. Distractor Analysis (Why Others Are Wrong)

* **If Statement 1 were "Yes":** This confuses resource group metadata location with resource location. Azure explicitly supports multi-region resources residing in the same resource group to align with application lifecycles.


* **If Statement 2 were "Yes":** This confuses **RBAC inheritance** with **metadata tags**. While permissions inherit downward automatically, metadata tags do not inherit down to resources.


* **If Statement 3 were "No":** This fails to recognize Azure RBAC downward inheritance, where assigning permissions at a container scope applies to all nested resources within that scope.



---

### 6. Exam Keyword / Trap Alert

* **Tags do NOT inherit** down to resources automatically (requires Azure Policy).


* **RBAC permissions DO inherit** down to child resources automatically.


* **Resource Group location $\neq$ Resource location** (resources inside a resource group can span multiple regions).



## Q115 

![Q115](/dump/question-images/q101-150/q115.png)

### 1. Extracted Question Summary

**Question 115 (HOTSPOT):**

To complete the sentence, select the appropriate option in the answer area.

* **Sentence:**
"Data that is stored in the Archive access tier of an Azure Storage account [ drop-down ]"


* **Drop-down Options:**
* can be accessed at any time by using azcopy.exe.


* can only be read by using Azure Backup.


* must be restored before the data can be accessed.


* must be rehydrated before the data can be accessed.





---

### 2. Correct Answer

**must be rehydrated before the data can be accessed.**

* **Full Completed Sentence:** "Data that is stored in the Archive access tier of an Azure Storage account **must be rehydrated before the data can be accessed.**"



---

### 3. Verification of Visible Selection / Community Key

**Correct.** The highlighted red box surrounds **"must be rehydrated before the data can be accessed,"** which matches Microsoft's official terminology and technical mechanics for the Archive tier.

---

### 4. Official Microsoft Justification

* Azure Blob Storage provides online tiers (**Hot** and **Cool**) and an offline tier (**Archive**).
* The **Archive access tier** is an offline storage tier optimized for data that is rarely accessed and can tolerate retrieval latency of several hours.
* While a blob is in the Archive tier, it is offline and cannot be directly read, downloaded, or modified. To read or access the data, you must first change the tier to an online tier (Hot or Cool) or copy it to an online tier—a process officially defined in Azure as **blob rehydration**.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **can be accessed at any time by using azcopy.exe.:** `AzCopy` cannot directly read or download blobs residing in the offline Archive tier; attempting to download an archived blob results in an error stating the blob is offline.
* **can only be read by using Azure Backup:** Azure Backup is a backup service, not an exclusive tool or reader for archived blobs; furthermore, it does not bypass the offline state of the tier.
* **must be restored before the data can be accessed:** While "restore" is a colloquial backup term, Microsoft specifically uses and tests the technical cloud storage lifecycle term **"rehydrated"** (or **"rehydration"**) for bringing an archived blob back online.

---

### 6. Exam Keyword / Trap Alert

* **Archive Tier $\rightarrow$ Rehydrate / Rehydration.** Whenever AZ-900 mentions accessing, reading, or retrieving blobs stored in the **Archive tier**, the specific technical term required is always **rehydrate / rehydration** (not restore).



## Q116

![alt text](/dump/question-images/q101-150/q116.png)


### 1. Extracted Question Summary

**Question 116 (HOTSPOT):**

You plan to deploy a critical line-of-business application to Azure.

The application will run on an Azure virtual machine.

You need to recommend a deployment solution for the application. The solution must provide a guaranteed availability of **99.99 percent**.

What is the minimum number of virtual machines and the minimum number of availability zones you should recommend for the deployment? To answer, select the appropriate options in the answer area.

NOTE: Each correct selection is worth one point.

* **Minimum number of virtual machines:** Dropdown choices [1, 2, 3]


* **Minimum number of availability zones:** Dropdown choices [1, 2, 3]



---

### 2. Correct Answer

* **Minimum number of virtual machines:** **2**
* **Minimum number of availability zones:** **2**

---

### 3. Verification of Visible Selection / Community Key

(No selections or answers are marked in the uploaded screenshot; dropdown menus show unselected options 1, 2, 3.)

---

### 4. Official Microsoft Justification

* According to the official Microsoft Service Level Agreements (SLA) for Virtual Machines:
* **99.99% (Four Nines):** Requires at least **two or more instances** deployed across **two or more Availability Zones** in the same Azure region.
* **99.95%:** Requires two or more instances deployed across separate Fault and Update Domains within the same **Availability Set**.
* **99.9% / 99.5%:** Applies to a **single VM** using Premium SSD / Ultra Disk storage.


* Therefore, to reach the **99.99%** threshold with the *minimum* footprint, you need at least **2 virtual machines** distributed across at least **2 availability zones** (1 VM per zone).

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Selecting 1 Virtual Machine / 1 Availability Zone:** A single instance or single zone deployment cannot protect against a physical datacenter hardware failure and only qualifies for a single-VM SLA (up to 99.9%), falling short of 99.99%.
* **Selecting 3 Virtual Machines / 3 Availability Zones:** While deploying across all 3 zones in a region is a recommended pattern for high resilience, the question explicitly asks for the **minimum** number required to meet the 99.99% SLA guarantee. Microsoft's SLA terms stipulate "two or more instances deployed across two or more Availability Zones," making **2** the minimum.

---

### 6. Exam Keyword / Trap Alert

* Memorize the VM SLA tiers: **Single VM = 99.9%**, **Availability Set = 99.95%**, **Availability Zones (min 2 VMs across min 2 zones) = 99.99%**.
* Always pay close attention to the word **"minimum"**—even though Azure regions commonly offer 3 zones, the SLA requirement for 99.99% requires at least **2**.


## Q117

![Q117](/dump/question-images/q101-150/q117.png)

### 1. Extracted Question Summary

**Question 117:**

Which Azure service should you use to collect events from multiple resources into a centralized repository?

* **A.** Azure Event Hubs
* **B.** Azure Analysis Services
* **C.** Azure Monitor
* **D.** Azure Stream Analytics

---

### 2. Correct Answer

**A: Azure Event Hubs**

---

### 3. Verification of Visible Selection / Community Key

**Correct.** The red rectangle outlines **A. Azure Event Hubs**, and the visible key at the bottom states **Answer: A**, which is the intended answer for big data event ingestion into a centralized repository.

---

### 4. Official Microsoft Justification

* **Azure Event Hubs** is a fully managed, real-time data ingestion service (event streaming platform) capable of receiving and processing millions of events per second from distributed sources and resources. It acts as a centralized repository and front door for streaming architectures, allowing incoming event telemetry to be stored, buffered, and forwarded to downstream analytics or processing services.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **B. Azure Analysis Services:** An enterprise-grade data modeling engine and BI semantic model host; it does not collect or ingest streaming events from distributed resources.
* **C. Azure Monitor:** Focuses on observability by collecting metrics and operational/diagnostic logs for system health, alerts, and dashboards. It is not a general-purpose big data event ingestion pipeline.
* **D. Azure Stream Analytics:** A real-time complex event processing (CEP) and stream analytics engine used to process, filter, and transform data in-flight (typically consuming from Event Hubs or IoT Hub), not the repository/ingestion layer itself.

---

### 6. Exam Keyword / Trap Alert

* **"Collect events" + "centralized repository" / "millions of events per second":** Look for **Azure Event Hubs**.
* Remember the data stream pipeline order: **Event Hubs** (Ingest/Collect) $\longrightarrow$ **Stream Analytics** (Process/Transform) $\longrightarrow$ **Azure Synapse / Power BI** (Store/Analyze/Visualize).


## Q118

![Q118](/dump/question-images/q101-150/q118.png)


## Q119

![Q119](/dump/question-images/q101-150/q119.png)



## Q120

![Q120](/dump/question-images/q101-150/q120.png)



## Q121

![Q121](/dump/question-images/q101-150/q121.png)


## Q122

![Q122](/dump/question-images/q101-150/q122.png)



## Q123

![Q123](/dump/question-images/q101-150/q123.png)



## Q124

![Q124](/dump/question-images/q101-150/q124.png)

### 1. Extracted Question Summary

**Question 124 (DRAG DROP):**

Match the Azure Services service to the correct description.

Instructions: To answer, drag the appropriate service from the column on the left to its description on the right. Each service may be used once, more than once, or not at all.

NOTE: Each correct selection is worth one point.

**Services:**

* Azure Sphere


* IoT Central


* IoT Hub



**Answer Area Descriptions:**

1. A managed service that provides bidirectional communication between IoT devices and Azure


2. A fully managed software as a service (SaaS) solution to connect, monitor, and manage IoT devices at scale


3. A software and hardware solution that provides communication and security features for IoT devices



---

### 2. Correct Answer

* **A managed service that provides bidirectional communication between IoT devices and Azure:** **IoT Hub**
* **A fully managed software as a service (SaaS) solution to connect, monitor, and manage IoT devices at scale:** **IoT Central**
* **A software and hardware solution that provides communication and security features for IoT devices:** **Azure Sphere**

---

### 3. Verification of Visible Selection / Community Key

*(Section skipped: No selections or answers are marked or filled in the uploaded screenshot; all drop target boxes are empty.)*

---

### 4. Official Microsoft Justification

* **Azure IoT Hub (PaaS):** A managed PaaS messaging service that acts as a central message hub for bi-directional communication between an IoT application and the attached devices it manages, supporting per-device authentication and telemetry ingestion at scale.
* **Azure IoT Central (SaaS):** An application platform delivered as Software as a Service (SaaS) that provides pre-built templates, dashboards, and turnkey device management, reducing the burden and cost of developing and maintaining custom IoT solutions.
* **Azure Sphere:** An end-to-end security solution encompassing **hardware and software**, consisting of a certified secured MCU (microcontroller unit) chip, a custom Linux-based secured operating system (Azure Sphere OS), and the cloud-based Azure Sphere Security Service (AS3) for brokered trust and automated patching.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Swapping IoT Hub and IoT Central:** IoT Hub provides the foundational underlying PaaS messaging backbone, whereas IoT Central is an end-to-end SaaS solution with pre-built UI dashboards.
* **Confusing IoT Hub with Azure Sphere:** IoT Hub does not include physical hardware chips or a proprietary device operating system; only Azure Sphere combines custom hardware/silicon design with operating system and cloud security services.

---

### 6. Exam Keyword / Trap Alert

* **"Bidirectional communication" / "managed service" (PaaS)** $\longrightarrow$ **IoT Hub**.


* **"Software as a service (SaaS)"** $\longrightarrow$ **IoT Central**.


* **"Software and hardware solution" / "secured MCU"** $\longrightarrow$ **Azure Sphere**.


The fundamental difference between **Azure IoT Hub** and **Azure IoT Central** comes down to the cloud service model: **IoT Hub is a PaaS (Platform as a Service) building block**, while **IoT Central is a SaaS (Software as a Service) turnkey solution**.

---

### High-Level Comparison

| Dimension | Azure IoT Hub (PaaS) | Azure IoT Central (SaaS) |
| --- | --- | --- |
| **Service Model** | **PaaS** | **SaaS** |
| **What It Is** | A centralized messaging broker and device registry | A fully managed, web-based IoT application platform |
| **Under the Hood** | Raw infrastructure component | Built *on top* of IoT Hub, Stream Analytics, and Time Series Insights |
| **User Interface** | No end-user dashboard (API/SDK driven) | Out-of-the-box web UI with customizable charts and telemetry widgets |
| **Customization & Control** | Maximum flexibility to design backend routing, storage, and processing | Opinionated, preconfigured templates with simplified configuration |
| **Development Effort** | Requires custom coding for pipelines, data sinks, and web interfaces | Low-code / No-code setup; deployable in minutes |
| **Pricing Model** | Tiered by messages per day (e.g., Free, Basic, Standard units) | Per-device monthly fee with an included message quota |

---

### 1. Azure IoT Hub (The PaaS Engine)

IoT Hub acts as the secure, bidirectional communication pipeline between millions of IoT assets and Azure.

* **Core Responsibility:** Ingestion and signaling. It accepts telemetry from field devices (temperature, GPS, vibration) via protocols like MQTT, AMQP, or HTTPS, and routes commands back down to devices (e.g., firmware update trigger, valve shutdown).
* **Architectural Role:** It does **not** store data long-term, render charts, or trigger complex business automations on its own. It requires you to plumb its endpoints into other PaaS services:

$$\text{IoT Devices} \longrightarrow \mathbf{\text{IoT Hub}} \longrightarrow \begin{cases} \text{Azure Stream Analytics} \rightarrow \text{Power BI (Real-time telemetry)} \\ \text{Event Grid / Logic Apps} \rightarrow \text{Alerting workflows} \\ \text{Blob Storage / ADLS Gen2} \rightarrow \text{Cold data lake} \end{cases}$$


* **When to choose IoT Hub:**
* You need complete control over backend data processing pipelines.
* You already have custom web dashboards or line-of-business systems (e.g., ERP, CRM) consuming the data.
* You have a dedicated engineering team to build, secure, and maintain the end-to-end cloud infrastructure.



---

### 2. Azure IoT Central (The SaaS Application)

IoT Central abstracts the underlying plumbing by combining IoT Hub, data transformation engines, and dashboarding into a ready-to-use web portal.

* **Core Responsibility:** Turnkey lifecycle management and monitoring. You create an application from industry templates (e.g., retail, logistics, healthcare), register device templates, and instantly view live charts.
* **Architectural Role:** The operational database, stream processing, device provisioning service (DPS), and front-end interface are managed by Microsoft. Rules (e.g., *"If temperature $> 80^\circ\text{C}$, send email and post to Teams"*) are configured directly in the web UI without writing backend code.
* **When to choose IoT Central:**
* You need rapid prototyping or fast time-to-market without developing custom application frontends.
* Your primary need is device monitoring, dashboarding, and basic alert thresholds.
* You want predictable operational costs per device without managing individual PaaS pipeline resources.



---

### AZ-900 Exam Takeaway & Trigger Phrases

* If a question mentions **"bidirectional communication"**, **"messaging broker"**, or **"managed service" / PaaS** $\longrightarrow$ **IoT Hub**.
* If a question mentions **"Software as a Service"**, **"SaaS"**, **"turnkey"**, or **"preconfigured templates / dashboards"** $\longrightarrow$ **IoT Central**.
* If a question adds hardware microcontroller units (MCUs) and an integrated OS $\longrightarrow$ **Azure Sphere**.



## Q125

![Q125](/dump/question-images/q101-150/q125.png)



## Q126

![Q126](/dump/question-images/q101-150/q126.png)




## Q127

![Q127](/dump/question-images/q101-150/q127.png)



## Q128

![Q128](/dump/question-images/q101-150/q128.png)



## Q129

![Q129](/dump/question-images/q101-150/q129.png)



## Q130

![Q130](/dump/question-images/q101-150/q130.png)


## Q131

![Q131](/dump/question-images/q101-150/q131.png)



## Q132

![Q132](/dump/question-images/q101-150/q132.png)



## Q133

![Q133](/dump/question-images/q101-150/q133.png)


## Q134

![Q134](/dump/question-images/q101-150/q134.png)


### 1. Extracted Question Summary

**Question 134 (HOTSPOT):**

For each of the following statements, select **Yes** if the statement is true. Otherwise, select **No**.

NOTE: Each correct selection is worth one point.

* **Statement 1:** The Archive access tier is set at the storage account level.


* **Statement 2:** The Hot access tier is recommended for data that is accessed and modified frequently.


* **Statement 3:** The Cool access tier is recommended for long term backups.



---

### 2. Correct Answer

* **The Archive access tier is set at the storage account level:** **No**
* **The Hot access tier is recommended for data that is accessed and modified frequently:** **Yes**
* **The Cool access tier is recommended for long term backups:** **No**

---

### 3. Verification of Visible Selection / Community Key

*(Section skipped: No selections or answers are marked or selected in the uploaded screenshot; all radio buttons are unselected.)*

---

### 4. Official Microsoft Justification

* **Statement 1 (No):** Default access tiers set at the storage account level can only be configured as **Hot** or **Cool** (and in newer accounts, **Cold**). The **Archive** tier cannot be set as the default access tier for an entire storage account; it is strictly an offline tier set at the **individual blob level** (or managed via Blob Lifecycle Management rules).
* **Statement 2 (Yes):** The **Hot access tier** is optimized for data that is actively in use, frequently read, and frequently modified. It features the lowest access and transaction costs, balanced against higher storage capacity costs compared to cooler tiers.
* **Statement 3 (No):** The **Archive access tier** is the recommended tier for long-term backups, secondary archival, and compliance records that are rarely accessed and can tolerate hours of retrieval latency. The Cool tier is intended for short-term backup or infrequently accessed data that is retained for at least 30 days, whereas long-term/permanent archival belongs in the Archive tier.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **If Statement 1 were "Yes":** This confuses account-level default tiers (Hot/Cool/Cold) with blob-level tiering. If an account were set to Archive, any newly written blob would immediately become inaccessible and offline, which Azure architecture does not permit.
* **If Statement 2 were "No":** This contradicts the core definition of the Hot tier, which is engineered specifically for high-frequency transactions and active read/write cycles.
* **If Statement 3 were "Yes":** This confuses short-term intermediate storage with long-term data retention. Long-term backup data that must be preserved for months or years at minimal storage cost is explicitly targeted for the **Archive tier** (or immutable archival storage).

---

### 6. Exam Keyword / Trap Alert

* **"Archive tier set at storage account level"** $\longrightarrow$ Always **No**; only **Hot** and **Cool** (and Cold) can be set as the storage account default tier.
* **"Long-term backups / archival"** $\longrightarrow$ Points to the **Archive tier**, not Cool.
* **"Accessed and modified frequently"** $\longrightarrow$ Direct signature trigger for the **Hot access tier**.


### The Scenario: "CarePulse Health"

To understand Azure Storage tiers and account types, let’s consider a hypothetical hospital network, **CarePulse Health**:

* They run a web-based patient portal where patients view lab results.
* They capture thousands of high-resolution radiology scans (X-rays, MRI scans) daily.
* They must retain patient diagnostic histories for **10 years** to meet statutory healthcare regulations.
* Doctors access recent scans frequently, but older records are rarely opened unless a patient returns years later.

---

### Part 1: Choosing the Right Azure Storage Account Type

Azure provides different account types depending on whether you need general-purpose capabilities, specialized file shares, or ultra-low latency.

| Account Type | Description | CarePulse Use Case |
| --- | --- | --- |
| **General-purpose v2 (GPv2)** | The standard, recommended account type for most workloads. Supports Blobs, Files, Queues, and Tables. Supports all access tiers (Hot, Cool, Cold, Archive). | **Core Repository:** Storing all patient portal documents, application data, and standard blob logs. |
| **Premium Block Blobs** | High-performance solid-state drive (SSD) storage optimized for high transaction rates, low-latency, or small object writes. | **Live PACS / Radiology:** Ingestion buffer for raw MRI scanner streams that require sub-millisecond read/write latency. |
| **Premium File Shares** | Fully managed SMB/NFS file shares backed by SSDs with burstable I/O performance. | **Shared Medical Software:** Legacy on-premises diagnostic imaging tools running on VMs mapped via SMB. |
| **Premium Page Blobs** | Optimized for frequent random read/write operations (primarily VM disks). | **VM Data Disks:** Hosting OS and data disks for VMs running hospital database servers. |

---

### Part 2: Blob Storage Access Tiers

Azure Blob Storage prices storage based on a trade-off: **Capacity Cost (GB/month)** versus **Access/Transaction Cost (per read/write operation)**.

$$\begin{array}{rcccl} \text{Storage Cost per GB:} & \text{Hot} & > \quad \text{Cool} \quad > \quad \text{Cold} \quad > & \text{Archive} \\ \text{Access/Transaction Cost:} & \text{Hot} & < \quad \text{Cool} \quad < \quad \text{Cold} \quad < & \text{Archive} \end{array}$$

#### 1. Hot Access Tier

* **Characteristics:** Highest storage cost, lowest access cost. Data is online with millisecond latency.
* **Minimum Retention Requirement:** None.
* **CarePulse Scenario:** Diagnostic reports and blood test results generated within the **last 30 days**, along with profile pictures on the patient portal. These files are accessed and updated daily by patients and attending clinicians.

#### 2. Cool Access Tier

* **Characteristics:** Lower storage cost than Hot, but higher transaction and read costs. Data remains online with millisecond latency.
* **Minimum Retention Requirement:** **30 days** (early deletion or modification incur a prorated fee).
* **CarePulse Scenario:** Scans and lab reports between **30 days and 90 days old**. Follow-up consultations still occur, but access drops off sharply after the initial hospital discharge.

#### 3. Cold Access Tier

* **Characteristics:** Sits between Cool and Archive. Lower storage cost than Cool, higher access fee, but data is **still online** with immediate access (no rehydration delay).
* **Minimum Retention Requirement:** **90 days**.
* **CarePulse Scenario:** Records between **90 days and 365 days old**. Doctors rarely query them, but if an emergency occurs, they need the record immediately without waiting hours for an offline tape/archive retrieval.

#### 4. Archive Access Tier

* **Characteristics:** Lowest storage cost by a wide margin, highest retrieval and transaction cost. **This is an offline tier**. The data cannot be read directly; it must be **rehydrated** back to an online tier (Hot, Cool, or Cold), taking several hours (or minutes via high-priority rehydration).
* **Minimum Retention Requirement:** **180 days**.
* **Configuration Scope:** Set strictly at the **individual blob level**; it cannot be set as the default tier for the entire storage account.
* **CarePulse Scenario:** Regulatory patient records from **1 to 10 years old**. Required by law for legal compliance and medical history retention, but almost never viewed. Storing petabytes here saves over 80–90% in monthly storage fees.

---

### Summary Table: Access Tiers at a Glance

| Feature | Hot | Cool | Cold | Archive |
| --- | --- | --- | --- | --- |
| **Availability / State** | Online | Online | Online | **Offline** |
| **Access Latency** | Milliseconds | Milliseconds | Milliseconds | **Hours** (requires rehydration) |
| **Min. Storage Duration** | None | 30 days | 90 days | 180 days |
| **Storage Cost** | Highest | Low | Lower | **Lowest** |
| **Access / Read Cost** | Lowest | Moderate | High | **Highest** |
| **Account Default Level?** | Yes | Yes | Yes | **No (Blob level only)** |

---

### Part 3: Automated Lifecycle Management

CarePulse does not manually switch tiers for millions of patient files. Instead, they define a **Lifecycle Management Policy** (a JSON rule engine built into Azure Storage) that automates the progression:

```
[Day 0: File Created] 
       │ 
       ▼ (Placed in Hot Tier)
[Day 30] ──> Automatically transition to Cool Tier
       │
[Day 90] ──> Automatically transition to Cold Tier
       │
[Day 365] ─> Automatically transition to Archive Tier (Rehydration required if accessed)
       │
[Day 3650 (Year 10)] ──> Automatically delete blob (statutory retention expired)

```

---

### Key AZ-900 Exam Takeaways

1. **Default Account Tiers:** General-purpose v2 accounts can set their default access tier to **Hot**, **Cool**, or **Cold**. The **Archive** tier can **never** be set as the default at the account level.
2. **Offline vs. Online:** Hot, Cool, and Cold are all **online** (instant millisecond access). Archive is **offline** and requires **rehydration**.
3. **Cost Trade-off:** As you transition Hot $\rightarrow$ Cool $\rightarrow$ Cold $\rightarrow$ Archive, storage per-GB costs decrease, while read/transaction costs increase.



## Q135

![Q135](/dump/question-images/q101-150/q135.png)


## Q136

![Q136](/dump/question-images/q101-150/q136.png)



## Q137

![Q137](/dump/question-images/q101-150/q137.png)


### 1. Extracted Question Summary

**Question 137 (DRAG DROP):**

Match the serverless solution to the correct characteristic.

To answer, drag the appropriate serverless solution from the column on the left to its characteristic on the right. Each serverless solution may be used once, more than once, or not at all.

NOTE: Each correct match is worth one point.

**Serverless Solutions:**

* Azure Functions


* Azure Logic Apps



**Characteristics (Answer Area):**

* Executes code: [ Target Box ]


* Is always stateful: [ Target Box ]


* Runs only in the cloud: [ Target Box ]



---

### 2. Correct Answer

* **Executes code:** **Azure Functions**
* **Is always stateful:** **Azure Logic Apps**
* **Runs only in the cloud:** **Azure Logic Apps**

---

### 3. Verification of Visible Selection / Community Key

*(Section skipped: No choices are marked or placed in the screenshot; all drop target boxes are empty.)*

---

### 4. Official Microsoft Justification

According to official Microsoft Learn documentation comparing **Azure Functions** and **Azure Logic Apps**:

* **Executes code $\longrightarrow$ Azure Functions:** Azure Functions is a code-first serverless compute service designed to run custom code (C#, Python, JavaScript, Java, PowerShell) in response to event triggers. In contrast, Logic Apps is a designer-first (low-code/no-code) orchestration engine that executes predefined actions and connectors rather than custom raw code.
* **Is always stateful $\longrightarrow$ Azure Logic Apps:** By default and in its traditional consumption model, Azure Logic Apps workflows are **stateful** (retaining execution history, input/output parameters, and run status for every step in Azure storage). Conversely, Azure Functions is fundamentally **stateless** by default (behaving as if restarted on every trigger invocation) unless explicitly implemented using the *Durable Functions* extension.
* **Runs only in the cloud $\longrightarrow$ Azure Logic Apps:** In the classic AZ-900 compute curriculum, Logic Apps workflows are fully managed cloud orchestrations that run within Azure datacenters. Azure Functions, on the other hand, is built on the open-source Azure Functions Core Tools/Runtime, enabling functions to run locally on a developer workstation, in on-premises containers, or across Kubernetes clusters.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **If "Executes code" were Logic Apps:** Logic Apps orchestrates services via visual connectors and declarative JSON workflows; it does not natively compile or execute raw source code directly (it must call external webhooks, APIs, or Azure Functions to run custom logic).
* **If "Is always stateful" were Functions:** Functions are stateless by default; they discard execution context as soon as the execution invocation terminates unless using Durable Functions state management.
* **If "Runs only in the cloud" were Functions:** The Azure Functions host runtime is cross-platform and containerized, making local workstation debugging and on-premises hosting a standard feature.

---

### 6. Exam Keyword / Trap Alert

* **"Code-first"** / **"Executes code"** $\longrightarrow$ **Azure Functions**.


* **"Designer-first"** / **"Automated workflows / Connectors"** / **"Stateful orchestration"** $\longrightarrow$ **Azure Logic Apps**.


* Note the subtle comparison tested here: Functions can run locally or in containers, whereas Consumption Logic Apps runs exclusively in Azure cloud datacenters.


In cloud computing and architecture, **state** refers to **data, memory, and execution history that must be preserved from one point in time to another**.

---

### 1. What "Stateful" Means in the Context of the Question

In Question 137, comparing **Azure Logic Apps** and **Azure Functions**:

* **Why Logic Apps is Considered "Always Stateful" (in the classic model):**
* When a Logic App workflow triggers, Azure automatically tracks and persists every single step, action, branch condition, input payload, and output response to underlying storage.
* If a workflow contains a delay or approval action that waits 7 days:

$$\text{Trigger} \longrightarrow \text{Action 1} \longrightarrow \mathbf{\text{Wait 7 Days (Sleep)}} \longrightarrow \text{Action 2}$$



The workflow doesn't occupy CPU memory for 7 days; instead, the runtime serializes its exact **state** to storage. A week later, it rehydrates that state and picks up precisely at Action 2.
* You get an out-of-the-box **Run History** in the Azure Portal showing the exact inputs and outputs of every single action that occurred during the execution.


* **Contrast with Azure Functions (Default: Stateless):**
* A standard Azure Function is an ephemeral, event-driven piece of code.
* It starts when triggered (HTTP request, queue message, timer), processes data in memory, returns a response, and terminates.
* It retains no memory of previous runs. If two requests arrive 2 seconds apart, Run #2 knows nothing about Run #1 unless your code manually queries an external database or cache.



---

### 2. What Else is Stateful in Azure Execution?

Beyond Logic Apps, several services and design patterns across Azure are explicitly built to manage or execute state:

#### A. Durable Functions (Stateful Code Execution)

While standard Azure Functions are stateless, Microsoft created the **Durable Functions** extension to bring code-first statefulness to serverless compute. It uses an underlying framework (Durable Task Framework) backed by Azure Storage queues and tables:

* **Orchestrator Functions:** Can pause execution (`await context.WaitForExternalEvent()`), wait for minutes, days, or months, and resume without losing variables or local state.
* **Entity Functions (Durable Entities):** Implement the *Actor Model* in code, allowing you to define stateful objects (e.g., a digital shopping cart or IoT digital twin) that maintain their state in-memory and persist it automatically.

#### B. Azure Service Fabric (Stateful Services & Reliable Actors)

* Unlike standard container orchestrators that treat containers as disposable and stateless, Azure Service Fabric natively supports **Stateful Reliable Services** and **Reliable Collections** (`IReliableDictionary`, `IReliableQueue`).
* The application code and data reside on the same compute nodes with automated state replication across replicas, delivering ultra-low-latency read/writes without querying external databases.

#### C. Enterprise Messaging & Service Bus Sessions

* **Azure Service Bus Sessions:** By default, message queues are stateless pipes. When **Sessions** (`SessionId`) are enabled, the broker guarantees ordered FIFO processing and allows consumers to store and retrieve **Session State** directly on the queue broker itself (e.g., accumulating multi-part transactions before committing).

#### D. Azure Kubernetes Service (AKS) with StatefulSets & Persistent Volumes

* Running standard web containers (e.g., NGINX, stateless APIs) treats pods as disposable (ephemeral).
* When deploying databases (PostgreSQL, MongoDB) or distributed systems (Kafka, Elasticsearch) on AKS, you use **Kubernetes StatefulSets** bound to **Azure Managed Disks (PVCs)**. The execution lifecycle preserves fixed network identities and persistent disk state across pod restarts and node failures.

#### E. Azure Stream Analytics (Windowing & Temporal Analytics)

* When calculating real-time aggregates over time (e.g., *"Calculate the average temperature over the last 10 minutes"* using Tumbling or Sliding Windows), Stream Analytics maintains **stateful in-flight memory** across incoming events until the window closes and outputs the result.

---

### Architectural Summary: Stateless vs. Stateful

| Execution Pattern | State Storage | Typical Azure Services | Best Used For |
| --- | --- | --- | --- |
| **Stateless** | None (State pushed out to external DB/Cache) | Azure Functions, App Service, Container Apps, AKS Deployments | Web APIs, image resizing, stream consumers, ETL microservices |
| **Stateful (Visual/Orchestration)** | Engine persists run history & step states | Azure Logic Apps, Power Automate | Business process flows, human-in-the-loop approvals, multi-step SaaS integrations |
| **Stateful (Code/Compute)** | Framework persists variables & execution pointers | Durable Functions, Service Fabric Reliable Actors | Long-running workflows in code, fan-out/fan-in patterns, distributed state machines |
| **Stateful (Data/Infrastructure)** | Dedicated storage volume attached to compute | AKS StatefulSets + Azure Disks, Azure SQL, Cosmos DB | Databases, message brokers, caching nodes, search clusters |



**Both are true.**

---

### 1. It is a Public Azure Service You Can Provision Directly

Just like you can create an Azure Kubernetes Service (AKS) cluster, you can go into the Azure Portal (or run an Azure CLI command / Bicep template) and provision an **Azure Service Fabric cluster**.

* When you provision it, Azure provisions a cluster of Virtual Machine Scale Sets (VMSS) running the Service Fabric orchestrator.
* You can deploy your own microservices, Docker containers, or .NET/Java applications directly into it.
* You manage application lifecycles, configure scaling rules, perform rolling upgrades, and monitor health metrics, exactly as you would with any container or microservice orchestrator.

```bash
# You can literally create one yourself:
az sf cluster create \
  --resource-group rg-microservices \
  --location eastus \
  --cluster-size 5 \
  --vm-sku Standard_D2s_v3

```

---

### 2. It is Also the Internal Engine Microsoft Built to Run Azure Itself

Historically, Microsoft developed Service Fabric internally in the early 2010s because off-the-shelf distributed systems tools could not deliver the scale, durability, and sub-millisecond data replication they needed for hyperscale cloud operations.

Microsoft built its foundational PaaS services on top of it:

* **Azure SQL Database:** Uses Service Fabric to handle automatic failover, high availability, and replica management between primary and secondary database instances.
* **Azure Cosmos DB:** Uses it to orchestrate partition management, global data replication, and low-latency read/write routing.
* **Azure Event Hubs & Service Bus:** Relies on its stateful partitions for high-throughput message ingestion and persistence.
* **Cortana & Skype for Business:** Scaled backends using Service Fabric's actor model.

After proving the platform internally at enterprise scale, Microsoft open-sourced the core runtime and released **Azure Service Fabric** as a first-class, publicly available compute service for external enterprise customers.

---

### Summary: Service Fabric vs. AKS in Practice

* **Azure Kubernetes Service (AKS):** Microsoft’s implementation of the CNCF open-source Kubernetes standard. It is the modern, cloud-native **go-to default** recommended by Microsoft for general-purpose container orchestration and microservices.
* **Azure Service Fabric:** A specialized distributed systems platform you can deploy yourself, but also the underlying architectural fabric Microsoft engineered to keep mission-critical Azure database and messaging services resilient.



## Q138

![Q138](/dump/question-images/q101-150/q138.png)

### 1. Extracted Question Summary

**Question 138 (DRAG DROP):**

Match the Azure governance feature to the correct description.

Instructions: To answer, drag the appropriate feature from the column on the left to its description on the right. Each feature may be used once, more than once, or not at all.

NOTE: Each correct match is worth one point.

**Features (Left Column):**

* Azure Blueprints


* Azure Policy


* Azure resource locks


* Azure tags



**Answer Area Descriptions (Right Column):**

1. Restrict which virtual machine types can be created in a subscription.


2. Identify Azure resources that are associated with specific cost centers.


3. Deploy a complete Azure application environment including resources configuration and role assignments.



---

### 2. Correct Answer

* **Restrict which virtual machine types can be created in a subscription:** **Azure Policy**
* **Identify Azure resources that are associated with specific cost centers:** **Azure tags**
* **Deploy a complete Azure application environment including resources configuration and role assignments:** **Azure Blueprints**

---

### 3. Verification of Visible Selection / Community Key

**Correct.** The red text in the answer boxes shows **Azure Policy**, **Azure tags**, and **Azure Blueprints** matching the three descriptions respectively, which aligns with Microsoft governance specifications.

---

### 4. Official Microsoft Justification

* **Azure Policy:** Enforces organizational standards and assesses compliance at scale by defining rules for resource properties and behaviors. A classic built-in policy definition is restricting allowed virtual machine SKUs/types within a subscription or management group scope.
* **Azure Tags:** Key-value pairs applied to Azure resources, resource groups, and subscriptions to logically organize assets and assign metadata. They are commonly used in enterprise cost management and billing reporting to associate resources with specific departments or cost centers.
* **Azure Blueprints:** Enables cloud architects to define a repeatable set of Azure resources that implement and adhere to an organization's standards, patterns, and requirements. It orchestrates the deployment of various resource artifacts—including ARM/Bicep templates, role assignments (RBAC), and policy assignments—into a fully packaged, governed environment package. *(Note: Microsoft is transitioning blueprints functionality toward Template Specs and Deployment Stacks, but Azure Blueprints remains standard in AZ-900 exam questions).*

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Azure resource locks (Unused Option):** Prevents accidental deletion or modification of resources (`CanNotDelete` and `ReadOnly`). Resource locks cannot restrict specific VM SKU sizes, track cost metadata, or deploy application environments.
* **If Azure Policy were matched to Cost Centers:** Azure Policy can enforce that tags exist, but tags themselves are the actual metadata identifiers used to track and associate cost center billing data.
* **If Azure tags were matched to Restricting VM types:** Tags are passive metadata; they have no active enforcement engine to block or allow resource creation by SKU or type.

---

### 6. Exam Keyword / Trap Alert

* **"Restrict / Enforce compliance"** $\longrightarrow$ **Azure Policy**.


* **"Cost centers / Billing metadata / Department organization"** $\longrightarrow$ **Azure tags**.


* **"Deploy complete environment / Package ARM templates + RBAC + Policies"** $\longrightarrow$ **Azure Blueprints**.


* **"Prevent accidental deletion or modification"** $\longrightarrow$ **Azure resource locks**.


### What is Azure Blueprints?

**Azure Blueprints** is a declarative orchestration engine designed to automate enterprise cloud governance and environment deployment at scale.

Instead of treating infrastructure deployment (ARM/Bicep templates), security guardrails (Azure Policy), access control (RBAC roles), and resource groups as disconnected administrative tasks, Azure Blueprints packages them together into a **single, reusable, and version-controlled definition**.

When an organization onboards a new project or department, cloud architects don't run four or five separate configuration scripts. They assign a **Blueprint**, and Azure stamps out a standardized, compliant subscription environment in minutes.

---

### The Four Core "Artifacts" of a Blueprint

A Blueprint definition is composed of four building blocks known as **artifacts**:

```
                  ┌──────────────────────────────────────────────┐
                  │               Azure Blueprint                │
                  └──────────────────────┬───────────────────────┘
                                         │
     ┌───────────────────┬───────────────┴───────────────┬───────────────────┐
     ▼                   ▼                               ▼                   ▼
[Resource Groups]  [Role Assignments (RBAC)]   [Policy Assignments]   [ARM / Bicep Templates]
Define logical     Grant who can do what       Enforce compliance &   Deploy actual resources
boundaries         (e.g., Reader, Contributor) restrictions           (VNets, Key Vaults, VMs)

```

1. **Resource Groups:** Automatically provisions named resource groups with required lifecycles.
2. **Role Assignments (RBAC):** Binds specific Entra ID groups or users to roles (e.g., ensuring the central SecOps team automatically receives *Security Admin* on every new environment).
3. **Policy Assignments:** Attaches compliance constraints (e.g., restricting VM sizes or requiring specific tags).
4. **ARM / Bicep Templates:** Deploys foundational infrastructure (e.g., standard virtual networks, subnets, route tables, network security groups, and central log forwarders).

---

### Key Feature: Resource Locking

Standard ARM template deployments are "deploy-and-forget"—once deployed, a subscription owner could modify or delete the resources.

Azure Blueprints introduces native **Resource Locking**:

* **Don't Lock:** Normal resource behavior.
* **Read Only:** Resources deployed by the blueprint cannot be changed, even by subscription owners.
* **Do Not Delete:** Resources cannot be deleted, ensuring foundational components (like an express route gateway or logging storage account) remain intact.

---

### Hypothetical Scenario: "FinTrust Digital Bank"

#### The Problem

**FinTrust**, a regulated financial institution, has 15 independent application teams developing new microservices. Every time a new team starts a project, they request a new Azure Subscription.

Historically, this created chaos:

* Team A forgot to enable disk encryption on their VMs.
* Team B deployed expensive GPU-based instances in unauthorized overseas regions, violating data sovereignty regulations.
* Team C failed to grant the Central IT Security team monitoring access.
* Manually setting up each subscription took Central IT two weeks of back-and-forth tickets.

#### The Blueprint Solution: `"Secure-Banking-Foundation:v1.0"`

Central Cloud Architecture builds a single Blueprint definition containing four artifacts:

| Blueprint Artifact Type | Configured Element | Purpose at FinTrust |
| --- | --- | --- |
| **Resource Group** | `rg-core-networking` & `rg-app-workload` | Separates shared network assets from developer applications. |
| **Policy Assignment** | 1. Allowed Locations: `UK South`, `UK West` only.<br>

<br>2. Require tag: `CostCenter`.<br>

<br>3. Deny unencrypted managed disks. | Guarantees data residency compliance and cost allocation before any code runs. |
| **Role Assignment** | Entra Group `SecOps-Admins` $\rightarrow$ **Security Admin** | Guarantees the corporate security team has permanent visibility without waiting for the app team to grant access. |
| **ARM / Bicep Template** | Hub-and-Spoke Spoke VNet with Network Security Group (NSG) and default routes to central firewall | Ensures the new environment is securely connected to the corporate network immediately upon provisioning. |

#### The Deployment Workflow

1. A new team ("Lending Portal") requests an environment.
2. Central IT assigns `"Secure-Banking-Foundation:v1.0"` to the new subscription and sets the Blueprint lock to **Do Not Delete**.
3. Azure evaluates the artifacts and automatically builds the resource groups, configures the network, attaches the policies, and assigns the roles.
4. **The Outcome:** In under 10 minutes, the Lending Portal team receives a production-ready subscription. They can deploy their databases and containers, but:
* If they attempt to spin up a VM in `East US`, **Azure Policy blocks it**.
* If they attempt to delete the central route table or VNet peering, **Blueprint Locks block it**.
* The security team already has full monitoring dashboards running.



---

### Important Evolution Note (AZ-900 Context)

* **For the AZ-900 Exam:** Azure Blueprints is tested as the primary governance tool to **"deploy a complete, repeatable environment packaging ARM templates, RBAC, and Policies."**
* **In Modern Azure Architecture:** Microsoft has evolved its governance and infrastructure-as-code strategy toward **Azure Deployment Stacks** and **Template Specs** (for resource lifecycle management and locking) paired with **Azure Landing Zones**. However, in certification exams, the key concept to match with *orchestrated multi-artifact governance* remains **Azure Blueprints**.


### What is Azure Policy?

**Azure Policy** is Azure’s native guardrail and governance engine. It evaluates the properties of resources across your environment and compares them against corporate business rules and regulatory standards.

Unlike Role-Based Access Control (**RBAC**), which focuses on **who** has permission to take an action (user identity and actions), Azure Policy focuses on **what** can be created, configured, or altered (resource properties, configurations, and locations), regardless of the user's privilege level. Even a Subscription **Owner** must comply with active Azure Policies.

---

### The Anatomy of an Azure Policy

Azure Policy operates through a distinct hierarchy of components:

```
┌────────────────────────────────────────────────────────┐
│               Policy Definition (Rule)                 │
│  JSON conditions defining what to check & what to do   │
└───────────────────────────┬────────────────────────────┘
                            │ (Grouped into)
                            ▼
┌────────────────────────────────────────────────────────┐
│             Initiative (Policy Set)                    │
│     Bundle of policies (e.g., "NIST 800-53", "FinOps") │
└───────────────────────────┬────────────────────────────┘
                            │ (Applied to)
                            ▼
┌────────────────────────────────────────────────────────┐
│                   Policy Assignment                    │
│  Scope: Management Group ──> Subscription ──> RG       │
└────────────────────────────────────────────────────────┘

```

1. **Policy Definition:** A JSON document outlining the conditions under which a resource is evaluated and the action (effect) taken.
2. **Initiative Definition (Policy Set):** A collection of multiple related policy definitions packaged together to achieve a broader compliance goal (e.g., a standard ISO 27001 or PCI-DSS initiative).
3. **Policy Assignment:** The act of attaching a policy or initiative to a specific **Scope** (a Management Group, an entire Subscription, or an individual Resource Group). Everything within that scope inherits the policy unless an explicit **Exclusion** is defined.

---

### Policy Effects: How Policies Enforce & Restrict

When a request arrives at the Azure Resource Manager (ARM) control plane (via Portal, CLI, Terraform, or Bicep), Azure Policy intercepts the call before resources are provisioned:

| Effect | How It Works | Ideal Governance Scenario |
| --- | --- | --- |
| **`Deny`** | Immediately blocks the deployment request and returns an error. | Hard guardrails: blocking costly VM sizes or unauthorized regions. |
| **`Audit`** | Allows the resource creation/update, but marks the resource as "Non-compliant" in the Azure Policy compliance dashboard. | Passive monitoring: tracking unapproved configurations without breaking production CI/CD pipelines. |
| **`Append`** | Adds required fields or properties to the resource payload during creation if missing. | Auto-adding default network rules or security settings. |
| **`Modify`** | Adds, updates, or removes properties or tags during resource creation/update. | Remediation: automatically adding required metadata tags (e.g., `Environment: Production`). |
| **`DeployIfNotExists` (DINE)** | If a related dependent resource is missing, deploys it automatically after the parent resource creates. | Automated agent deployment: automatically installing the Azure Monitor Agent when a VM is provisioned. |

---

### Deep Dive: Restricting Virtual Machine SKUs

One of the most common governance scenarios in enterprise cloud cost management is preventing teams from accidentally spinning up ultra-expensive compute (such as GPU instances like `Standard_NC24` costing thousands per month) when they only need basic general-purpose nodes.

#### How It Works Under the Hood

Microsoft provides a built-in policy named **"Allowed virtual machine size SKUs"**.

1. **The Policy Definition (Rule Logic):**
The policy evaluates the `type` and inspects the `sku.name` attribute submitted in the ARM template request:
```json
{
  "mode": "Indexed",
  "policyRule": {
    "if": {
      "allOf": [
        {
          "field": "type",
          "equals": "Microsoft.Compute/virtualMachines"
        },
        {
          "not": {
            "field": "Microsoft.Compute/virtualMachines/sku.name",
            "in": "[parameters('listOfAllowedSKUs')]"
          }
        }
      ]
    },
    "then": {
      "effect": "Deny"
    }
  },
  "parameters": {
    "listOfAllowedSKUs": {
      "type": "Array",
      "metadata": {
        "description": "The list of size SKUs that can be specified for virtual machines."
      }
    }
  }
}

```


2. **The Assignment:**
* **Scope:** Subscription `Finance-Production`.
* **Parameter input:** `["Standard_D2s_v5", "Standard_D4s_v5", "Standard_B2ms"]`.
* **Effect:** `Deny`.


3. **The User Experience:**
* If a developer attempts to run `az vm create --size Standard_E64s_v5 ...` or clicks the portal to launch a memory-intensive instance, ARM halts the operation with a HTTP 403 Forbidden payload:
`"Resource 'vm-analytics-01' was disallowed by policy 'Allowed virtual machine size SKUs'."`
* No virtual machine is created, and zero unexpected infrastructure charges are incurred.



---

### Other Core Governance Patterns Handled by Azure Policy

1. **Geographic Data Sovereignty & Residency:**
* **Policy:** "Allowed locations"
* **Mechanism:** Blocks creation of any resource outside specified regions (e.g., allowing only `UK South` or `North Europe`).


2. **Cost Allocation & Financial Tagging:**
* **Policy:** "Require a tag and its value on resources"
* **Mechanism:** Prevents resource group creation unless mandatory key-value tags exist (e.g., `CostCenter: 4021`, `Environment: Staging`), ensuring cost attribution across departments.


3. **Storage & Data Security Controls:**
* **Policy:** "Secure transfer to storage accounts should be enabled"
* **Mechanism:** Denies or flags any Azure Storage Account deployed with plain unencrypted HTTP traffic enabled instead of forcing HTTPS.


4. **Network Perimeter Enforcement:**
* **Policy:** "Network interfaces should not have public IPs"
* **Mechanism:** Prevents VMs from binding directly to public IP addresses, requiring all ingress traffic to pass through centralized Application Gateways, Azure Firewalls, or NVAs.



---

### RBAC vs. Azure Policy: The Critical Distinction

| Feature | Azure Role-Based Access Control (RBAC) | Azure Policy |
| --- | --- | --- |
| **Focus** | **User Actions & Identity** ("Who") | **Resource Properties & State** ("What") |
| **Execution Point** | Checks if the user has the API action permission (e.g., `Microsoft.Compute/virtualMachines/write`). | Checks if the resulting resource conforms to configuration rules (e.g., location, SKU size, tags). |
| **Scope of Authority** | Grants access to manage resources. | Applies guardrails across all users, regardless of RBAC role (even Subscription Owners). |
| **Core AZ-900 Question Trigger** | *"Grant access to a specific team / manage user rights"* | *"Ensure compliance / restrict resource types / enforce naming or tagging standards"* |




## Q139

![Q139](/dump/question-images/q101-150/q139.png)



## Q140

![Q140](/dump/question-images/q101-150/q140.png)



## Q141

![Q141](/dump/question-images/q101-150/q141.png)



## Q142

![Q142](/dump/question-images/q101-150/q142.png)


## Q143

![Q143](/dump/question-images/q101-150/q143.png)



## Q144

![Q144](/dump/question-images/q101-150/q144.png)



## Q145

![Q145](/dump/question-images/q101-150/q145.png)



## Q146

![Q146](/dump/question-images/q101-150/q146.png)



## Q147

![Q147](/dump/question-images/q101-150/q147.png)



## Q148

![Q148](/dump/question-images/q101-150/q148.png)



## Q149

![Q149](/dump/question-images/q101-150/q149.png)


## Q150

![Q150](/dump/question-images/q101-150/q150.png)



## Q151

![Q151](/dump/question-images/q151-200/q151.png)


## Q152

![Q152](/dump/question-images/q151-200/q152.png)



## Q153

![Q153](/dump/question-images/q151-200/q153.png)



## Q154

![Q154](/dump/question-images/q151-200/q154.png)



## Q155

![Q155](/dump/question-images/q151-200/q155.png)



## Q156

![Q156](/dump/question-images/q151-200/q156.png)


## Q157

![Q157](/dump/question-images/q151-200/q157.png)


## Q158

![Q158](/dump/question-images/q151-200/q158.png)


## Q159

![Q159](/dump/question-images/q151-200/q159.png)



## Q160

![Q160](/dump/question-images/q151-200/q160.png)



## Q161

![Q161](/dump/question-images/q151-200/q161.png)



## Q162

![Q162](/dump/question-images/q151-200/q162.png)



## Q163

![Q163](/dump/question-images/q151-200/q163.png)



## Q164

![Q164](/dump/question-images/q151-200/q164.png)



## Q165

![Q165](/dump/question-images/q151-200/q165.png)


## Q166

![Q166](/dump/question-images/q151-200/q166.png)



## Q167

![Q167](/dump/question-images/q151-200/q167.png)

### 1. Extracted Question Summary

**Question 167:**

Note: This question is part of a series of questions that present the same scenario. Each question in the series contains a unique solution that might meet the stated goals.

An Azure administrator plans to **run a PowerShell script that creates Azure resources**.

You need to **recommend which computer configuration to use to run the script**.

**Solution:** Run the script from a computer that runs **macOS and has PowerShell Core 6.0 installed**.

Does this meet the goal?

* **A.** Yes


* **B.** No



---

### 2. Correct Answer

**A: Yes**

---

### 3. Verification of Visible Selection / Community Key

*(Section skipped: No choices or community keys are marked, boxed, or pre-selected in the uploaded screenshot.)*

---

### 4. Official Microsoft Justification

* **PowerShell Core (PowerShell 6.0 and later)** is built on .NET Core and is fully cross-platform, running natively on **macOS**, **Linux**, and **Windows**.
* The **Azure PowerShell module (`Az`)** supports PowerShell Core on macOS. Once PowerShell Core is present on macOS, an administrator can execute scripts that interact with the Azure Resource Manager (ARM) API to deploy and manage Azure resources.
* Because macOS with PowerShell Core 6.0 fulfills the platform requirement to run Azure PowerShell scripts, the proposed solution meets the goal.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **B. No:** This option is incorrect because it relies on the outdated misconception that PowerShell is exclusive to Windows (Windows PowerShell 5.1). PowerShell Core removed the Windows-only dependency, making macOS a fully supported workstation configuration for Azure PowerShell automation.

---

### 6. Exam Keyword / Trap Alert

* **"macOS / Linux" + "PowerShell Core / pwsh"** $\longrightarrow$ **Yes** (PowerShell Core is cross-platform and runs Azure resource creation scripts).


* **Compare this series across the three variations:**
* *Linux + Azure CLI* $\longrightarrow$ **No** (CLI tools alone cannot execute `.ps1` PowerShell scripts).


* *Chrome OS + Azure Cloud Shell* $\longrightarrow$ **Yes** (Cloud Shell provides the full web-based PowerShell environment).


* *macOS + PowerShell Core* $\longrightarrow$ **Yes** (cross-platform local execution environment).

No, **Azure CLI is not required at all** to run PowerShell scripts that manage Azure resources. They are two completely independent command-line tools.

However, **just installing PowerShell itself is not enough either**.

To run a PowerShell script that creates or manages Azure resources, your system needs **two things**—neither of which is the Azure CLI:

---

### What Is Actually Required

1. **PowerShell Engine (The Shell / Runtime):**
* Either Windows PowerShell 5.1 (built into Windows) or **PowerShell Core (PowerShell 7+)** on Windows, macOS, or Linux.


2. **The Azure PowerShell Module (`Az`):**
* PowerShell out of the box only understands base operating system cmdlets (like `Get-Process`, `Set-Item`).
* It does not know what an Azure resource group or VM is until you install the **`Az` module**, which provides the Azure-specific cmdlets (`Connect-AzAccount`, `New-AzResourceGroup`, `New-AzVM`):
```powershell
Install-Module -Name Az -Repository PSGallery -Force

```





Once the `Az` module is installed inside PowerShell, you can authenticate and run scripts directly against Azure Resource Manager (ARM) APIs via HTTPS. **No Azure CLI component is involved or consulted.**

---

### Why People Mix Them Up: Azure CLI vs. Azure PowerShell

Both tools can achieve almost identical administrative tasks, but they use different syntax, runtimes, and execution pipelines:

| Feature | Azure PowerShell | Azure CLI (`az`) |
| --- | --- | --- |
| **Tool Type** | A set of cmdlets installed as a **PowerShell module (`Az`)** | A standalone executable program (`az.exe` or binary built in Python) |
| **Command Syntax** | Verb-Noun cmdlets:<br>

<br>`New-AzResourceGroup -Name rg1 -Location eastus` | Space-delimited command verbs:<br>

<br>`az group create --name rg1 --location eastus` |
| **Output Type** | Strongly-typed **.NET Objects** passed through the pipeline | Text streams formatted as **JSON, TSV, or Table** |
| **Where it Runs** | Inside the PowerShell host runtime (`pwsh` or `powershell.exe`) | Any shell (Bash, Zsh, CMD, or PowerShell) |
| **Dependency on the other?** | **Zero.** Does not need Azure CLI. | **Zero.** Does not need PowerShell (can run directly in Bash/Zsh). |

---

### How the AZ-900 Exam Frames This

The AZ-900 exam tests your understanding of tooling dependencies with questions like the ones you just reviewed:

* **"Can you run a PowerShell script on Linux if you only install Azure CLI?"**
$\longrightarrow$ **No.** Azure CLI cannot parse PowerShell cmdlets like `New-AzResourceGroup`.


* **"Can you run an Azure PowerShell script from macOS?"**
$\longrightarrow$ **Yes**, provided you have PowerShell Core (`pwsh`) and the `Az` module installed. (In AZ-900 questions, mentioning *"PowerShell Core installed"* is treated as establishing the valid PowerShell execution environment).


* **"Can you run Azure PowerShell or CLI without installing either on your local machine?"**
$\longrightarrow$ **Yes**, via **Azure Cloud Shell**, which runs in a browser and comes with both Azure PowerShell and Azure CLI pre-installed and authenticated.



## Q168

![Q168](/dump/question-images/q151-200/q168.png)



## Q169

![Q169](/dump/question-images/q151-200/q169.png)



## Q170

![Q170](/dump/question-images/q151-200/q170.png)


## Q171 

![Q171](/dump/question-images/q151-200/q171.png)


## Q172

![Q172](/dump/question-images/q151-200/q172.png)



## Q173

![Q173](/dump/question-images/q151-200/q173.png)


## Q174

![Q174](/dump/question-images/q151-200/q174.png)



## Q175

![Q175](/dump/question-images/q151-200/q175.png)


## Q176

![Q176](/dump/question-images/q151-200/q176.png)


## Q177

![Q177](/dump/question-images/q151-200/q177.png)


## Q178

![Q178](/dump/question-images/q151-200/q178.png)


## Q179

![Q179](/dump/question-images/q151-200/q179.png)


## Q180

![Q180](/dump/question-images/q151-200/q180.png)



## Q181

![Q181](/dump/question-images/q151-200/q181.png)


## Q182

![Q182](/dump/question-images/q151-200/q182.png)


## Q183

![Q183](/dump/question-images/q151-200/q183.png)


## Q184

![Q184](/dump/question-images/q151-200/q184.png)


## Q185

![Q185](/dump/question-images/q151-200/q185.png)


## Q186

![Q186](/dump/question-images/q151-200/q186.png)



## Q187

![Q187](/dump/question-images/q151-200/q187.png)



## Q188

![Q188](/dump/question-images/q151-200/q188.png)


## Q189

![Q189](/dump/question-images/q151-200/q189.png)


## Q190

![Q190](/dump/question-images/q151-200/q190.png)


## Q191

![Q191](/dump/question-images/q151-200/q191.png)



## Q192

![Q192](/dump/question-images/q151-200/q192.png)


## Q193

![Q193](/dump/question-images/q151-200/q193.png)



## Q194

![Q194](/dump/question-images/q151-200/q194.png)


## Q195

![Q195](/dump/question-images/q151-200/q195.png)


## Q196

![Q196](/dump/question-images/q151-200/q196.png)



## Q197

![Q197](/dump/question-images/q151-200/q197.png)



## Q198

![Q198](/dump/question-images/q151-200/q198.png)


## Q199

![Q199](/dump/question-images/q151-200/q199.png)

### 1. Extracted Question Summary

**Question 199 (HOTSPOT):**

Which node in the Azure portal should you use to assign a user the Reader role for a resource group? To answer, select the node in the answer area.

NOTE: Each correct selection is worth one point.

**Hot Area Nodes:**

* `Overview`


* `Activity log`


* `Access control (IAM)`


* `Tags`


* `Resource visualizer`


* `Events`


* `Resource costs`


* `Deployments`


* `Security`


* `Policies`


* `Properties`



---

### 2. Correct Answer

**Access control (IAM)**

---

### 3. Verification of Visible Selection / Community Key

*(Section skipped: No node or option is selected, checked, or boxed in the provided image; the answer area options and bottom Answer field are blank.)*

---

### 4. Official Microsoft Justification

* Azure uses **Azure role-based access control (Azure RBAC)** to manage fine-grained authorization to Azure resources.
* Every resource group, subscription, management group, and individual resource blade in the Azure portal features an **Access control (IAM)** blade.
* To grant access permissions—such as assigning the built-in **Reader**, **Contributor**, or **Owner** role to a user, group, or service principal at that resource group scope—you navigate to **Access control (IAM)** $\longrightarrow$ **Add** $\longrightarrow$ **Add role assignment**.

---

### 5. Distractor Analysis (Why Others Are Wrong)

* **Overview:** Displays high-level metadata (subscription, location, resource group ID) and a list of contained resources; it does not assign RBAC permissions.


* **Activity log:** Audits past management plane operations (who performed what action and when); it is for auditing and compliance, not granting permissions.


* **Tags:** Applies key-value metadata to organize, categorize, and track billing for resources; it does not control access permissions.


* **Policies:** Assigns Azure Policy definitions to enforce compliance standards (e.g., allowed locations, required tags); it does not assign user roles like Reader.


* **Security:** Links to Microsoft Defender for Cloud recommendations for the resource group; role assignments are not managed here.


* **Deployments / Properties / Resource costs:** Used to inspect ARM deployment history, technical object identifiers, and cost analysis, respectively.



---

### 6. Exam Keyword / Trap Alert

* **"Assign a role (Reader / Contributor / Owner)"** or **"Manage permissions / RBAC"** $\longrightarrow$ Always points to **Access control (IAM)**.


* Do not confuse **Azure RBAC via Access control (IAM)** (which answers *who has access to perform actions*) with **Policies** (which answers *what resource configurations and compliance rules are allowed*).

## Q200

![Q200](/dump/question-images/q151-200/q200.png)


## Q201

![Q201](/dump/question-images/q201-250/q201.png)

