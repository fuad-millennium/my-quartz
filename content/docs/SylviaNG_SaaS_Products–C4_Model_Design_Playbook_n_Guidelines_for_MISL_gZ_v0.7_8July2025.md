---
marp: true
---

Here’s a **detailed C4 Model Guide & Design Playbook** tailored for **MISL SylviaNG SaaS Products** and all related design documentation efforts. It is designed to be **practical, adaptable, and reusable** for all current and future MISL SaaS Platforms.

---

# 📝 **MISL SylviaNG SaaS Products – C4 Model Design Playbook & Guidelines**

---

## ✅ **1. Purpose of This Document**

This playbook provides a clear, practical guideline for using the **C4 Model** for documenting software architecture within MISL SylviaNG SaaS Products Platform, ensuring:

* Consistency across design docs.
* High adaptability for evolving products.
* Effective communication among engineers, product teams, and stakeholders.

---

## ✅ **2. What is the C4 Model?**

The **C4 Model** is a **hierarchical, structured approach** for visualizing software architecture, created by **Simon Brown**.
It defines **4 hierarchical levels of diagrams**:

| Level | Name                   | Purpose                                                                 | Audience                                  |
| ----- | ---------------------- | ----------------------------------------------------------------------- | ----------------------------------------- |
| 1     | System Context Diagram | Shows system’s scope, external actors, and systems.                     | Business Owners, Stakeholders, Architects |
| 2     | Container Diagram      | Shows high-level technical building blocks (apps, services, databases). | Architects, Engineers, Developers         |
| 3     | Component Diagram      | Shows internal structure within a container (modules, packages).        | Developers, QA Engineers                  |
| 4     | Code Diagram           | Shows actual code-level artifacts (optional).                           | Developers                                |

---

### 📌 **Why C4 for SylviaNG?**

* Highly adaptable for multi-tenant SaaS platforms.
* Focuses on **communication** rather than over-documentation.
* Perfect for evolving Agile environments.

---

## ✅ **3. How to Use C4 Model in MISL Design Docs**

### 🎯 **Always Document Level 1 & 2 in All Products**:

* Level 1 and 2 are mandatory for all SylviaNG SaaS products (Payroll, HRMS, etc.).
* Level 3 and 4 are optional, based on complexity.

---

### ➜ **Level 1: System Context Diagram**

**Purpose:** Identify the product’s ecosystem and its interactions.
**Steps:**

1. Define *who* uses the system (e.g., HR Manager, Employee).
2. Identify *external systems* (e.g., Accounting Systems, SSO Providers).
3. Describe *major data flows* (what moves between actors/systems).

**Key Questions:**

* Who are the primary users?
* What external systems does this product integrate with?
* What does this product do at a high level?

---

### ➜ **Level 2: Container Diagram**

**Purpose:** Identify core building blocks of the product.
**Steps:**

1. Break down the system into containers (e.g., web apps, APIs, DBs, services).
2. Show the technologies used in each container.
3. Document interactions between containers.

**Key Questions:**

* What services, databases, and apps make up this product?
* How do they communicate?
* Which technologies power them?

---

### ➜ **Level 3: Component Diagram (Optional)**

**Purpose:** Decompose containers into internal modules.
**Typical Usage:** Only for complex containers like "Payroll Service" or "HRMS Core Service".

**Key Questions:**

* What modules or packages exist inside this service?
* How do they interact?

---

### ➜ **Level 4: Code Diagram (Optional)**

**Purpose:** Illustrate specific class or function-level details.
**Typical Usage:** Only for critical sections like security modules or shared libraries.

---

## ✅ **4. MISL Standard C4 Diagram Tools**

| Tool Name                 | Usage                                          | Recommended For                       |
| ------------------------- | ---------------------------------------------- | ------------------------------------- |
| **Structurizr DSL**       | Official C4 tool, text-based modeling.         | Engineering / Architecture Teams      |
| **PlantUML**              | Diagramming in Markdown / Git docs.            | Lightweight, version-controlled docs. |
| **Mermaid.js**            | Markdown-native diagramming (GitHub-friendly). | Simpler documentation in Git repos.   |
| **Lucidchart / Draw\.io** | Drag-and-drop visual diagrams.                 | Workshops, Presentations.             |

---

## ✅ **5. MISL C4 Design Document Template Structure**

```plaintext
/docs/architecture/{product}/
  system-context-diagram.md    # Level 1
  container-diagram.md         # Level 2
  component-diagram.md         # Level 3 (optional)
  code-diagram.md              # Level 4 (optional)
```

---

## ✅ **6. Design Documentation Guidelines (Playbook Rules)**

| Rule                          | Description                                                                    |
| ----------------------------- | ------------------------------------------------------------------------------ |
| **1. Keep It Lightweight**    | Focus on clarity and high-value information only. Avoid verbose documentation. |
| **2. Use Version Control**    | Store all diagrams and docs in Git (Documentation-as-Code).                    |
| **3. Link Design to Code**    | Reference relevant repos, modules, or APIs from diagrams.                      |
| **4. Regular Review**         | Review diagrams quarterly or after major architectural changes.                |
| **5. Use Consistent Styles**  | Stick to uniform colors, notations, and diagram layouts across all products.   |
| **6. Prefer Diagrams + Text** | Always explain diagrams in plain text alongside visual models.                 |
| **7. Annotate for Evolution** | Document assumptions, constraints, and known areas of change within diagrams.  |
| **8. Focus on Key Scenarios** | Highlight critical flows (e.g., Payroll Run, Leave Approval) in diagrams.      |

---

## ✅ **7. Recommended Diagram Notations (for Consistency)**

| Element Type     | Symbol / Shape              | Notes                                       |
| ---------------- | --------------------------- | ------------------------------------------- |
| Users            | Stick Figure or Rounded Box | Named roles (e.g., Employee, HR Manager).   |
| External Systems | Rectangle (Dashed Border)   | Identify external apps, APIs, or platforms. |
| Services         | Solid Rectangle             | APIs, Microservices, Backend Logic.         |
| Databases        | Cylinder / DB Icon          | Internal data stores (multi-tenant DBs).    |
| Event Bus        | Cloud / Hexagon             | Kafka, Message Buses, Queues.               |
| Communication    | Labeled Arrows              | Indicate protocol (REST, Kafka, etc.)       |

---

## ✅ **8. Document Review Checklist (For Architects)**

Before finalizing a C4 Diagram, ensure:

* [ ] Clear boundary between internal and external systems.
* [ ] Data flows are explicitly labeled.
* [ ] All major containers are included with tech stacks noted.
* [ ] Sensitive components (auth, compliance) are identified.
* [ ] Diagram complexity matches intended audience.
* [ ] Linked to product repos and other technical docs.

---

## ✅ **9. C4 Diagram Example Labels (For Reference)**

| Label Example                                 | Description                         |
| --------------------------------------------- | ----------------------------------- |
| **"Uses API to submit payroll data"**         | Clarify interaction purpose.        |
| **"Consumes Kafka Topic: payroll.events"**    | For event-driven interactions.      |
| **"Reads from PostgreSQL (multi-tenant DB)"** | Show backend storage relationships. |

---

## ✅ **10. Long-Term Maintenance Recommendations**

* Assign a **System Architecture Owner** for each product to own diagrams.
* Conduct **Architecture Sync Sessions** quarterly.
* Use diagrams in **Design Reviews** and **Onboarding** sessions.
* Track changes via Git history (Markdown + Diagram DSL preferred).

---

## ✅ ✅ Summary

This C4 Model Playbook empowers all MISL SylviaNG SaaS Product teams to:

* Document and evolve architecture collaboratively.
* Align design decisions with business outcomes.
* Communicate effectively across stakeholders and technical teams.

---

