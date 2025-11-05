# Overview of Microsoft Threat Modeling (MTM)

The **Microsoft Threat Modeling** approach is primarily facilitated by the **Microsoft Threat Modeling Tool (MTMT)**.  
It is fundamentally based on the **STRIDE** methodology and is a highly **Application/Software-Centric** method used to identify design-level security flaws early in the development lifecycle.

---

## 1. Core Focus & Purpose

- **Focus:** Identifying security threats within the design and architecture of a software application.  
- **Goal:** To help designers and developers create a visual representation of their system, enumerate potential threats, and derive appropriate mitigations before code is written.  
- **Approach Type:** Application/Software-Centric (specifically leveraging **STRIDE**).

---

## 2. The Six-Step Process (As Used in MTMT)

| Step | Action | Description |
|------|---------|-------------|
| **1. Identify the Assets** | Define Value | Determine what the application is trying to protect (e.g., user PII, financial data, service availability). |
| **2. Architecture Overview** | Define Scope | Understand the high-level system components, technologies, and deployment environment. |
| **3. Decompose the Application** | Visualize Model | Use the MTMT to create a **Data Flow Diagram (DFD)** showing Processes, Data Stores, External Interactors, and Trust Boundaries. |
| **4. Identify Threats** | Apply STRIDE | Apply the **STRIDE** model to every element of the DFD to automatically or manually generate a list of potential threats. |
| **5. Documenting Threats** | Catalogue & Mitigate | List each threat, assign it an initial priority, and propose specific countermeasures/mitigations. |
| **6. Rating the Threats** | Risk Assessment | Evaluate the severity and likelihood of each threat using a risk model like **DREAD**, **CVSS**, or a custom rating. |

---

## 3. Key Concepts and Terminology

### **Data Flow Diagram (DFD)**
The core deliverable of the modeling phase. It visualizes the flow of data through the system and is built using four primary elements:

- **External Interactors (Squares):** Users or external systems that send or receive data.  
- **Processes (Circles):** Where data is processed, transformed, or stored.  
- **Data Stores (Parallel Lines/Containers):** Where data resides (databases, files, memory).  
- **Data Flows (Arrows):** The movement of data between components.  

**Trust Boundaries:**  
Lines drawn on the DFD representing where the level of trust changes (e.g., the network boundary between a client browser and a server). Threats are often generated when data crosses these boundaries.

---

### **STRIDE Categories**

| Threat Category | Property Violated | Application Component |
|-----------------|-------------------|------------------------|
| **Spoofing** | Authentication | Interactors/Users |
| **Tampering** | Integrity | Data Flow/Data Store |
| **Repudiation** | Non-Repudiation | Process/Data Store |
| **Information Disclosure** | Confidentiality | Data Flow/Data Store |
| **Denial of Service** | Availability | Process/Data Store |
| **Elevation of Privilege** | Authorization | Process/User |

---

## 4. Benefits and Limitations

| **Benefit** | **Limitation** |
|--------------|----------------|
| **Systematic Coverage:** STRIDE ensures a comprehensive look at common technical threat categories. | **Technical Focus:** Primarily targets design and code flaws, often neglecting broader organizational, human, or physical risks. |
| **Early Integration:** Encourages security thinking early in the design phase, making fixes cheaper and easier. | **Diagram Dependency:** The quality of the threat model is heavily reliant on the accuracy and completeness of the DFD. |
| **Automation:** The MTMT automatically generates threats based on the DFD components and trust boundaries. | **Limited to Web Apps:** While flexible, it is most frequently and successfully applied to web, cloud, and enterprise applications. |

---
