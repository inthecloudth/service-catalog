# AWS Identity & Access Governance and Security Baseline

> **IP-05 | Customer Service Brochure**  
> **AWS Organizations · IAM Identity Center · IAM Security · Multi-Account Governance**

**Reference Duration: 6 Person-Days** — Security Assessment, Governance Baseline Design และ Selected Remediation/Pilot (ยืนยันขนาด Environment, Account Scope และ Acceptance Criteria ใน Statement of Work)

## 1. About This Service

บริการตรวจสอบ ประเมิน และปรับปรุงมาตรฐาน Identity & Access Security สำหรับองค์กรที่ใช้งาน Amazon Web Services (AWS) ครอบคลุม AWS Organizations, IAM Identity Center, IAM Users/Roles, Privileged Access, Cross-Account Trust, Organization Guardrails และ Security Monitoring

บริการช่วยให้องค์กรทราบว่า **ใครหรือระบบใดเข้าถึง AWS Account และ Resource อะไรได้บ้าง** สิทธิ์นั้นได้รับผ่าน Permission Set, IAM Policy, Role Trust หรือ Resource Policy ใด และมีความเสี่ยงจาก Excessive Privileges, Long-Term Credentials, External Access หรือข้อจำกัด Governance อย่างไร

ทีม In The Cloud จะจัดทำ Risk-Based Security Baseline, Target Access Model และ Remediation Plan พร้อมดำเนินการ **Selected Remediation/Pilot** ที่ได้รับอนุมัติ โดยทดสอบทั้ง Allowed และ Denied Actions ก่อนส่งมอบ เพื่อให้ลดความเสี่ยงโดยไม่กระทบ Workloads หรือ Administrative Recovery Paths ที่จำเป็น

## 2. Who Is This For?

- องค์กรที่มี AWS หลาย Accounts / Organizational Units (OUs) และต้องการมาตรฐาน Identity Governance ร่วมกัน
- องค์กรที่ใช้หรือกำลังเตรียมใช้งาน AWS IAM Identity Center, Microsoft Entra ID, Active Directory หรือ External Identity Provider สำหรับ Workforce Federation
- องค์กรที่มี IAM Users, IAM Roles, Access Keys, CI/CD Integrations หรือ External Vendors จำนวนมาก
- องค์กรที่ต้องการตรวจสอบ Administrator Access, Root Account, Break-glass Access และ Cross-Account Permissions
- ทีม Cloud Platform, Security, Audit และ Compliance ที่ต้องการหลักฐาน Findings, Remediation Decisions และ Policy Validation สำหรับการปรับปรุงระยะถัดไป

## 3. Scope & Approach

### A. AWS Identity & Access Discovery and Security Assessment

| # | Capability | Assessment Activities |
|---|---|---|
| **1** | **AWS Organization & Account Governance** | สำรวจ Organization, OUs, Management/Member Accounts, Account Ownership, Security/Logging Accounts, Delegated Administrators และ Organizational Structure ตรวจความสอดคล้องของ Account Boundaries และ Governance Responsibilities พร้อมระบุ Accounts ที่ยังไม่มี Owner หรือ Policy Standard ชัดเจน |
| **2** | **Workforce Identity & Federation Security** | ตรวจสอบ IAM Identity Center Instance, Identity Source (เช่น Entra ID/External IdP, Active Directory หรือ Identity Center Directory), SAML/SCIM Configuration, User/Group Provisioning, AWS Account Assignments, Permission Sets, Session Duration และ MFA Enforcement โดยระบุว่า MFA ถูกจัดการที่ IdP หรือ Identity Center ตามสถาปัตยกรรมจริง |
| **3** | **IAM Identity Inventory & Ownership** | จัดทำ Inventory ของ IAM Users, Groups, Roles, Service/Workload Roles, Service-linked Roles, Role Trust และ Identity Owners ตรวจความสัมพันธ์ระหว่าง IAM Roles กับ EC2/Lambda/ECS/EKS, CI/CD หรือ External Workloads ตามข้อมูลที่เข้าถึงได้ และจำแนก Human กับ Non-human Access |
| **4** | **Privileged, Root & Emergency Access Security** | ตรวจสอบ Admin/PowerUser Assignments, High-Privilege Roles, Root User Security, Root MFA/Access Keys, การใช้ Centralized Root Access สำหรับ Member Accounts เมื่อรองรับ, Management Account Access และ Break-glass / Emergency Access Procedures พร้อมประเมิน Separation of Duties และ Recovery Readiness |
| **5** | **IAM Permissions & Least-Privilege Assessment** | ตรวจ Identity-based/Resource-based Policies, Inline/Managed Policies, Permission Sets, Permissions Boundaries, Policy Conditions, Session Restrictions และการใช้ Wildcard Actions/Resources วิเคราะห์เส้นทาง Effective Access ที่สำคัญร่วมกับ SCP/RCP และใช้ IAM Access Analyzer / CloudTrail Evidence ช่วยหาโอกาสลดสิทธิ์ |
| **6** | **Cross-Account & External Access Assessment** | ตรวจ Role Trust Policies, AssumeRole Paths, Third-party Accounts, ExternalId/Principal/Condition Restrictions, OIDC Federation และ Resource-based Policies ของทรัพยากรที่อยู่ใน Scope เช่น S3 หรือ KMS พร้อมทบทวน IAM Access Analyzer External/Internal Access Findings เมื่อเปิด Analyzer ที่เกี่ยวข้อง |
| **7** | **Credential Hygiene & Unused Access Review** | ตรวจ IAM Credential Reports, Console Password/MFA Status, Access Key Age/Status/Last Used, Long-term Credentials, Dormant IAM Users/Roles และ Unused Permission Signals จาก IAM Last-Accessed Data หรือ IAM Access Analyzer Unused Access เมื่อมีสิทธิ์ใช้งาน โดยให้ Owner ยืนยันการใช้งานก่อน Rotate/Deactivate/Delete |

### B. Organization Guardrails, Detection and Governance

| # | Capability | Assessment & Implementation Activities |
|---|---|---|
| **8** | **Organization Guardrails & Access Boundaries** | ตรวจ AWS Organizations SCP Inheritance, OU Attachments, Deny Conditions และ Guardrail Gaps; ทบทวน RCP สำหรับ Resource Protection เฉพาะบริการที่รองรับ พร้อมออกแบบ Scoped Guardrails, Exception Model, Rollback และ Test Cases โดยไม่ถือว่า SCP/RCP เป็นกลไกให้สิทธิ์ |
| **9** | **Security Monitoring & Threat Detection Baseline** | ตรวจ CloudTrail Coverage และ Retention, Organization Trails, IAM/API Activity Evidence, AWS Config, Amazon GuardDuty, AWS Security Hub CSPM และ Access Analyzer Findings (ตาม Services ที่เปิดใช้จริง) กำหนด Identity-focused Monitoring Use Cases เช่น Root Activity, Privilege Escalation, IAM Policy/Trust Changes, Suspicious Role Assumption และ Unauthorized Access |
| **10** | **Identity Governance & Access Lifecycle** | กำหนด Account/Role/Permission Set Ownership, Access Request/Approval, Periodic Access Reviews, Joiner-Mover-Leaver Controls, External Access Review, Exception Register และ Governance Cadence พร้อมจัดทำ Remediation Priorities, Evidence Requirements และแนวทางตรวจสอบ Privileged Access อย่างต่อเนื่อง |

### C. Approved Security Remediation — Performed by In The Cloud

จาก Findings ที่ตรวจพบ ทีมจะร่วมกับ AWS Account Owners, Application Owners และ Security Team กำหนด Change Scope พร้อมดำเนินการแก้ไขในรายการที่อนุมัติแล้ว โดยไม่ปิดหรือเปลี่ยนสิทธิ์ Production ที่ยังมี Dependencies ไม่ชัดเจน

| Remediation Area | Example Activities |
|---|---|
| **Permission Set & IAM Policy Hardening** | ลด Administrator/PowerUser Access ที่ไม่จำเป็น แยก Read-only/Operator/Admin Duties ปรับ IAM Policies, Conditions หรือ Permissions Boundaries |
| **Role Trust & Cross-Account Restrictions** | จำกัด Trusted Principals, External Access Paths และ Trust Conditions; ทดสอบ AssumeRole ที่จำเป็น |
| **IAM User & Credential Cleanup** | ตรวจ Owner ก่อน Disable/Rotate Access Keys และพิจารณาย้าย Workloads ไปใช้ Temporary Credentials/IAM Roles เมื่อรองรับ |
| **Root & Emergency Access Improvements** | ปรับ Root/Emergency Access Procedures, MFA/Recovery Controls หรือ Centralized Root Access เฉพาะรายการที่เหมาะสมและได้รับอนุมัติ |
| **Organization Guardrail Pilot** | ทดลอง Selected SCP (และ RCP เมื่อรองรับ) ใน OU/Account ที่กำหนด พร้อมทดสอบ Expected Allow/Deny และ Administrative Recovery |
| **Logging & Detection Improvements** | แก้ Configuration Gaps หรือกำหนด Selected Detection/Alert Rules โดยพิจารณา License/Usage Charges และ Operating Ownership |
| **Validation & Rollback** | เก็บ Policy ก่อนเปลี่ยน, Change Approval, Functional Tests, Allowed/Denied API Results และ Recovery Evidence |

**Important Access Model:** IAM Policies และ Resource Policies เป็นส่วนหนึ่งของกลไกให้สิทธิ์ ส่วน SCP และ RCP ใช้จำกัดสิทธิ์ที่เป็นไปได้ ไม่ได้ให้ Permissions เพิ่มโดยลำพัง การทดสอบต้องพิจารณา Permission Evaluation ตาม Context ของ Workload จริง

### D. Implementation Agenda

| Phase | Activities | Effort |
|---|---|---:|
| **1. Environment Review & Discovery** | ยืนยัน Organization/Account Scope, Federation, Identities, Tools, Access Owners และ Evidence Sources | 1 วัน |
| **2. Identity & Security Assessment** | วิเคราะห์ Permission Sets, IAM Roles/Policies, Cross-account Trust, Root/Privileged Access, Credentials, Guardrails และ Logging Coverage | 2 วัน |
| **3. Baseline & Remediation Planning** | จัดระดับ Risk, กำหนด Target Access Model, Proposed Guardrails, Prioritized Actions, Approval/Recovery Plan | 1 วัน |
| **4. Selected Remediation & Guardrail Pilot** | ปรับ Configurations/Policies ที่อนุมัติและทดสอบ Selected Workloads/Accounts พร้อม Allow/Deny Validation | 1 วัน |
| **5. Validation, Reporting & Handover** | ตรวจ Workload/Administrative Access, Exceptions, Residual Risks และส่งมอบ Evidence/Runbook | 1 วัน |
| **Total** | | **6 Person-Days** |

**Delivery boundary:** 6 Person-Days เป็น Reference Package สำหรับ Assessment และ **Selected Remediation/Pilot** ไม่รวม Organization-wide IAM Cleanup, Full Federation Migration, การเปลี่ยนทุก SCP/RCP หรือการตั้งระบบ Security Monitoring แบบครบวงจร จำนวน Accounts, OUs, Roles, Permission Sets และ Approval Windows ต้องยืนยันก่อนเริ่มโครงการ

## 4. Deliverables

| Deliverable | Description |
|---|---|
| **1. AWS Account & Identity Inventory** | AWS Account/OU Ownership, IAM Users/Roles, Workload Identities, Permission Sets, Privileged Access และ Configuration Coverage |
| **2. Identity & Permission Mapping** | Workforce-to-Account Assignments, IAM Role Trust, Cross-account Paths และ Permissions/Guardrail Interactions ที่วิเคราะห์ได้ |
| **3. Security Risk Assessment Report** | Findings Register, Risk Classification, Evidence, Affected Accounts/Roles, Remediation Priority และ Owner Decision |
| **4. Security Baseline & Remediation Plan** | Proposed Identity Access Model, Permission Set Standards, Least-Privilege/Trust Controls, SCP/RCP Guardrails, Exceptions และ Approved Actions |
| **5. Implementation & Validation Evidence** | Selected Configuration/Policy Changes, Before/After State, Allow/Deny API Tests, Workload Verification และ Rollback/Recovery Notes |
| **6. Identity Governance & Operations Guide** | Access Review Matrix, Role/Permission Set Ownership, Monitoring Recommendations, Residual Risks และ Prioritized Roadmap |

รายงานแยกสถานะ **Identified → Proposed → Owner Reviewed → Approved → Applied → Validated / Exception** อย่างชัดเจน ไม่ถือว่า Finding ถูกแก้ไขแล้วจากการให้คำแนะนำเพียงอย่างเดียว

## 5. Tools & Technologies

### Primary — AWS Native Tools

| AWS Tool | Usage |
|---|---|
| **AWS Organizations + AWS CLI/SDK** | Account/OU Inventory, Governance Model, Delegated Administration, SCP/RCP Assessment |
| **AWS IAM Identity Center** | Workforce Federation, Permission Sets, Account Assignments, Central Access Governance |
| **AWS IAM** | Users/Roles, Managed/Inline Policies, Trust Relationships, Credential Reports, Role and Access Key Review |
| **AWS IAM Access Analyzer** | External/Internal/Unused Access Findings, Policy Validation, Policy Generation จาก CloudTrail Activity เมื่อรองรับ |
| **AWS CloudTrail** | IAM/API Activity Investigation, Role Assumption Evidence, Account Changes และ Audit Trails |
| **AWS Config / Security Hub CSPM** | IAM-related Configuration Checks, Security Baseline Findings และ Control Status เมื่อเปิดใช้ |
| **Amazon GuardDuty** | Detection Findings สำหรับ Suspicious/Unauthorized IAM/API Activity เมื่อเปิดใช้ |
| **IAM Policy Simulator / CLI-based Tests** | ประเมิน Policy และตรวจ Allowed/Denied Actions; ยืนยันผลกับ Workload Tests จริงเมื่อจำเป็น |

**AWS Tool Mapping — 10 Capabilities**

| Capability | Primary AWS Tool(s) |
|---|---|
| 1. Organization & Account Governance | AWS Organizations, AWS CLI |
| 2. Workforce Identity & Federation | IAM Identity Center, External IdP, SAML/SCIM |
| 3. IAM Identity Inventory & Ownership | IAM, AWS CLI/SDK, Workload Role Configuration |
| 4. Privileged, Root & Emergency Access | IAM, IAM Identity Center, Centralized Root Access |
| 5. Permissions & Least Privilege | IAM Policy Analysis, IAM Access Analyzer, CloudTrail |
| 6. Cross-account / External Access | Role Trust/Resource Policies, IAM Access Analyzer |
| 7. Credential & Unused Access | IAM Credential Report, Access Key Last Used, Access Analyzer |
| 8. SCP/RCP Guardrails | AWS Organizations, IAM Policy Evaluation, Scoped Access Tests |
| 9. Security Monitoring Baseline | CloudTrail, GuardDuty, AWS Config, Security Hub CSPM |
| 10. Access Governance & Lifecycle | IAM Identity Center, Account Ownership Register, AWS CLI/SDK |

### Licensing, Costs & Data Coverage

- **IAM Access Analyzer:** External Access Findings ไม่คิดค่าบริการสำหรับตัว Analyzer แต่ Unused/Internal Access Analyzers และบาง Custom Checks มีค่าบริการตามการใช้งาน/จำนวน Resources หรือ Principals ที่วิเคราะห์
- **CloudTrail:** Event History ให้ข้อมูล Management Events ย้อนหลัง 90 วันต่อ Region; Organization Trails, Long-term Retention หรือ Data Events ต้องตรวจ Configuration และค่าใช้จ่าย
- **GuardDuty, AWS Config และ Security Hub CSPM:** ต้องตรวจสถานะการเปิดใช้, AWS Regions, Coverage และค่าใช้จ่ายเพิ่มเติมก่อนเพิ่มเข้าขอบเขต
- **Federation MFA:** ถ้า IAM Identity Center ใช้ External IdP ต้องตรวจ MFA ที่ IdP นั้น ไม่สรุปว่า IAM Identity Center เป็นจุด Enforce MFA เอง
- **Root/SCP/RCP:** Centralized Root Access สำหรับ Member Accounts และ SCP/RCP มี Prerequisites/ข้อยกเว้น; Guardrails ไม่ครอบคลุม Management Account หรือทุก Resource/Principal ในรูปแบบเดียวกัน

ไม่จำเป็นต้องซื้อ Third-party IAM Governance Platform เพื่อดำเนิน Assessment นี้ แต่ความครบถ้วนของ Findings ขึ้นกับ AWS Native Services ที่เปิดใช้งาน ขอบเขต Permissions และ Historical Evidence

## 6. Sample Report

> **Fictional Data Only** — เป็นตัวอย่างรูปแบบรายงาน ไม่ใช่ผลการประเมิน AWS ของลูกค้าจริง

**[ดู Sample AWS Identity & Access Baseline Outcome ฉบับเต็ม — 6 AWS Accounts / 14 Findings](../examples/aws-identity-access-baseline-outcome.md)**  
**[ดาวน์โหลดตัวอย่าง Findings Register (CSV)](../../assets/examples/aws-iam-baseline-findings-demo.csv)**

### A. Executive Summary (Demo)

| Metric | Example |
|---|---:|
| AWS Accounts Assessed | 6 |
| IAM Identity Center Permission Sets | 8 |
| Security Findings | 14 |
| Validated Pilot Controls | 3 |

ตัวเลขทั้งหมดตรงกับชุดข้อมูลสมมติใน Sample Report และไม่ใช่จำนวนที่รับประกันสำหรับลูกค้าจริง

### B. Example Security Findings & Decisions

| Finding | AWS Account (Fictional) | Security Observation | Priority | Proposed Action |
|---|---|---|---|---|
| IAM-001 | demo-prod | Privileged IAM Role กว้างเกินความจำเป็น | High | Review Role Duties และ Pilot Least-Privilege Reduction |
| IAM-003 | demo-shared | Resource Policy อาจเปิด External Access | High | ตรวจ Trusted Principals และ Resource Policy Conditions |
| IAM-005 | demo-dev | Permission Set เกินความจำเป็นของงาน | Medium | Split / Reduce Permission Set แล้วทดสอบ User Access |
| IAM-008 | demo-dev | Role ไม่พบ Usage ใน Evidence Window | Medium | ยืนยัน Consumers/Automation ก่อน Remove |
| IAM-010 | demo-logs | Audit Access กว้างเกินหน้าที่ | Medium | Pilot Read-only Access ตาม Operational Duties |

### C. Workforce & Cross-account Access Mapping (Demo)

| Identity / Role | Account | Intended Access | Review Decision |
|---|---|---|---|
| Platform-Admins / Admin Permission Set | demo-prod | Privileged Operations | Review Break-glass และ Separation of Duties |
| App-Operators / Operations Permission Set | demo-dev | Scoped Application Operations | Remove Unneeded Admin Actions |
| External-CI-Role | demo-dev | Deployment Automation | Validate OIDC Trust/Conditions |
| Audit-Readers / Read-only Permission Set | demo-logs | Security Audit Evidence | Validate Minimum Required Permissions |

### D. Implementation & Validation Format

| Control | Before | Target / Validation Evidence |
|---|---|---|
| IAM Role Privileges | Broad Action/Resource Scope | Allowed Operations Pass; Unnecessary Actions Denied |
| IAM Identity Center Permission Set | Wide Assignment Scope | Approved Users/Groups Retain Needed Access |
| Cross-account Trust | Broad Trusted Principal / Conditions | Required AssumeRole Works; Other Paths Denied |
| SCP Guardrail | No Scoped Restriction | Pilot OU Test + Emergency Recovery Pass |
| Credential Hygiene | Unverified / Stale Usage | Owner Approval + Safe Disable/Rotation Result |

ตารางเป็นรูปแบบ **Target / Validation Evidence** ไม่ใช่ผลว่าทำ Remediation เสร็จแล้ว ในโครงการจริงจะบันทึกผล Approved, Applied, Validated, Deferred และ Exception แยกกัน

---

### Assumptions & Boundaries

- ยืนยัน AWS Accounts, Organization/OU Scope, Identity Source, IAM Population, Regional Coverage และ Access Ownership ก่อนเริ่มงาน
- ใช้ Read-only/Least-Privilege Access สำหรับ Discovery เท่าที่เป็นไปได้ และใช้ Change Role เฉพาะรายการที่อนุมัติ
- Unused Access/Last-Accessed Signals ไม่ใช่หลักฐานเพียงพอให้ลบ IAM User, Role หรือ Credential ทันที ต้องตรวจ Consumers และ Historical Coverage
- การเปลี่ยน SCP/RCP, Permission Sets, Trust Policies และ Root/Emergency Access ต้องมี Business Owner Approval, Allowed/Denied Test Cases และ Recovery Route
- ไม่รวม Full AWS Landing Zone Implementation, CI/CD/Application Refactoring, Organization-wide Identity Migration, 24×7 Monitoring หรือ Full Remediation Rollout โดยอัตโนมัติ

**[ดู Technical Service IP-05](../ip-05-aws-identity-access-baseline.md)** · **[ติดต่อ In The Cloud](../../contact.md)**

### References

- [AWS IAM Identity Center — Permission Sets](https://docs.aws.amazon.com/singlesignon/latest/userguide/permissionsets.html)
- [AWS IAM Identity Center — External Identity Providers](https://docs.aws.amazon.com/singlesignon/latest/userguide/manage-your-identity-source-idp.html)
- [AWS IAM Access Analyzer — Capabilities and Pricing](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)
- [AWS IAM Access Analyzer — Findings](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-findings.html)
- [AWS Organizations — SCPs](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html)
- [AWS Organizations — RCPs](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_rcps.html)
- [AWS IAM — Centralize Root Access](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-enable-root-access.html)
- [AWS CloudTrail — Event History](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html)
