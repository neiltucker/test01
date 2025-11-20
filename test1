This revised Module 1 provides highly detailed lecture content for the instructor, ensuring robust material (approaching 5-10 pages per lesson, separated from demonstrations) that directly supports the advanced **SCVMM 2025** curriculum and all subsequent review questions.

***

# Module 1: Installing and Configuring Microsoft Virtual Machine Manager (3.5 Hours)

This module describes how to integrate **Virtual Machine Manager (SCVMM) 2025** and server virtualization, install **SCVMM**, add hosts, manage host groups, and configure high availability for the datacenter fabric.

---
# Lesson 1.1: Merge system center and server virtualization

**(Approximate time: 30 minutes)**

## Lecture material

### 1. The SCVMM 2025 role as the centralized management platform

#### Purpose and scope
*   The core functionality of **SCVMM 2025** is its role as a **datacenter management solution**. **SCVMM** is a key component of the System Center suite used to configure, manage, and transform traditional datacenters.
*   The fundamental difference between **Hyper-V** and **SCVMM 2025** is that **Hyper-V is the underlying virtualization technology** (**hypervisor**), while **SCVMM is the centralized management platform** designed for enterprise virtualization environments.
*   **SCVMM 2025** acts as the management layer that configures, manages, and transforms datacenter components—including virtualization servers, networking, and storage—as a **single fabric**.
*   **Hyper-V** operates at the host level, managing individual virtual machines (VMs) and local components, such as virtual switches, directly. **Hyper-V** is the engine that provides the virtualized hardware equivalents, enabling multiple operating systems to run concurrently on a single physical host.

#### Scale limits and environment management
*   **SCVMM** is designed to manage and optimize a **large-scale virtualization infrastructure**.
*   **SCVMM 2025** supports tested scale limits of managing up to **1000 physical hosts** and **25,000 virtual machines**. It also supports managing up to **1000 services** and **1000 user roles**.
*   The **SCVMM** role provides a unified management experience across on-premises, service provider, and Azure cloud environments.
*   **SCVMM** supports the management of both **Hyper-V** and **VMware** virtualization hosts and clusters.

---
### 2. Key tasks managed by SCVMM 2025

#### Virtualization hosts and clusters
*   **SCVMM** adds, provisions, and manages hosts running **Windows Server 2025**.
*   **SCVMM** manages the entire lifecycle of VMs and services from creation and deployment to patching and retirement.
*   **High-scale support:** Through its management of **Windows Server 2025 Hyper-V**, **SCVMM** manages Generation 2 VMs that can support up to **248 virtual processors** and **240 TB of RAM**.

#### Networking and storage fabric
*   **Networking:** **SCVMM** manages the complete virtualization networking stack. Tasks include:
    *   Adding networking resources to the **SCVMM fabric**, including **network sites defined by IP subnets** and virtual LANs (VLANs).
    *   Managing **logical switches** and virtual network adapters.
    *   Providing network virtualization, including support for creating and managing virtual networks and network gateways.
*   **Storage:** **SCVMM** can discover, classify, provision, allocate, and assign local and remote storage.
    *   It supports block storage technologies like fiber channel (FC), iSCSI, and serial attached SCSI (SAS) storage area networks (SANs).
    *   The **VMM Storage Fabric** feature helps monitor the health and operational status of storage pools, logical unit numbers (LUNs), and physical disks.

#### Library and hybrid management
*   **Library:** The **VMM Library** retains a repository of file-based resources (virtual hard disks, ISO images, scripts) and non-file-based resources (templates, profiles). These resources are used to standardize the creation and deployment of VMs and services to **private clouds**.
*   **Hybrid Management:** **SCVMM 2025** primarily integrates with Azure through **Azure Arc-enabled SCVMM**, enabling VM self-service operations using Azure role-based access control (**RBAC**). This enhanced integration provides access to Azure management services like Microsoft Defender for Cloud and Azure Monitor.

---
# Demonstration 1.1: Comparing hyper-v manager and SCVMM console scope

**Objective:** Visually demonstrate the difference between host-level management (**Hyper-V Manager**) and fabric-level management (**SCVMM Console**), emphasizing the "single fabric" view.

**Steps (Instructor):**
1.  **Open hyper-v manager:** Connect to a single **Windows Server 2025** host machine. Show that the view is limited to the local host's virtual machines, local switches, and basic settings.
2.  **Open SCVMM 2025 console:** Connect to the **VMM Management Server** **VM556012**.
3.  **Navigate the fabric workspace:** Navigate to the **Fabric** workspace in the **SCVMM Console**.
4.  **Show centralized management:** Explicitly show the broader scope available from this single console. Expand and review the following nodes:
    *   **Servers:** Demonstrate viewing multiple hosts/clusters and confirming the host operating system versions (e.g., **Windows Server 2025** host support).
    *   **Storage:** Show the ability to discover, classify, and provision storage arrays and pools, including support for **iSCSI** or fiber channel storage.
    *   **Networking** nodes: Show the management of logical networks, virtual switches, and network sites.
5.  **Conclusion:** Emphasize that **SCVMM** orchestrates the entire datacenter infrastructure (**single fabric**), whereas **Hyper-V Manager** only manages the local host's hypervisor functions.

---
# Lesson 1.2: Overview of VMM and installation

**(Approximate time: 45 minutes)**

## Lecture material

### 1. VMM 2025 system requirements (server and host)

#### VMM management server OS and prerequisites
*   **Operating System:** The **VMM Management Server** must run on **Windows Server 2025** (desktop experience or server core).
*   **Domain Membership:** The **SCVMM** management server must be a **domain member**.
*   **Computer Name:** The computer name should not exceed 15 characters.

#### Critical software dependencies
*   **Windows ADK:** Installation requires **Windows ADK for Windows 11 and Windows Server 2025** and the Windows PE add-on for ADK. This is required for deployment and imaging processes used in VM provisioning.
*   **.NET and PowerShell:** A minimum requirement of .NET 4.6 and **PowerShell** 5.1 is necessary on the **VMM server**.

#### Hardware requirements (recommended and minimum)
*   **Processor (Recommended):** 16-core, 2.66 GHz CPU.
*   **RAM (Recommended):** **16 GB**. This is particularly important because the installer generates a warning if insufficient RAM is detected.
    *   *Note on VM deployment:* If the **SCVMM** management server is installed on a VM (such as **VM556012**) and dynamic memory is used, the minimum start RAM must be set to at least **4096 MB**.
*   **Storage (Recommended):** **10 GB** minimum hard drive space on the **VMM server** itself, and **200 GB** recommended for the **VMM database**.

#### Hyper-V Host Requirements (Reminder)
*   The **VMM Management Server** should *not* be installed on a server already running **Hyper-V**.
*   The virtualization support (Intel VTx or AMD-V) must be enabled in the BIOS or UEFI of the physical hosts.

---
### 2. VMM database requirements

#### Supported SQL versions and utilities
*   **SCVMM 2025** supports **SQL Server 2022** and SQL Server 2019.
*   The **VMM database** should have a recommended size of **200 GB**.
*   **External SQL Connectivity:** If the VMM database is located on a remote SQL server, the **SCVMM** installer needs the corresponding **SQL Server command-line utilities** (2019 or 2022) installed on the **VMM Management Server** to communicate with the database.

#### Deployment options for VMM
*   **Highly Available Deployment:** The **VMM Management Server** can be deployed in a **highly available cluster** to ensure centralized management remains operational even during a server failure.
*   **Console Installation:** The **VMM Console** can be installed remotely on supported client operating systems (e.g., Windows 10/11 Enterprise) or **Windows Server 2025**.

---
# Demonstration 1.2: VMM 2025 installation walkthrough and prerequisite check

**Objective:** Show the **SCVMM** setup process, focusing on confirming prerequisites and understanding the service account requirement.

**Steps (Instructor):**
1.  **Launch the SCVMM 2025 setup:** Begin the installation of the **VMM Management Server** and **Console** on **VM556012**.
2.  **Product key and license:** Confirm acceptance of the license agreement and proceed through the initial screens.
3.  **Installation Path:** Show how to change the default installation path, noting that **10 GB** of space is recommended on the server.
4.  **Prerequisite check:** Show the screen where the installer identifies missing components.
    *   Highlight the critical requirement for the **Windows ADK for Windows Server 2025** and the **Windows PE add-on for ADK**.
    *   Note the warning that appears if the RAM is below the recommended **16 GB**.
5.  **SQL server confirmation:** Confirm that if SQL is external, the installer checks for the necessary **SQL Server command-line utilities**. If SQL is local, verify the database instance name and ports.
6.  **Service account:** Identify where the installation prompts for the **VMM service account** credentials (e.g., `svc_vmm`). **Explain that this account must be separate from the administrator account used to add Hyper-V hosts later**, which is enforced by security restrictions.
7.  **Port and library settings:** Review the default firewall ports used by **SCVMM** (e.g., TCP port 8100 for the console) and the default library share location.
8.  **Final Summary:** Review the summary before proceeding to the final installation step.

---
# Lesson 1.3: Add and manage host groups

**(Approximate time: 45 minutes)**

## Lecture material

### 1. Adding hyper-v hosts to the fabric

#### Host integration process
*   **SCVMM 2025** allows administrators to integrate **Windows Server 2025 Hyper-V hosts** into the **VMM fabric**.
*   **VMM Agent:** When a host is added, the **VMM Console** automatically installs a **VMM agent** on that hypervisor host. This agent is essential for facilitating centralized management, communication (e.g., through default firewall ports), and executing job operations on the host.
*   **Host Groups:** Once added, **SCVMM** manages the host properties and logically groups the hosts into **Host Groups**.
    *   **Purpose:** Host groups are used for delegated administration (allowing specific user roles access to certain groups), applying common configuration settings (e.g., storage QoS policies), and managing resources efficiently.

---
### 2. Security and account requirements for host addition

#### Security model and separation of duties
*   **Crucial Best Practice:** The account used to add a **Hyper-V** host to **SCVMM** **must be an administrator on the Hyper-V host server itself**. This is a core security requirement.
*   **VMM Service Account Restriction:** The system account used to install the **SCVMM service/server cannot be used** to add hypervisors to be managed.
    *   This is enforced by design for security and administrative delegation, ensuring separation between the **SCVMM** management function and the individual host administration function.
    *   Attempting to use the **VMM service account** (`svc_vmm`) for host discovery will fail, forcing the administrator to specify a **different account** (typically a dedicated Run As account with local host administrator privileges).

#### Host property management
*   Once successfully onboarded, **SCVMM** automatically collects and displays detailed host information in the **Fabric** workspace:
    *   Host status (e.g., **OK** or `Needs Attention`).
    *   Host operating system (confirming **Windows Server 2025** support).
    *   List of all **Virtual Machines** currently running on that host.

---
# Demonstration 1.3: Adding a windows server 2025 host (security focus)

**Objective:** Demonstrate the security requirement that the host administration credentials must be separate from the **SCVMM** service account, and successfully onboard a **Windows Server 2025** host.

**Steps (Instructor):**
1.  **Launch VMM console:** Open the console on **VM556012** and navigate to the **Fabric** workspace.
2.  **Initiate host addition:** Right-click **Servers** and start the process to **Add Resources** > **Hyper-V hosts and clusters**.
3.  **Attempt 1 (failure scenario):** On the **Credentials** page, attempt to use the VMM Service Account credentials (e.g., `svc_vmm`) for host discovery.
    *   Show the resulting error message confirming that a **different account** must be specified.
4.  **Attempt 2 (success scenario):** Re-initiate the process and use a dedicated administrative Run As account (e.g., `Admin_Host`) that has administrator rights on the target **Windows Server 2025 Hyper-V** host (`WS2025-HV01`).
5.  **Verify agent installation:** Observe the progress bar and confirm that **SCVMM** successfully installs the **VMM agent** on the remote **Hyper-V** server.
6.  **Verify host in fabric:** Confirm that the **Windows Server 2025** host now appears in the **Fabric** workspace under the specified **Host Group**.

---
# Lesson 1.4: Configuring high availability and upgrades

**(Approximate time: 45 minutes)**

## Lecture material

### 1. High availability for hyper-v clusters

#### Live migration and clustering
*   **SCVMM 2025** manages **Hyper-V** host clusters, providing continuous uptime by supporting **Live Migration**.
*   **Live Migration** is the process where a VM moves from one **Hyper-V** host to another within a cluster without downtime or interruption, which is crucial for maintenance and balancing. **SCVMM** orchestrates this migration process across the fabric.

#### VM checkpoints (saved states)
*   **SCVMM** manages VM checkpoints, which are saved states of a VM at a specific point in time, allowing reversion to that state later.
*   **Windows Server 2025 Hyper-V** offers two distinct types of checkpoints:
    *   **Standard checkpoint:** Captures the state of the VM, including memory and device state. This is suitable for **development and testing environments** where quick reversion is the priority. It **does not enable application consistency**.
    *   **Production checkpoint:** Creates a consistent state by integrating with the VM's backup solutions, such as **Volume Shadow Copy Service (VSS)** for Windows or file system freeze for Linux. This is **recommended for production environments** as the application state is maintained, ensuring integrity for systems like SQL Server or Active Directory. **Production checkpoints are enabled by default** in **Windows Server 2025 Hyper-V**.

---
### 2. High availability for the VMM management server

*   The **VMM management server** itself can be deployed in a **highly available cluster** to ensure that centralized management remains operational even if one server fails.
*   This highly available deployment requires that the **VMM** server be a domain member and often utilizes clustered SQL Server for the database.

---
### 3. VMM 2025 upgrade and security focus

#### Protocol modernization
*   **SCVMM 2025** continues the theme of infrastructure modernization and enhanced security.
*   **TLS 1.3 Support:** **SCVMM 2025** works with **TLS 1.3** and significantly reduces dependence on older, less secure authentication protocols like CredSSP and NTLM. This enhances the security posture for **Windows Servers**.

#### VM and host security
*   **Generation 2 Default:** All VMs created with **SCVMM 2025** will **default to Generation 2** architecture. **Generation 2** architecture uses UEFI firmware, which is more secure and supports features like **vTPM** (Virtual Trusted Platform Module).
*   **High Scale:** **Generation 2** virtual machines on **Windows Server 2025** can support massive scaling, up to **248 virtual processors** and **240 TB of RAM**.

#### Hybrid cloud integration
*   **Azure Arc:** The strategic focus of **SCVMM 2025** is on **Azure Arc-enabled SCVMM** integration. This is the modern alternative to older Azure integration capabilities (like Azure VM management or Azure Update Management v1) that are no longer supported in **VMM 2025**.
*   **Azure Stack HCI:** **VMM 2025** supports managing **Azure Stack HCI 23H2 clusters**, providing unified control of heterogeneous infrastructure through the **single management plane**.

---
# Demonstration 1.4: Exploring cluster and checkpoint management

**Objective:** Show where HA and the critical checkpoint settings are managed in the virtualization stack.

**Steps (Instructor):**
1.  **VMM cluster management:** Navigate the **VMM Console** to the **Fabric** workspace and select the **Servers** node. Show where cluster properties and host affinity settings can be managed by **SCVMM**.
2.  **Live migration settings (hyper-v manager):** Open **Hyper-V Manager** settings for a **Windows Server 2025** host. Show where **Live Migration** is enabled and configured, including settings for simultaneous live migrations.
3.  **Checkpoint configuration:** In **Hyper-V Manager**, open the **Settings** dialog for a guest VM.
    *   Show the **Checkpoint Type** section.
    *   Highlight the default setting of **Production checkpoint**. Explain that this uses VSS for application consistency, making it superior to the **Standard checkpoint** for production use.
4.  **VMM security posture review (upgrade focus):** Briefly review an **SCVMM** property page or presentation slide confirming the use of **TLS 1.3** and the reduction of dependency on legacy protocols like CredSSP and NTLM, emphasizing the security improvements introduced in **SCVMM 2025**.

---
# Student lab exercise 1: VMM 2025 installation verification and hyper-v host onboarding

**(Approximate time: 60 minutes)**

**Scenario:** As a datacenter administrator, you need to verify the core components of the newly deployed **SCVMM 2025** Management Server and begin onboarding the first **Windows Server 2025 Hyper-V** host into the **VMM fabric**.

**Requirements:**
*   You are logged into the **SCVMM Management Server VM** named **VM556012**.
*   **Login:** `Student` with the password `Pa$$w0rdPa$$w0rd`.
*   A separate VM, `WS2025-HV01` (running **Windows Server 2025** with **Hyper-V** role installed), is available in the domain.
*   You have two domain accounts: `svc_vmm` (the **SCVMM** service account) and `Admin_Host` (a separate account with administrative rights on `WS2025-HV01`).

### Task 1: Verify SCVMM 2025 pre-requisites
1.  Verify the installed operating system on the **VMM Management Server VM556012** is **Windows Server 2025**.
2.  Open **PowerShell** as an administrator.
3.  Verify the necessary ADK components were installed (reviewing the required **Windows ADK for Windows 11 and Windows Server 2025** and the Windows PE add-on).
4.  Verify that **VM556012** is a member of the domain.

### Task 2: Attempt and fail to add a hyper-v host (security check)
1.  Launch the **VMM 2025 Console** on **VM556012**.
2.  Navigate to the **Fabric** workspace.
3.  Right-click on **Servers** and select **Add Resources** > **Hyper-V hosts and clusters**.
4.  Specify the resources as **Windows Server computers in an Active Directory domain**.
5.  On the **Credentials** page, attempt to create a Run As account using the **VMM Service Account** (`svc_vmm`) to discover the host `WS2025-HV01`.
6.  Observe and document the error message received, confirming that this **VMM service account cannot be used for host addition**.

### Task 3: Successfully onboard the windows server 2025 host
1.  Re-initiate the **Add Resources** wizard.
2.  On the **Credentials** page, create a new Run As account using the dedicated **Host Admin account** (`Admin_Host`). This account **must be an administrator on the Hyper-V host server itself**.
3.  Specify the host name, `WS2025-HV01`, for discovery.
4.  Select the discovered host and associate it with the **All Hosts** group.
5.  Review the settings summary and click **Finish**.
6.  Wait for the job status to show **Completed** (indicating the **VMM agent** has been installed on `WS2025-HV01`).

### Task 4: Verify the onboarded host and its capabilities
1.  In the **VMM Console** on **VM556012**, locate `WS2025-HV01` in the **Fabric** workspace.
2.  Review the host status (should be **OK**).
3.  Review the host **Properties**, specifically confirming that the host operating system is recognized as **Windows Server 2025**.
4.  View the list of **Virtual Machines** currently running on the host via the **VMM Console**.

---
# Module 1 review

**(Approximate time: 15 minutes)**

Choose the single best answer for each question.

**1. What is the fundamental difference in purpose between Hyper-V (Windows Server 2025) and SCVMM 2025?**
A. **Hyper-V** manages up to **1000 hosts**, while **SCVMM** manages local storage.
B. **Hyper-V** is the centralized management platform, while **SCVMM** is the host **hypervisor**.
C. **Hyper-V** is the underlying virtualization technology (**hypervisor**), while **SCVMM** is the centralized management solution (**fabric** manager).
D. **Hyper-V** only supports **Generation 1** VMs, while **SCVMM** only supports **Generation 2** VMs.

**2. Which Windows Server 2025 component is a critical prerequisite that must be installed on the SCVMM Management Server prior to VMM installation?**
A. IIS web server role
B. **Windows ADK for Windows 11 and Windows Server 2025** and its **PE Add-on**.
C. Microsoft exchange server 2025
D. SQL server reporting services (SSRS)

**3. What is the recommended amount of RAM for the SCVMM 2025 Management Server?**
A. 4 GB
B. **16 GB**.
C. 32 GB
D. 240 TB

**4. When adding a Windows Server 2025 Hyper-V host to the SCVMM fabric, what is the critical security requirement regarding the credentials used?**
A. The credentials must be the **VMM Service Account** for seamless integration.
B. The credentials must be stored securely in Azure key vault before use.
C. The credentials must be a separate administrator account with rights on the target **Hyper-V** host, **distinct from the VMM service account**.
D. The credentials must use CredSSP authentication for **TLS 1.3** support.

**5. What type of checkpoint is recommended for production workloads on a Hyper-V VM managed by SCVMM 2025 because it uses volume shadow copy service (VSS) to ensure application-consistency?**
A. **Standard checkpoint**
B. Isolated checkpoint
C. **Production checkpoint**.
D. Application checkpoint

### Answers:
1.  **C.** **Hyper-V** is the underlying virtualization technology (**hypervisor**), while **SCVMM** is the centralized management solution (**fabric** manager).
2.  **B.** **VMM 2025** requires the **Windows ADK for Windows 11 and Windows Server 2025** and the **Windows PE add-on for ADK**.
3.  **B.** The recommended RAM for the **VMM** server is **16 GB**.
4.  **C.** You cannot use the same **VMM service account**; a separate administrator account on the **hypervisor** host is required.
5.  **C.** **Production checkpoints** are application-consistent and are intended for use in production environments.

---
# Q&A

**(Approximate time: 15 minutes)**

The instructor will now open the floor for questions regarding the material covered in Module 1: Installing and Configuring Microsoft Virtual Machine Manager (2025). This Q&A session is an opportunity to clarify any concepts related to **SCVMM 2025** prerequisites, installation, host addition, or high availability features.
