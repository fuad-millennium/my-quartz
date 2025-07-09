---
marp: true
---
Here’s a **sample “Context & Capability Map” Agile Design Document** for the **SylviaNG SaaS Payroll & HRMS Products Platform**, using **C4 Model Levels 1 & 2**.

This document is intentionally designed to evolve along with the platform and remain concise yet informative.

---

# 📝 **SylviaNG SaaS Payroll & HRMS Platform – Context & Capability Map (C4 Model: Level 1 & 2)**

---

## **1. Document Version**

* **Version:** 1.0
* **Date:** YYYY-MM-DD
* **Owner:** Solution Architect / Engineering Lead
* **Contributors:** \[List Names & Roles]

---

## **2. Purpose**

This document provides a **high-level architectural overview** of the SylviaNG SaaS Payroll & HRMS Platform using the **C4 Model**:

* **Level 1:** System Context Diagram (external relationships, main users).
* **Level 2:** Container Diagram (internal subsystems and interactions).

---

## **3. System Context Diagram (C4 Level 1)**

### ➜ **System Purpose:**

The SylviaNG SaaS Payroll & HRMS Platform automates payroll, HR operations, employee management, and compliance processes for businesses in a multi-tenant SaaS environment.

### ➜ **Primary Users & External Systems:**

| Actor/System                                         | Interaction Type              | Purpose                                             |
| ---------------------------------------------------- | ----------------------------- | --------------------------------------------------- |
| HR Managers & Payroll Specialists                    | Web App / API                 | Manage payroll, leave, attendance, and compliance.  |
| Employees                                            | Mobile App / ESS Web Portal   | Access payslips, apply leave, manage personal info. |
| External Accounting Systems (e.g., Xero, QuickBooks) | REST APIs / Integration Layer | Push payroll data, synchronize accounts.            |
| Tax Authorities (Gov Portals)                        | API / File Upload             | Submit tax reports and filings.                     |
| Identity Providers (Okta, Azure AD, Google)          | OAuth 2.0 / SAML SSO          | Single Sign-On Authentication.                      |
| Email & Notification Services                        | SMTP / API                    | Send alerts, payslips, notifications.               |

---

### ➜ **System Context Diagram (Visual Representation):**

```
[HR Manager] → [SylviaNG Payroll & HRMS Platform] ← [Employees]
           ↘                               ↙
[Accounting Systems]                 [Tax Authorities]
               ↘                   ↙
         [Identity Providers]   [Notification Systems]
```

---

## **4. Container Diagram (C4 Level 2)**

This level details the **main containers/services** within the SylviaNG Platform.

| Container                      | Technology Stack              | Responsibilities                               |
| ------------------------------ | ----------------------------- | ---------------------------------------------- |
| Web Frontend (HR Admin Portal) | React / Next.js, Tailwind CSS | HR, Payroll, Compliance Management UI          |
| Mobile App / ESS Portal        | Flutter / React Native        | Employee Self-Service (ESS) Interface          |
| API Gateway                    | NGINX / Kong Gateway          | API Routing, Security, Throttling              |
| Payroll Service                | Java / Spring Boot / Kafka    | Payroll Calculation, Tax Processing, Payslips  |
| HRMS Core Service              | Java / Spring Boot / Postgres | Employee Records, Leave, Attendance, Benefits  |
| Workflow Engine (Optional)     | Camunda / Zeebe               | Workflow Automation for HR Processes           |
| Reporting & Analytics Service  | Python / FastAPI / ClickHouse | Payroll & HR Analytics, Compliance Reports     |
| Integration Layer              | Node.js / Python              | Integrations with Accounting, Tax, ERP Systems |
| Notification Service           | Python / Node.js              | Email, SMS, In-App Notifications               |
| Authentication Service         | Keycloak / Auth0 / OAuth2     | SSO, User Identity Management                  |
| Event Bus / Message Broker     | Kafka                         | Event-driven Communication Across Services     |
| Database Cluster               | PostgreSQL / Redis            | Persistent Storage (multi-tenant, partitioned) |

---

### ➜ **Key Data Flows:**

* API Gateway routes external requests to backend microservices.
* Payroll Service and HRMS Core Service exchange events via Kafka.
* ESS Portal communicates via APIs with the Payroll & HRMS Core.
* Reporting Service periodically fetches data from the database and event bus.
* Integration Layer connects with external accounting and tax systems.
* Notification Service triggers messages based on events or scheduled jobs.

---

### ➜ **Container Diagram (Simplified Visual Representation):**

```
 +----------------------------+
 |      SylviaNG SaaS         |
 |    Payroll & HRMS Platform |
 +----------------------------+
           /          \
 [Web Frontend]    [Mobile ESS Portal]
           \          /
         [API Gateway]
             |
  +-------------------------------+
  | Core Backend Microservices     |
  | ------------------------------|
  | - Payroll Service              |
  | - HRMS Core Service            |
  | - Workflow Engine (Optional)   |
  | - Reporting & Analytics        |
  | - Notification Service         |
  | - Authentication Service       |
  | - Integration Layer            |
  +-------------------------------+
             |
      [Kafka Event Bus]
             |
      [PostgreSQL / Redis DB Cluster]
```

---

## **5. Key Architectural Drivers**

| Driver             | Description                                                      |
| ------------------ | ---------------------------------------------------------------- |
| Multi-tenancy      | Isolated tenant data; shared services infrastructure.            |
| Compliance         | Local tax rules, legal requirements per country.                 |
| Modularity         | Independent services for Payroll, HRMS, Analytics.               |
| API-First Approach | REST/GraphQL APIs for external integrations.                     |
| Scalability        | Horizontal scaling supported via Kubernetes, Kafka, DB clusters. |
| Security           | SSO, Data Encryption at Rest and Transit, Audit Logs.            |

---

## **6. Constraints & Assumptions**

* Cloud-native deployment on Kubernetes.
* PostgreSQL chosen for structured, relational data.
* Kafka used for event-driven architecture.
* Modular approach enabling feature-based deployments.
* Initial focus on APAC payroll compliance markets.

---

## **7. Document Review & Update Cadence**

* Review every **quarter** or **after significant architectural changes**.
* Owners: **Solution Architecture Team & Platform Engineering Team**

---

