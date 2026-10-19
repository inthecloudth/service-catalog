# Enterprise MCP Server Implementation & Integration

> **IP-09 | Customer Service Brochure**  
> **Microsoft 365 (Exchange Online, Teams, SharePoint, OneDrive) · Azure · AWS**

**Reference Duration: 15 Person-Days** — Enterprise MCP Foundation + Scoped Integration Pilot. ขอบเขตตัวอย่างคือ **1 Microsoft 365 Tenant, 1 Azure Subscription, 1 AWS Account และ MCP Tools ไม่เกิน 8 รายการ** บน Hosting Environment ที่ลูกค้าเตรียมไว้หรืออนุมัติให้จัดเตรียมตามข้อตกลง

## 1. About This Service

บริการออกแบบ พัฒนา และติดตั้ง **Enterprise Model Context Protocol (MCP) Server** เพื่อให้ AI Clients, Enterprise AI Agents และ Internal Applications เรียกใช้ความสามารถของระบบองค์กรผ่าน MCP Tools ที่กำหนด โดยเชื่อมต่อกับ **Microsoft 365, Azure และ AWS** อย่างปลอดภัย ตรวจสอบสิทธิ์ได้ และพร้อมให้ทีม IT ดูแลต่อ

ครอบคลุมการพัฒนา Integration สำหรับ **Exchange Online, Microsoft Teams, SharePoint Online, OneDrive for Business, Azure Resource Management/Monitoring และ AWS Resources/Monitoring** โดยใช้ Microsoft Graph, Azure REST/SDK และ AWS SDK/API ตาม Use Cases ที่ได้รับอนุมัติ

การดำเนินงานเน้น **Least Privilege, Per-tool & Per-resource Authorization, Data Access Boundaries, Human Approval สำหรับ Sensitive Write Operations, Audit Logging และ Functional/Security Validation** เพื่อไม่ให้ AI Client ใช้สิทธิ์เกินกว่าผู้ใช้หรือ Workload ที่ได้รับอนุญาต

**Service Outcome:** องค์กรได้ MCP Endpoint, Approved Tool Catalog, Connector Integrations, Access/Permission Matrix, Pilot Test Evidence และ Operations Runbook สำหรับการใช้งาน AI กับ Enterprise Systems อย่างมี Governance

## 2. Who Is This For?

- องค์กรที่ต้องการให้ Internal AI Assistants, Copilots หรือ Automation Agents ทำงานกับ Microsoft 365, Azure และ AWS ผ่านจุดเชื่อมต่อมาตรฐาน
- ทีม IT Operations / Cloud Platform ที่ต้องการค้นข้อมูลสถานะระบบ, Resource Configuration และ Alerts โดยไม่ให้ AI เข้าถึง Management API อย่างไร้ข้อจำกัด
- ทีม Knowledge Management / Service Desk ที่ต้องการเข้าถึงข้อมูล Email, Teams, SharePoint และ OneDrive ตามสิทธิ์ที่ได้รับ
- ทีม Security/Identity ที่ต้องการควบคุม App Permissions, Consent, Tool Authorization, Sensitive Operations และ Audit Evidence
- องค์กรที่มี Microsoft Entra ID, Microsoft 365, Azure และ AWS อยู่แล้ว และต้องการสร้าง Integration Layer ที่นำไปขยาย Use Cases ต่อได้

## 3. Scope & Approach

### A. Enterprise MCP Platform & Security Foundation

| # | Capability | Assessment & Implementation Activities |
|---|---|---|
| **1** | **Use Case & Tool Contract Assessment** | รวบรวม Business Use Cases, Approved Users/Agents, Data Owners, Backend APIs, Resource Boundaries, Tool Names, Read/Write Classification, Input/Output Schemas, Success Criteria และ Integration Dependencies เพื่อจัดลำดับ Tool ที่นำไปพัฒนา |
| **2** | **MCP Server Architecture & Hosting** | ออกแบบ Remote MCP Endpoint, Protocol/SDK Compatibility, Supported Transport, TLS, Network Access, Health Checks, Timeouts, Rate Limits, Deployment Topology และ Environment Separation พร้อมติดตั้ง MCP Runtime บน **Azure หรือ AWS Hosting** ที่เลือกเพียงหนึ่ง Primary Environment |
| **3** | **Enterprise Authentication & Identity Integration** | เชื่อม Client Access กับ Microsoft Entra ID หรือ Approved Identity Provider; ตรวจ Token Issuer, Audience, Expiry, Authorized Clients/Scopes และเลือก Downstream Credential Model แบบ **Delegated / On-Behalf-Of หรือ Application/Workload Identity** ให้เหมาะกับ Backend โดยไม่ส่ง MCP Caller Token ตรงไปใช้กับ Microsoft Graph/Azure/AWS |
| **4** | **Tool Authorization & Security Guardrails** | สร้าง Allowlisted Tool Registry, Per-tool/Per-resource Access Matrix, Input Validation, Output Filtering, Sensitive Data Minimization, Rate/Usage Limits, Policy Exceptions, Audit Correlation และ Approval Gates สำหรับ Write Operations พร้อมป้องกันการใช้ Tool Results/Prompts เป็นคำสั่งขยายสิทธิ์ |

### B. Enterprise System Integrations

| # | Integration Capability | Integration Activities & Example Use Cases |
|---|---|---|
| **5** | **Exchange Online MCP Integration** | เชื่อม Microsoft Graph สำหรับ Mail และ Calendar ที่อยู่ใน Scope เช่น Search/List Messages, Read Mail Metadata และ Retrieve Calendar Events; กำหนด Delegated/Application Permissions และ Mailbox Access Boundaries ตาม Use Case; Write/Send Mail ต้องผ่าน Approval และ Permission Review แยก |
| **6** | **Microsoft Teams MCP Integration** | เชื่อม Microsoft Graph สำหรับ Teams/Channels และ Messages ที่ API รองรับ เช่น List Teams/Channels และอ่านข้อมูล Channel/Chat ที่ผู้เรียกได้รับสิทธิ์ ตรวจ Teams-specific Delegated/Application Permission Limitations, Consent, Resource-Specific Consent และ Licensing/Capacity เมื่อเกี่ยวข้อง; ไม่สมมติว่า App-only สามารถส่ง Chat Messages ปกติได้ทุกกรณี |
| **7** | **SharePoint Online MCP Integration** | เชื่อม Sites, Document Libraries, Lists และ Files ผ่าน Microsoft Graph โดยใช้ Site/List/File-scoped Permissions ที่รองรับ เช่น Sites.Selected และ Selected Operations เพื่อจำกัดการเข้าถึงเฉพาะ Resource ที่อนุมัติ พร้อมตรวจสิทธิ์จริงบน SharePoint |
| **8** | **OneDrive for Business MCP Integration** | เชื่อม User Drive และ Files ผ่าน Microsoft Graph สำหรับ File Listing, Metadata หรือ Approved Read Operations โดยทดสอบ User Delegation, Folder/File Access และ Data Boundary เพื่อป้องกัน Cross-user File Access |
| **9** | **Azure MCP Integration** | สร้าง Tools สำหรับ Approved Azure Subscriptions/Resource Groups เช่น Resource Inventory, Configuration Metadata และ Azure Monitor Alerts (หากเปิดใช้) โดยใช้ Azure Resource Manager/Service APIs ร่วมกับ Managed Identity หรือ Service Principal และ Azure RBAC Scope ที่เหมาะสม |
| **10** | **AWS MCP Integration** | สร้าง Tools สำหรับ Approved AWS Accounts/Regions เช่น EC2 Resource Inventory, Resource Status หรือ CloudWatch Alarms (หากเปิดใช้) โดยใช้ AWS SDK/API พร้อม IAM Role Trust, STS Temporary Credentials และ Least-Privilege Policies; ไม่ใช้ Long-term Administrator Access Keys เป็น Default |

### C. Monitoring, Validation & Operational Readiness

| # | Capability | Implementation Activities |
|---|---|---|
| **11** | **Observability, Failure Handling & Operations** | จัดทำ Structured Audit Logs, Correlation IDs, Metrics, Trace/Health Checks, API Throttling/Retry/Timeout Handling, Secrets Storage/Rotation Responsibilities, Alerting และ Service Recovery Procedures โดยไม่ Log Tokens, Raw Secrets หรือข้อมูลอ่อนไหวโดยไม่จำเป็น |
| **12** | **Functional & Security Testing / Handover** | ทดสอบ Authorized/Deny Scenarios, Invalid Token/Scope, Cross-user/Cross-resource Access, Malformed Arguments, Prompt Injection in Retrieved Content, Sensitive Data Filtering, Rate Limits และ API Error Handling พร้อมทดสอบ Tool Calls ใน AI Client ที่รองรับและส่งมอบ Deployment/Operations Guide |

### D. Conceptual Architecture

![Enterprise MCP Server Architecture — Microsoft 365, Azure and AWS (monochrome)](../../assets/diagrams/ip-09-enterprise-mcp-architecture.svg)

**[Open full-size black-and-white architecture diagram](../../assets/diagrams/ip-09-enterprise-mcp-architecture.svg)**

**Request flow:** AI Client → Enterprise Identity / MCP Token Validation → **MCP Tool Authorization** → Backend Credential Acquisition → Microsoft Graph / Azure APIs / AWS APIs → Validated & Filtered Tool Result → AI Client

**Security boundaries:**

- **MCP access is not backend authorization:** MCP Server ต้องตรวจ Caller และ Tool แต่ Microsoft 365/Azure/AWS ยังต้องอนุญาตตาม Principal, Resource/Scope และ Permissions จริง
- **Do not forward raw caller tokens:** Graph ใช้ Supported Delegation/OBO หรือ Approved App Identity; Azure ใช้ RBAC + Managed Identity/Service Principal; AWS ใช้ IAM Role + STS ตาม Hosting/Trust Design
- **Read-first approach:** Sensitive Write Actions เช่น Send Mail, Post Teams Message, Modify Files, Stop VM หรือ Change IAM Policy ไม่เปิดโดย Default ต้องมี Approval, Policy และ Rollback/Fallback ที่เหมาะสม
- **Data minimization:** MCP Responses ต้องจำกัด Record Fields, File Contents, Recipients และ Context ตาม Data Owner/Classification; ไม่ถือว่า Graph Consent อย่างเดียวพิสูจน์ Per-user/Per-resource Authorization ครบแล้ว

### E. Example MCP Tool Catalog (Illustrative)

| MCP Tool | Backend | Operation | Authentication / Access Model |
|---|---|---|---|
| `exo_search_mail` | Exchange Online | Search approved mailbox messages | Graph delegated + mailbox permission |
| `exo_list_calendar_events` | Exchange Online | List scoped calendar events | Graph delegated + calendar permissions |
| `teams_list_channels` | Microsoft Teams | List channels in an approved Team | Graph delegated; Team access |
| `sp_list_site_documents` | SharePoint Online | List files in an allowed document library | Graph + Selected site/list scope where supported |
| `od_list_my_files` | OneDrive for Business | List user's accessible files | Graph delegated; user drive boundary |
| `azure_list_resources` | Azure Resource Manager | List resources in selected scope | Managed Identity/Service Principal + RBAC |
| `azure_list_monitor_alerts` | Azure Monitor | Retrieve configured alerts | Resource-scoped Azure RBAC; monitoring enabled |
| `aws_list_ec2_instances` | Amazon EC2 | List instances in approved Account/Region | AWS SDK + IAM Role / STS |

**Tool Count Boundary:** รายการด้านบนเป็นตัวอย่าง 8 Pilot Tools เพื่อกำหนด Effort; รายการจริงจะเลือกตาม Use Cases และ API Permissions ที่พร้อมใช้งาน การพัฒนา 8 Tools ไม่ได้หมายถึงการเปิดทุก API ของทั้ง 6 Systems

### F. Implementation Agenda

| Phase | Activities | Effort |
|---|---|---:|
| **1. Discovery & Integration Readiness** | Confirm Use Cases, Data Owners, API Availability, Existing Identity, Tenant/Subscription/Account Scope และ Tool Priorities | 2 วัน |
| **2. Architecture & Security Design** | กำหนด MCP Transport, Deployment, Identity/AuthZ, Backend Permissions, Tool Schemas, Sensitive-Data/Write Boundaries และ Test Plan | 2 วัน |
| **3. MCP Foundation & Hosting** | Implement MCP Endpoint, AuthN/AuthZ, Tool Registry, Secrets, Audit, CI/Deployment Basics และ Health Monitoring | 3 วัน |
| **4. Microsoft 365 / Azure / AWS Connector Pilot** | Implement Selected Graph, Azure และ AWS Tools (รวมไม่เกิน 8 รายการตาม Scope) พร้อม API Error Handling และ Resource Access Checks | 5 วัน |
| **5. Functional & Security Validation** | ทดสอบ End-to-end Tools, Allowed/Denied Actions, Resource Scope, Malformed Inputs, Error Handling และ Audit Evidence | 2 วัน |
| **6. Documentation & Knowledge Transfer** | ส่งมอบ Code/Configuration, Test Evidence, Tool Matrix, Operations Runbook, Open Risks และ Rollout Plan | 1 วัน |
| **Total** | | **15 Person-Days** |

*15 Person-Days เป็น Reference Pilot Package เมื่อมี Tenant/Cloud Access, API Permissions, Hosting และ Data Owners พร้อมใช้งาน และไม่ต้องพัฒนา Backend APIs ใหม่ ความซับซ้อนของ Microsoft Graph Consent/Teams, Cross-cloud Identity Federation, Write Workflows หรือ Production HA อาจทำให้ต้องเพิ่ม Effort*

## 4. Deliverables

| Deliverable | Description |
|---|---|
| **1. Use Case & MCP Tool Catalog** | Approved Tool Inventory, Business Owners, Operation Types, Tool Descriptions, Input/Output Schemas และ Backend Dependencies |
| **2. Enterprise MCP Architecture & Security Design** | Hosting, Identity/Token Flows, Data/Trust Boundaries, Network, Secrets, Authorization & Approval Model รวม Architecture Diagram |
| **3. MCP Server & Selected Connectors** | Source Code/Repository, Deployed Pilot MCP Endpoint, Approved Microsoft 365/Azure/AWS Integrations และ Configuration Templates ที่ไม่มี Secrets |
| **4. Tool & Permission Authorization Matrix** | MCP Principals → Tools → Resource Scope → Backend Permission/Role → Allow/Deny Rules และ Required Consents |
| **5. Functional & Security Validation Report** | Positive/Negative Test Cases, Observed Results, API Permission Failures, Data Boundary Tests, Monitoring Evidence และ Remaining Risks |
| **6. Deployment & Operations Runbook** | Deployment/Upgrade Steps, Secret & Credential Ownership, Logging/Monitoring, Incident Response, Emergency Disable/Recovery และ Future Rollout Roadmap |

## 5. Tools & Technologies

| Technology | Role in Service |
|---|---|
| **Model Context Protocol SDK / Remote MCP Transport** | MCP Endpoint, Tools, Input/Output Contracts, Client Integration |
| **Microsoft Entra ID / OAuth 2.x** | Caller Authentication, App Registration, Consent, Delegated OBO และ Application Identity เมื่อรองรับ |
| **Microsoft Graph API** | Exchange Online, Teams, SharePoint Online และ OneDrive Workload Integration |
| **Exchange Online Application RBAC / Graph Permission Model** | Mailbox Scope/Authorization สำหรับ Application Access ตาม Use Case |
| **SharePoint/OneDrive Selected Permissions** | Sites.Selected และ Resource-scoped Controls เมื่อ API รองรับ |
| **Azure Resource Manager / Azure SDK / Azure RBAC** | Azure Resource Inventory, Approved Operations และ Scoped Access |
| **AWS SDK / IAM / STS** | AWS Read/Action Tools, Role Trust, Temporary Credentials และ Resource-level Policies |
| **Azure Container Apps / App Service หรือ AWS ECS / Lambda** | Primary MCP Hosting Environment ตาม Target Architecture ที่เลือก |
| **Azure Key Vault หรือ AWS Secrets Manager** | Credential, Certificate และ Secret Lifecycle |
| **Azure Monitor / Log Analytics หรือ Amazon CloudWatch** | Service Logs, Health Metrics และ Alerting; SIEM Integration ตามที่ตกลง |

**Licensing & Usage:** Microsoft 365/Graph Workload APIs, Teams-specific APIs, Azure APIs, AWS Services, Cloud Hosting, Secret Stores และ Monitoring อาจมี License, API Limits หรือ Consumption Charges เพิ่มเติม การใช้งาน Conditional Access กับ Interactive Users ไม่ได้แทน Backend Service Permissions ของ App-only Calls

## 6. Sample Report

> **Fictional demonstration only:** ข้อมูล Tools, Tenants, Subscriptions, Accounts, Access Decisions และ Test Results เป็นตัวอย่าง ไม่ใช่ผลการติดตั้งหรือเข้าถึงระบบลูกค้าจริง

**[View Enterprise MCP — Microsoft 365, Azure & AWS Pilot Outcome](../examples/enterprise-mcp-m365-azure-aws-outcome.md)**

### A. Example Pilot Summary

| Metric | Fictional Example |
|---|---:|
| Integrated Service Areas | 6 (Exchange, Teams, SharePoint, OneDrive, Azure, AWS) |
| Registered MCP Tools | 8 |
| Approved Read-only Tools | 8 |
| Functional & Security Test Scenarios | 12 |
| Passed | 11 |
| Pending Recovery Test | 1 |

### B. Example Tool Authorization Matrix

| Tool | Approved Principal / Scope | Denied Scenario |
|---|---|---|
| `exo_search_mail` | User's own/delegated permitted mailbox | Attempt to read another user's mailbox |
| `sp_list_site_documents` | Explicitly approved SharePoint Site/Library | Access outside selected site scope |
| `azure_list_resources` | Approved Azure Resource Group/Subscription | Unapproved subscription |
| `aws_list_ec2_instances` | Approved AWS IAM Role / Region | Untrusted account or forbidden role |

### C. Example Test & Remediation Register

| Test ID | Test | Expected | Fictional Status |
|---|---|---|---|
| MCP-01 | Authorized Exchange Mail Query | Allowed + Filtered Result | Pass |
| MCP-05 | SharePoint Out-of-scope Site | Denied Before Data Return | Pass |
| MCP-08 | AWS Role/Region Scope | Only Approved Resources | Pass |
| MCP-09 | Invalid MCP Token Audience | Reject Before Backend Call | Pass |
| MCP-11 | Prompt Injection in Retrieved Document | Do Not Execute External Instructions | Pass |
| MCP-12 | Approved Disable/Recovery Drill | Restore Service Safely | Pending |

ตัวอย่างแสดงเฉพาะบาง Test Cases จาก Test Register; รายงานจริงจะแยก **Passed, Failed, Pending, Exception** และมี Supporting Evidence/Correlation ID ตามที่บันทึกได้

---

### Assumptions & Boundaries

- Scope อ้างอิง **1 Microsoft 365 Tenant + 1 Azure Subscription + 1 AWS Account**, Approved APIs และ **ไม่เกิน 8 MCP Tools** ตามข้อตกลง; Read-only Tools เป็น Default
- ไม่รวมการสร้าง AI Agent/Chat UI ใหม่, Model Training, Enterprise Search Index ทั้งองค์กร, Backend API ใหม่ หรือ Full RAG Knowledge Platform เว้นแต่ระบุใน SOW
- ไม่รวม Mass Mail Sending, Teams Posting Bots, Organization-wide File Write/Delete, Azure/AWS Infrastructure Modification หรือ Privileged Administrative Actions เป็น Default; Write Tools ต้องกำหนด Flow/Approval/Permissions แยก
- Microsoft Teams Graph APIs มีข้อจำกัดด้าน Operation/Delegated vs App Permissions; Write/Sending Messages ไม่รับประกันว่าจะใช้ App-only Model ได้
- การขอ Consent แบบกว้างหรือ Application Permissions อาจเข้าถึงข้อมูลได้มากกว่าผู้ใช้รายบุคคล จึงต้องมี Workload-side Scope และ Server-side Authorization ที่ตรวจสอบได้
- การติดตั้งบน Azure **หรือ** AWS ไม่ได้หมายถึง Deploy Active-Active ทั้งสอง Clouds; Cross-cloud Trust/Connectivity และ High Availability/Disaster Recovery อาจเป็น Workstream เพิ่มเติม
- ไม่รวม 24×7 Operations, Enterprise-wide AI Client Rollout, Advanced DLP/CASB Design หรือรับประกันการป้องกัน Prompt Injection ได้ทุกกรณี

**[View Technical Service IP-09](../ip-09-enterprise-mcp-server.md)** · **[Contact In The Cloud](../../contact.md)**

### References

- [Model Context Protocol — Authorization (2026-07-28)](https://github.com/modelcontextprotocol/modelcontextprotocol/blob/main/docs/specification/2026-07-28/basic/authorization/index.mdx)
- [Microsoft — On-Behalf-Of (OBO) Flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-on-behalf-of-flow)
- [Microsoft Graph — Permissions Reference](https://learn.microsoft.com/en-us/graph/permissions-reference)
- [Microsoft Graph — Teams Messaging Overview](https://learn.microsoft.com/en-us/graph/teams-messaging-overview)
- [Exchange Online — RBAC for Applications](https://learn.microsoft.com/en-us/exchange/permissions-exo/application-rbac)
- [Microsoft Graph — SharePoint/OneDrive Selected Permissions](https://learn.microsoft.com/en-us/graph/permissions-selected-overview)
- [Azure — Azure RBAC Scope](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview)
- [AWS — IAM Temporary Security Credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html)
