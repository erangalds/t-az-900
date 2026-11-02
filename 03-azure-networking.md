# Azure Networking

### Fundamental Azure Networking Concepts

Before examining traffic paths across zones and regions, three baseline rules govern Azure Virtual Network (VNet) architecture:

1. **VNets and Subnets are Regional Constructs:**
Unlike AWS (where each subnet is locked to a single Availability Zone), an Azure VNet and its subnets **span all Availability Zones** within an Azure Region. You do not create "Zone 1 Subnet" or "Zone 2 Subnet"; resources in Zone 1, Zone 2, and Zone 3 share the exact same subnet IP address pool.
2. **VNet Peering is Non-Transitive:**
Connecting VNet A to VNet B, and VNet B to VNet C, does **not** allow VNet A to talk to VNet C without an intermediary routing appliance (such as an NVA or Azure Firewall).
3. **PaaS Services (Storage & Managed Databases) Access Patterns:**
PaaS endpoints live on public IP addresses by default. To bring them directly into a private subnet, Azure provides **Private Endpoints (Azure Private Link)**, allocating an internal private IP (`10.x.x.x`) to the Storage Account or Database.

---

### Scenario 1: Single Availability Zone (Intra-Zone / Local Subnet Traffic)

In a single datacenter/zone, compute, database, and storage endpoints communicate over ultra-low-latency local physical switching with zero cross-zone transit fees.

#### Architecture & Traffic Flow

```
+---------------------------------------------------------------------------------------+
|  Azure Region (e.g., East US) - Availability Zone 1                                  |
|                                                                                       |
|  Virtual Network A (10.0.0.0/16)                                                      |
|                                                                                       |
|    +-----------------------------+         +-------------------------------------+    |
|    | Subnet: Web-Tier (10.0.1.0/24)|         | Subnet: DB-Tier (10.0.2.0/24)        |    |
|    |                             |         |                                     |    |
|    |  [ App VM 1 ]               | --(1)-->|  [ Azure SQL Managed Instance ]     |    |
|    |  IP: 10.0.1.4               |         |  IP: 10.0.2.10                      |    |
|    +-----------------------------+         +-------------------------------------+    |
|                   |                                                                   |
|                  (2)                                                                  |
|                   v                                                                   |
|    +-----------------------------------------------------------------------------+    |
|    | Subnet: Data-Endpoints (10.0.3.0/24)                                        |    |
|    |                                                                             |    |
|    |  [ Private Endpoint: Azure Blob Storage (LRS) ]                            |    |
|    |  Private IP: 10.0.3.50 (privatelink.blob.core.windows.net)                  |    |
|    +-----------------------------------------------------------------------------+    |
+---------------------------------------------------------------------------------------+

```

* **(1) VM to Database Traffic:**
* The VM initiates a connection to `10.0.2.10` over TCP port 1433.
* Azure's Software Defined Network (SDN) hypervisor layer looks up the routing table (system default route: `10.0.0.0/16 -> Virtual network`).
* Packets route directly over internal top-of-rack datacenter switches with single-digit microsecond latency.


* **(2) VM to Azure Storage:**
* Azure Storage Account is configured with **LRS (Locally Redundant Storage)**, replicating 3 copies inside Zone 1.
* The VM queries `mystorage.blob.core.windows.net`. Azure Private DNS returns `10.0.3.50`.
* Traffic leaves the VM interface and terminates directly at the Private Endpoint NIC in the local subnet.



---

### Scenario 2: Multi-Availability Zone (High-Availability Zonal Redundancy)

When deploying for high availability, workloads are distributed across physically separate datacenters (Zone 1, Zone 2, Zone 3) within the same region.

#### Architecture & Traffic Flow

```
+---------------------------------------------------------------------------------------------------------+
| Azure Region (e.g., East US)                                                                           |
|                                                                                                         |
| VNet 1 (10.0.0.0/16) - SPANS ALL ZONES                                                                   |
|                                                                                                         |
|       AVAILABILITY ZONE 1                         AVAILABILITY ZONE 2                                   |
|  +-----------------------------+             +-----------------------------+                            |
|  | Subnet: Web (10.0.1.0/24)   |             | Subnet: Web (10.0.1.0/24)   |                            |
|  |                             |             |                             |                            |
|  |  [ App VM 1 (Zonal) ]       |             |  [ App VM 2 (Zonal) ]       |                            |
|  |  IP: 10.0.1.4               |             |  IP: 10.0.1.5               |                            |
|  +-----------------------------+             +-----------------------------+                            |
|                 \                                           /                                           |
|                  \                                         /                                            |
|                   v                                       v                                             |
|  +---------------------------------------------------------------------------------------------------+  |
|  | Subnet: DB-Tier (10.0.2.0/24)                                                                     |  |
|  |                                                                                                   |  |
|  |  [ Primary DB (Zone 1) ] <===== Synchronous Replication =====> [ Secondary Standby DB (Zone 2) ]  |  |
|  |  IP: 10.0.2.10                  (High-speed dark fiber)        (Hot Standby Replica)              |  |
|  +---------------------------------------------------------------------------------------------------+  |
|                 |                                                                                       |
|                (3)                                                                                      |
|                 v                                                                                       |
|  +---------------------------------------------------------------------------------------------------+  |
|  | Subnet: Private-Endpoints (10.0.3.0/24)                                                           |  |
|  |                                                                                                   |  |
|  |  [ Private Endpoint: Azure Storage Account (ZRS - Zone-Redundant Storage) ]                       |  |
|  |  Private IP: 10.0.3.100                                                                           |  |
|  +---------------------------------------------------------------------------------------------------+  |
+---------------------------------------------------------------------------------------------------------+

```

* **Network Mechanics Across Zones:**
* Notice that `App VM 1` (Zone 1) and `App VM 2` (Zone 2) belong to the **same subnet** (`10.0.1.0/24`).
* Cross-zone network traffic flows over dedicated high-speed, dense-wavelength optical fiber meshes connecting the physical datacenter facilities, maintaining sub-2-millisecond latency.


* **Database High-Availability:**
* The database engine (e.g., Azure SQL DB with Zone-Redundant configuration) runs an active primary in Zone 1 and an automatic failover replica in Zone 2.
* Every write transaction committed on the primary is synchronously pushed across the inter-zone fiber to Zone 2 before confirming success to the application layer.


* **Storage with ZRS (Zone-Redundant Storage):**
* The storage account writes data synchronously across **three separate availability zones** in the region.
* When `App VM 1` writes a blob to the Private Endpoint (`10.0.3.100`), the Azure Storage fabric handles replication to Zone 2 and Zone 3 under the hood; the VM only sees a single private endpoint IP.



---

### Scenario 3: VNet Peering & Multi-Geo Zones (Cross-Region Disaster Recovery)

When scaling across geographic boundaries (e.g., East US to West US, or North Europe to West Europe), you deploy separate VNets in each region and link them using **Global Virtual Network Peering**.

#### Architecture & Traffic Flow

```
+-------------------------------------------------------+       +-------------------------------------------------------+
| REGION 1: Primary (e.g., East US)                     |       | REGION 2: Secondary / DR (e.g., West US)              |
|                                                       |       |                                                       |
| VNet-East (10.10.0.0/16)                              |       | VNet-West (10.20.0.0/16)                              |
|                                                       |       |                                                       |
| +---------------------------------------------------+ |       | +---------------------------------------------------+ |
| | Subnet: Web (10.10.1.0/24)                        | |       | | Subnet: Web (10.20.1.0/24)                        | |
| |  [ App VM - East ]                                | |       | |  [ App VM - West (Standby) ]                      | |
| |  IP: 10.10.1.4                                    | |       | |  IP: 10.20.1.4                                    | |
| +---------------------------------------------------+ |       | +---------------------------------------------------+ |
|            |                           |              |       |            |                                          |
|           (1)                         (2)             |       |            |                                          |
|            v                           v              |       |            v                                          |
| +---------------------+   +-------------------------+ |       | +---------------------+   +-------------------------+ |
| | Subnet: DB          |   | Subnet: Private-Link    | |       | | Subnet: DB          |   | Subnet: Private-Link    | |
| | (10.10.2.0/24)      |   | (10.10.3.0/24)          | |       | | (10.20.2.0/24)      |   | (10.20.3.0/24)          | |
| |                     |   |                         | |       | |                     |   |                         | |
| | [ Primary DB ]      |   | [ PE: Storage (GZRS) ]  | |       | | [ Read-Replica DB ] |   | [ PE: Storage Secondary]| |
| | IP: 10.10.2.10      |   | IP: 10.10.3.50          | |       | | IP: 10.20.2.10      |   | IP: 10.20.3.50          | |
| +---------------------+   +-------------------------+ |       | +---------------------+   +-------------------------+ |
+-----------|----------------------------|--------------+       +-----------^----------------------------^--------------+
            |                            |                                  |                            |
            |                            |  Global VNet Peering             |                            |
            |                            +==================================+                            |
            |                               (Azure Private Global Backbone)                              |
            |                                                                                            |
            +------------ Asynchronous Failover Group Replication (Geo-DR) ------------------------------+
            |                                                                                            |
            +------------ Asynchronous Storage Data Mirroring (Microsoft Backbone) ----------------------+

```

#### Detailed Network Traffic Flow Across Regions:

1. **Global VNet Peering Routing:**
* Traffic between `VNet-East` (`10.10.0.0/16`) and `VNet-West` (`10.20.0.0/16`) travels entirely on **Microsoft’s private global WAN backbone**, never traversing the public internet.
* No encryption gateways (VPNs) are required; latency is governed strictly by the speed of light over geographical distance (typically 30–70ms between coastlines).


2. **Database Cross-Region Replication (Azure SQL Failover Groups):**
* Unlike intra-region multi-zone replication (which is synchronous), multi-geo database replication is **asynchronous** to avoid slowing down write operations in the primary region due to geographical latency.
* If the East US region suffers a total outage, DNS automatically pivots write traffic to the read-replica in West US at `10.20.2.10`.


3. **Storage Cross-Region Replication (GZRS - Geo-Zone-Redundant Storage):**
* Data is first replicated synchronously across 3 availability zones in East US.
* Then, the Azure storage subsystem **asynchronously replicates** the data to the paired secondary region (West US).
* With **RA-GZRS (Read-Access Geo-Zone-Redundant Storage)**, `App VM - West` can actively query the secondary storage endpoint via its local private endpoint (`10.20.3.50`) for read-only workloads or reporting.



---

### Comparison Matrix: Traffic, Latency & Failure Boundaries

| Scope | Network Boundary | How Traffic Moves | Typical Latency | Failure Blast Radius |
| --- | --- | --- | --- | --- |
| **Single Zone** | Single Subnet / Datacenter | Local switch fabric inside the physical building. | Single-digit $\mu\text{s}$ to $< 1\text{ ms}$ | Individual rack, power supply, or physical datacenter failure. |
| **Multi-Zone (AZ)** | Same VNet & Subnet across Zones | Microsoft metropolitan dark-fiber ring connecting zones. | $\approx 1\text{ ms} - 2\text{ ms}$ | Full datacenter outage (isolated; other zones maintain operations). |
| **Multi-Geo (Peered)** | Distinct Regional VNets (`VNet-A` $\leftrightarrow$ `VNet-B`) | **Global VNet Peering** across Microsoft global fiber backbone. | $30\text{ ms} - 100\text{ ms}+$ (distance dependent) | Entire geographical region failure (weather, power grid, subsea cable sever). |

## Example Use Case

### Core Azure Networking Fundamentals

Three primary principles govern how network traffic is routed, isolated, and connected in Azure:

1. **VNets and Subnets are Regional, Not Zonal:**
Unlike AWS (where every subnet is tied strictly to a single Availability Zone), an Azure Virtual Network (VNet) and each of its subnets **span all Availability Zones** across an Azure Region. Resources deployed into Zone 1, Zone 2, and Zone 3 can share the exact same subnet IP address space without requiring inter-subnet routing.
2. **VNet Peering is Non-Transitive:**
If VNet A is peered to VNet B, and VNet B is peered to VNet C, traffic from VNet A **cannot** reach VNet C directly. Transitive routing requires a central router, such as a Network Virtual Appliance (NVA) or Azure Firewall using User-Defined Routes (UDRs).
3. **PaaS Private Connectivity (Private Endpoints):**
Azure SQL Database and Azure Storage (Blob & Files) natively provide public endpoints. Using **Azure Private Link (Private Endpoints)**, these PaaS services are projected into a designated subnet with an internal, private IP address (`10.x.x.x`), eliminating public Internet exposure.

---

### Architectural Scenarios: End-to-End Traffic Flows

To illustrate how these networking boundaries behave, we examine an enterprise application stack consisting of:

* **Compute:** Application running on Azure Virtual Machines.
* **Relational Data:** Azure SQL Database.
* **Shared File Storage:** Azure Files (mounted as an SMB network share for shared configuration/state).
* **Unstructured Data:** Azure Blob Storage (for document/media uploads).

---

### Scenario 1: Single Availability Zone Deployment (Development / Non-Critical Workload)

All compute, database, and storage endpoints reside inside a single physical datacenter building (Zone 1). Storage redundancy is set to **LRS (Locally Redundant Storage)**, replicating data three times within that single facility.

#### Network Architecture & Traffic Diagram

```
+---------------------------------------------------------------------------------------------------+
| Azure Region: East US (Availability Zone 1)                                                       |
|                                                                                                   |
| Virtual Network: VNet-Core (10.0.0.0/16)                                                          |
|                                                                                                   |
|  +-------------------------------------+         +---------------------------------------------+  |
|  | Subnet: Web-App (10.0.1.0/24)       |         | Subnet: Database (10.0.2.0/24)              |  |
|  |                                     |         |                                             |  |
|  |  [ App VM 1 (Zonal: Zone 1) ]       | ---(1)->|  [ Azure SQL Database (General Purpose) ]   |  |
|  |  IP: 10.0.1.4                       | TCP 1433|  Private Endpoint IP: 10.0.2.10             |  |
|  |                                     |         |  (privatelink.database.windows.net)         |  |
|  +-------------------------------------+         +---------------------------------------------+  |
|                    |                                                                              |
|                   (2)                                                                             |
|                    v                                                                              |
|  +---------------------------------------------------------------------------------------------+  |
|  | Subnet: Private-Endpoints (10.0.3.0/24)                                                     |  |
|  |                                                                                             |  |
|  |  [ Private Endpoint: Azure Files (LRS) ]     [ Private Endpoint: Azure Blob Storage (LRS) ] |  |
|  |  Private IP: 10.0.3.20                       Private IP: 10.0.3.21                          |  |
|  |  Port 445 (SMB Share Mount)                  Port 443 (HTTPS REST Calls)                    |  |
|  +---------------------------------------------------------------------------------------------+  |
+---------------------------------------------------------------------------------------------------+

```

#### Step-by-Step Traffic Flow:

1. **App VM to Database (1):**
* The application queries `app-db.privatelink.database.windows.net`.
* Azure Private DNS resolves the target to `10.0.2.10`.
* Traffic routes across local datacenter switching fabrics over TCP port 1433 with sub-millisecond latency.


2. **App VM to Azure Storage (2):**
* **Azure Files:** App VM mounts the network drive over port 445 (SMB) pointing to `10.0.3.20`. Configuration files are read directly from local LRS storage.
* **Azure Blob:** Media uploads execute HTTPS `PUT` requests over port 443 to `10.0.3.21`.



* **Blast Radius / Risk:** If Zone 1 experiences a facility-level fault (power outage, chiller failure, localized network outage), all compute, database, and storage resources become unreachable simultaneously.

---

### Scenario 2: Multi-Availability Zone Deployment (High-Availability Zonal Redundancy)

Workloads are distributed across two or three physically separate datacenters within the same region. Subnets span across these zones automatically. Storage redundancy is upgraded to **ZRS (Zone-Redundant Storage)**.

#### Network Architecture & Traffic Diagram

```
+---------------------------------------------------------------------------------------------------------+
| Azure Region: East US                                                                                   |
|                                                                                                         |
| Virtual Network: VNet-Core (10.0.0.0/16) - SPANS ALL ZONES                                              |
|                                                                                                         |
|       AVAILABILITY ZONE 1                         AVAILABILITY ZONE 2                                   |
|  +-----------------------------+             +-----------------------------+                            |
|  | Subnet: Web-App             |             | Subnet: Web-App             |                            |
|  | (10.0.1.0/24)               |             | (10.0.1.0/24)               |                            |
|  |                             |             |                             |                            |
|  |  [ App VM 1 (Zone 1) ]      |             |  [ App VM 2 (Zone 2) ]      |                            |
|  |  IP: 10.0.1.4               |             |  IP: 10.0.1.5               |                            |
|  +-----------------------------+             +-----------------------------+                            |
|                 \                                           /                                           |
|                  \--- [ Standard Load Balancer (Zone-Redundant) ]                                       |
|                                       |                                                                 |
|                                       | (1) Route to Primary DB                                         |
|                                       v                                                                 |
|  +---------------------------------------------------------------------------------------------------+  |
|  | Subnet: Database (10.0.2.0/24)                                                                    |  |
|  |                                                                                                   |  |
|  |  [ Primary SQL Replica (Zone 1) ] <===== Synchronous Replication =====> [ Standby Replica (Zone 2)]|
|  |  Private Endpoint IP: 10.0.2.10          (Inter-Zone Dark Fiber)         (Hot Standby Node)       |  |
|  +---------------------------------------------------------------------------------------------------+  |
|                                       |                                                                 |
|                                      (2) Inter-Zone Storage Access                                      |
|                                       v                                                                 |
|  +---------------------------------------------------------------------------------------------------+  |
|  | Subnet: Private-Endpoints (10.0.3.0/24)                                                           |  |
|  |                                                                                                   |  |
|  |  [ Private Endpoint: Azure Files (ZRS) ]       [ Private Endpoint: Azure Blob (ZRS) ]             |  |
|  |  Private IP: 10.0.3.50                         Private IP: 10.0.3.51                              |  |
|  |  Replicated synchronously to Z1, Z2, and Z3     Replicated synchronously to Z1, Z2, and Z3         |  |
|  +---------------------------------------------------------------------------------------------------+  |
+---------------------------------------------------------------------------------------------------------+

```

#### Step-by-Step Traffic Flow:

1. **VM Inter-Zone Database Routing (1):**
* Both `App VM 1` (Zone 1) and `App VM 2` (Zone 2) route SQL queries to `10.0.2.10`.
* For `App VM 2`, traffic crosses the metropolitan inter-zone dark fiber ring ($\approx 1\text{ ms} - 2\text{ ms}$ latency).
* **Synchronous Database Replication:** Every database write transaction received on the Primary Replica in Zone 1 is synchronously acknowledged by the standby replica in Zone 2 before the transaction is marked as committed.


2. **Multi-Zone Storage Access (2):**
* Regardless of whether `App VM 1` or `App VM 2` sends data to the Private Endpoints (`10.0.3.50` / `10.0.3.51`), Azure Storage synchronously commits all file and blob writes across three physical availability zones before returning success.



* **Blast Radius / Resilience:** If Availability Zone 1 suffers a total facility failure, Azure detects the outage. The load balancer stops sending requests to VM 1, Azure SQL automatically promotes the Zone 2 replica to Primary, and VM 2 continues processing without application downtime ($RPO = 0$).

---

### Scenario 3: Multi-Geo Cross-Region Deployment (Disaster Recovery & Global Business Continuity)

Two separate Azure regions (Primary and DR/Secondary) joined by **Global VNet Peering**. Storage uses **GZRS (Geo-Zone-Redundant Storage)** and SQL uses **Azure SQL Auto-Failover Groups**.

#### Network Architecture & Traffic Diagram

```
+-------------------------------------------------------+       +-------------------------------------------------------+
| PRIMARY REGION: East US                               |       | SECONDARY / DR REGION: West US                        |
|                                                       |       |                                                       |
| VNet-East (10.10.0.0/16)                              |       | VNet-West (10.20.0.0/16)                              |
|                                                       |       |                                                       |
| +---------------------------------------------------+ |       | +---------------------------------------------------+ |
| | Subnet: Web-App (10.10.1.0/24)                    | |       | | Subnet: Web-App (10.20.1.0/24)                    | |
| |   [ Active Production VMs ]                       | |       | |   [ DR Standby VMs (Scaled down) ]                | |
| |   IP: 10.10.1.4, 10.10.1.5                        | |       | |   IP: 10.20.1.4, 10.20.1.5                        | |
| +---------------------------------------------------+ |       | +---------------------------------------------------+ |
|              |                           |            |       |              |                           |            |
|             (1)                         (2)           |       |              |                           |            |
|              v                           v            |       |              v                           v            |
| +-------------------------+ +-----------------------+ |       | +-------------------------+ +-----------------------+ |
| | Subnet: Database        | | Subnet: Private-Link  | |       | | Subnet: Database        | | Subnet: Private-Link  | |
| | (10.10.2.0/24)          | | (10.10.3.0/24)        | |       | | (10.20.2.0/24)          | | (10.20.3.0/24)        | |
| |                         | |                       | |       | |                         | |                       | |
| | [ Primary SQL DB ]      | | [ PE: Blob & Files ]  | |       | | [ Secondary SQL DB ]    | | [ PE: Blob (RA-GZRS)] | |
| | IP: 10.10.2.10          | | IP: 10.10.3.50        | |       | | (Read-Only Replica)     | | IP: 10.20.3.50        | |
| |                         | |                       | |       | | IP: 10.20.2.10          | | (Read Secondary)      | |
| +-------------------------+ +-----------------------+ |       | +-------------------------+ +-----------------------+ |
+--------------|---------------------------|------------+       +--------------^---------------------------^------------+
               |                           |                                   |                           |
               |                           |      Global VNet Peering          |                           |
               |                           +===================================+                           |
               |                               (Microsoft Global WAN Backbone)                             |
               |                                                                                           |
               +--- (3) Asynchronous SQL Auto-Failover Group Replication (TDS Port 1433) -------------------+
               |                                                                                           |
               +--- (4) Asynchronous Storage Geo-Replication (Underlying Azure Storage Fabric) ------------+

```

#### Step-by-Step Traffic Flow:

1. **Local Regional Ingress (1 & 2):**
* Under standard operational conditions, all live production traffic is serviced locally inside `VNet-East`.
* VMs in East US write to the local SQL Primary DB (`10.10.2.10`) and Azure Files/Blob endpoints (`10.10.3.50`) with sub-millisecond local latency.


2. **Cross-Region Peering Backbone Transit:**
* When administrators or services communicate between `VNet-East` and `VNet-West`, packets traverse **Global VNet Peering**.
* This traffic runs directly over Microsoft's private, encrypted global fiber network, completely isolated from the public internet.


3. **Database Asynchronous Geo-Replication (3):**
* Because East US and West US are separated by thousands of miles, synchronous replication would introduce unacceptable write latency.
* Azure SQL uses an **Auto-Failover Group** to replicate transaction logs **asynchronously** to the secondary database in West US (`10.20.2.10`).
* The secondary replica remains in read-only mode and can serve offloaded read/reporting traffic.


4. **Storage Geo-Replication (GZRS / RA-GZRS) (4):**
* Data written to Blob storage in East US is first synchronously protected across 3 availability zones locally.
* Then, Azure Storage asynchronously copies the data across the Microsoft backbone to the West US paired region.
* With **Read-Access Geo-Zone-Redundant Storage (RA-GZRS)**, the DR standby VMs in West US can read files and data from the local secondary storage endpoint (`10.20.3.50`) without querying East US.



* **Failover Scenario:** If a regional catastrophe disrupts the entire East US region, Microsoft or the customer initiates a failover. The DNS read-write listener points traffic to `VNet-West`, the secondary database becomes the primary read-write instance, and the standby VMs begin serving application traffic immediately.

---

### Architectural Summary Matrix

| Metric / Attribute | Single Availability Zone | Multi-Availability Zone | Multi-Geo Cross-Region |
| --- | --- | --- | --- |
| **VNet Footprint** | Single Regional VNet | Single Regional VNet (Zonal Subnets) | Distinct Regional VNets via Global Peering |
| **VM Placement** | Single Zonal VM or Default | Distributed across Zones 1, 2, and 3 | Active/Standby VMs in separate regions |
| **SQL Database Setup** | Locally Hosted (General Purpose) | Zone-Redundant (Sync Auto-Failover) | Auto-Failover Groups (Async Geo-Replication) |
| **Storage SKU** | LRS (3 copies in 1 datacenter) | ZRS (3 copies across 3 physical zones) | GZRS / RA-GZRS (ZRS locally + Async Geo-copy) |
| **Average Latency** | $< 1\text{ ms}$ | $\approx 1\text{ ms} - 2\text{ ms}$ | $30\text{ ms} - 70\text{ ms}+$ (Speed of light over distance) |
| **Disaster Boundary** | Rack / Building outage | Single Datacenter facility loss | Full Regional / Geo-political outage |