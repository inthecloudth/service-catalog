# Sample Outcome — Enterprise MCP Server for Microsoft 365, Azure & AWS

> **DEMO DATA ONLY · Fictional identities, resources and test evidence**  
> ตัวอย่างรายงานสำหรับ [IP-09 — Enterprise MCP Server Implementation & Integration](../ip-09-enterprise-mcp-server.md) ไม่มีการเรียก API หรือแก้ไขข้อมูลของลูกค้าจริง

## Executive Summary

ตัวอย่าง Pilot ของ Enterprise MCP Server เชื่อม **Exchange Online, Microsoft Teams, SharePoint Online, OneDrive for Business, Azure และ AWS** ผ่าน Tool Catalog ที่ควบคุมสิทธิ์แบบ Read-only

| Metric | Fictional Pilot |
|---|---:|
| Enterprise service areas | 6 |
| Registered MCP tools | 8 |
| Read-only tools | 8 |
| Security & functional test scenarios | 12 |
| Expected results passed | 11 |
| Recovery scenario pending | 1 |
| Unauthorized data exposures observed in demo | 0 |

**Example decision: Conditional Pilot Approval (Read-only only).** ไม่อนุมัติ Production-wide Rollout หรือเพิ่ม Write Tools จนกว่าจะผ่าน Recovery Test และ Owner Sign-off ตามระดับความเสี่ยง

## 1. Approved Tool & Backend Authorization Matrix

| MCP Tool | Backend | Approved Principal / Access | Prohibited Case |
|---|---|---|---|
| `exo_search_mail` | Microsoft Graph / Exchange | Delegated user + approved mailbox | Query another user's mailbox |
| `exo_list_calendar_events` | Microsoft Graph / Exchange | Delegated user + permitted calendar | Read unshared private calendar |
| `teams_list_channels` | Microsoft Graph / Teams | Approved user/team membership | Access unrelated Team |
| `sp_list_site_documents` | Microsoft Graph / SharePoint | Approved site or delegated document permission | Read other site library |
| `od_list_my_files` | Microsoft Graph / OneDrive | Current user's accessible drive | Cross-user drive access |
| `azure_list_resources` | ARM | Pilot Azure subscription/RG, scoped RBAC | Other subscription |
| `azure_list_monitor_alerts` | Azure Monitor | Approved monitoring scope | Other management group |
| `aws_list_ec2_instances` | AWS EC2 | Approved IAM role/region with STS | Unapproved role, account or region |

**Control model:** แยก **Caller-to-MCP Authorization** ออกจาก **MCP-to-Backend Credential + Authorization**; Token ของ MCP Client ไม่ส่งต่อไปเป็น Graph/ARM/AWS Token ตรง ๆ

## 2. Example Integration Architecture

![Enterprise MCP Service Architecture](../../assets/diagrams/ip-09-enterprise-mcp-architecture.svg)

*ภาพแสดง Trust Boundaries แบบ Conceptual ไม่ใช่ Actual Customer Environment*

## 3. Functional & Security Test Register

| Test | Scenario | Expected Result | Fictional Outcome | Status |
|---|---|---|---|---|
| **MCP-01** | Exchange: approved user searches mail | Allowed scoped messages only | Returned masked, scoped metadata | PASS |
| **MCP-02** | Exchange: read permitted calendar | Authorized events returned | Correct calendar boundary | PASS |
| **MCP-03** | Teams: list authorized channels | Authorized Team list only | Returned permitted channels | PASS |
| **MCP-04** | SharePoint: list approved library | Documents returned for approved site | Allowed docs returned | PASS |
| **MCP-05** | SharePoint: request another site | Deny before resource data exposure | Access denied | PASS |
| **MCP-06** | OneDrive: list own drive | Own files/metadata only | Correct user scope | PASS |
| **MCP-07** | Azure: resource inventory + monitor alerts | Read-only returns scoped resources and alerts | Resources/alerts match scope | PASS |
| **MCP-08** | AWS: approved role/region + forbidden path | Allowed EC2 read; forbidden role/region denied | Correct allow/deny | PASS |
| **MCP-09** | Invalid MCP token audience | Reject before calling backend | HTTP authorization failure | PASS |
| **MCP-10** | Exchange: cross-user mailbox | Deny despite tool name being visible | Denied | PASS |
| **MCP-11** | Injected instructions inside document | Treat document as untrusted data; no additional tool call | Injection ignored | PASS |
| **MCP-12** | Disable MCP endpoint + verify recovery | Authorized disable/restore and audit trail | Maintenance window not approved | PENDING |

**Test outcome:** 11 PASS + 1 PENDING = 12 Scenarios; no Test Case claims real Production Validation. Passing Prompt Injection Test does not guarantee resistance to all attacks.

## 4. Risk Register & Decisions

| Finding | Risk | Evidence / Consideration | Recommended Action | State |
|---|---|---|---|---|
| MCP-R01 | High | Disable/Recovery Drill not completed | Test recovery, break-glass owner, rollback and alerting | Open |
| MCP-R02 | Medium | Future Write Tool demand (send mail / update file) | Require per-tool approvals, explicit user confirmation, idempotency and separate sign-off | Future phase |
| MCP-R03 | Medium | Third-party agent / client permissions can differ | Validate each MCP Client's auth/token support and consent path | Review |
| MCP-R04 | Medium | Monitoring costs/retention may vary by provider | Set log fields, retention, masking and budget | Open |
| MCP-R05 | Medium | SharePoint/OneDrive selected permissions vary by endpoint | Check target API support and assigned resource scope per use case | Review |

## 5. Example Audit Trail Fields

| Field | Example (Fictional) |
|---|---|
| Correlation ID | demo-req-0049 |
| Caller | demo-ops-reader |
| MCP Tool | `aws_list_ec2_instances` |
| Backend | AWS EC2 / approved-account / ap-southeast-1 |
| Decision | ALLOW |
| Resource scope | Approved IAM Role and Region |
| Outcome | 3 instance metadata records returned |
| Sensitive data | No credentials or full customer payload retained |

**Logging practice:** เก็บ Principal Identifier, Tool Name, Decision, Timestamp, Correlation ID, Backend Target และ Status เท่าที่จำเป็น ไม่เก็บ Raw OAuth Bearer Tokens, AWS Session Keys, Message Bodies หรือ File Contents โดยไม่มีความจำเป็นและการอนุมัติ

## 6. Pilot Acceptance Gates

| Gate | Acceptance Evidence | Fictional State |
|---|---|---|
| MCP Transport & Caller Auth | Token validation, supported client, TLS | PASS |
| Microsoft 365 Resource Scope | Delegated/Selected permissions and denied cross-resource tests | PASS |
| Azure IAM Boundaries | Required Read-only calls work, outside scope denied | PASS |
| AWS Role Isolation | STS role/region test and negative case | PASS |
| Prompt/Data Safety | Schema, sensitive output and untrusted content tests | PASS |
| Monitoring & Recovery | Audit logs + approved disable/restore exercise | **PENDING** |
| **Enterprise-wide rollout** | **All critical gates and owner sign-off** | **HOLD** |

## 7. Customer Deliverables

- Enterprise MCP Architecture and Trust Boundary
- Approved Tool Catalog with JSON Input/Output Contracts
- Authorization Matrix: Caller → Tool → Backend → Resource
- Pilot Server and Connector Configuration (excluding secrets)
- Functional / Negative Security Test Results with Correlation IDs
- Open Risks, Runbook, Disable/Recovery Plan and Rollout Decision

**[View Customer Brochure](../brochures/ip-09-enterprise-mcp-server.md)** · **[View Technical Service IP-09](../ip-09-enterprise-mcp-server.md)**

---

*All accounts, identifiers, policies, resources, statuses and test results in this example are fictional.*
