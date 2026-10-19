# Service Account Security Assessment & Remediation

> **IP-03 | Customer Service Brochure**  
> **Active Directory & Hybrid Identity Security**

**Reference Duration: 6 Person-Days** — Assessment + Selected Remediation / Protection Pilot (ขึ้นอยู่กับขนาด Environment และข้อมูลที่มีอยู่; ยืนยันขอบเขตและระยะเวลาใน Statement of Work)

## 1. About This Service

บริการตรวจสอบ ประเมิน และปรับปรุงความปลอดภัยของ Service Accounts ในระบบ Active Directory และ Hybrid Identity ครอบคลุมการค้นหาและจำแนกบัญชี วิเคราะห์สิทธิ์การเข้าถึง พฤติกรรม Authentication และความสัมพันธ์กับ Servers หรือ Applications ที่เกี่ยวข้อง

ช่วยให้องค์กรระบุบัญชีที่มีสิทธิ์สูงเกินความจำเป็น ใช้ Credentials ที่มีความเสี่ยง หรือถูกนำไปใช้จากระบบที่ไม่คาดหมาย พร้อมออกแบบและดำเนินการ Security Hardening, Access Restrictions และ **Selected Remediation** ภายใต้การอนุมัติและตรวจสอบผลกระทบ

บริการยังครอบคลุมการออกแบบ Authentication Protection และ Security Monitoring เพื่อลดความเสี่ยงจาก Credential Compromise และ Lateral Movement โดยใช้ Microsoft Built-in Tools ร่วมกับ Microsoft Defender for Identity (MDI) เป็นแนวทางหลัก และสามารถใช้ Silverfort เป็นเครื่องมือเสริมได้ตาม License และความพร้อมของระบบ

## 2. Who Is This For?

- องค์กรที่ใช้งาน Active Directory หรือ Hybrid Identity และมี Service Accounts กระจายอยู่หลาย Servers/Applications
- องค์กรที่ยังไม่มี Account Inventory, Account Owner หรือ Application Dependencies ที่ชัดเจน
- องค์กรที่มี Windows Services, Scheduled Tasks, IIS Application Pools หรือ Legacy Applications ที่ใช้ Traditional Service Accounts
- องค์กรที่ต้องการทบทวน Privileged Service Accounts, Password Management และ Authentication Risks
- ทีม IT/Security ที่ต้องการหลักฐานและแผน Remediation สำหรับ Security Review, Audit หรือ Compliance

## 3. Scope & Approach

### A. Service Account Discovery & Security Assessment

| # | Capability | Assessment Activities |
|---|---|---|
| **1** | **Service Account Discovery** | ค้นหาและจำแนกบัญชีจาก AD และ Authentication Evidence รวมถึง Traditional Service Accounts, sMSA และ gMSA ตรวจ Windows Services, Scheduled Tasks, IIS Application Pools และ Applications ที่อยู่ใน Scope เพิ่มเติมเพื่อระบุการใช้งานจริง |
| **2** | **Account Classification & Privilege Assessment** | ตรวจ Account Types, Privileged/Nested Group Membership, Administrative Rights, SPNs, Delegation, Logon Rights และสิทธิ์เกินความจำเป็น เพื่อจัดกลุ่มบัญชีที่ควรทบทวนก่อน |
| **3** | **Authentication Activity Mapping** | วิเคราะห์ Source/Destination Servers, Authentication Protocols, Logon Types, Frequency และ Last Observed Activity จาก MDI, Windows Logs หรือแหล่งข้อมูลที่รองรับ พร้อมระบุช่วงเวลาข้อมูลและ Coverage |
| **4** | **Application Dependency Mapping** | เชื่อมโยง Account กับ Servers, Services, Scheduled Tasks และ Applications จาก Configuration + Authentication Evidence แล้วให้ Application Owner ยืนยัน Dependencies ก่อนเปลี่ยน Password, Restrict Logon หรือ Disable Account |
| **5** | **Security Risk Assessment & Prioritization** | ประเมิน Excessive Privileges, Password Risks, Stale/Dormant Signals, Unnecessary Access, Weak Authentication และ Misconfigurations จัดลำดับ Findings พร้อมเหตุผลและ Remediation Priority |
| **6** | **Authentication Behavioral Baseline** | วิเคราะห์รูปแบบการใช้งานที่คาดหวัง เช่น Authorized Sources/Destinations, Protocols, Frequency และ Observed Usage Window เพื่อออกแบบการตรวจจับ/จำกัด Authentication; บัญชีที่รันเป็นรายเดือนต้องมีข้อมูลเพิ่มเติม |
| **7** | **Abnormal Authentication Detection** | ตรวจ Unexpected Sources/Destinations, Interactive/Remote Logon ที่ไม่เหมาะสม, Failed Logons และพฤติกรรมที่ผิด Baseline ภายใต้ Sensor/Log Coverage ที่มี พร้อมแยก False Positives และเหตุการณ์ที่ต้อง Investigate |

### B. Authentication Protection & Policy Enforcement

| # | Capability | Implementation Activities |
|---|---|---|
| **8** | **Authentication Policy Recommendations** | สร้าง Recommended Policies จาก Account Usage, Dependencies และ Least Privilege เช่น Allowed Sources/Destinations, Logon Restrictions, Exceptions และการทบทวน Policy แบบเป็นระยะ โดยใช้ผู้เชี่ยวชาญ/Script หรือ Automated Recommendations เมื่อมี Platform รองรับ |
| **9** | **Virtual Fencing & Authentication Restrictions** | ออกแบบและทดสอบ Authentication Restrictions กับ Selected Accounts โดยใช้ AD Authentication Policies/Silos, GPO หรือ Native Controls เมื่อรองรับ; หากมี Silverfort NHI Security สามารถทดลอง Virtual Fencing ได้ตาม Protocol, Deployment และ License ที่ครอบคลุม |
| **10** | **Continuous Authentication Protection** | กำหนด Detection/Monitoring Rules, Security Alerts, Policy Violation Review และวิธีตอบสนอง/Enforcement ตลอดจนกระบวนการจัดการ Exceptions และทบทวนบัญชีใหม่ ทดสอบ Notify/Block เฉพาะ Policy ที่อนุมัติและเครื่องมือรองรับ |

### C. Additional Native AD Remediation — Performed by In The Cloud

Silverfort หรือ MDI ช่วยค้นหา วิเคราะห์ และตรวจสอบ Authentication ได้ แต่การแก้ไข Account และ Application Configuration ที่ต้นทางต้องดำเนินการด้วย Native Tools และร่วมกับเจ้าของระบบ

| Remediation Area | Activities |
|---|---|
| **Privilege Reduction** | ลด Group Membership, Delegation, Administrative/Resource Permissions ที่ไม่จำเป็นตาม Least Privilege |
| **Account Cleanup** | ตรวจสอบ Unused/Orphaned Accounts และพิจารณา Disable เฉพาะรายการที่ Owner ยืนยันและอนุมัติ |
| **Logon Restrictions** | จำกัด Interactive/Remote Logon หรือ Host Usage ผ่าน GPO/AD Policies ที่ Workloads รองรับ |
| **Credential Security** | ทบทวน Password Age/Rotation, Secret Storage และ Credential Exposure; ดำเนินการ Rotation เฉพาะบัญชีที่ผ่าน Dependency Review |
| **Managed Service Accounts** | ประเมิน gMSA/dMSA Compatibility และจัดทำ Migration/Pilot Plan สำหรับ Application ที่รองรับ |
| **Validation & Recovery** | มี Change Approval, Functional Test, Before/After Evidence และ Rollback Plan ก่อนขยายผล |

### D. Implementation Agenda

| Phase | Activities | Effort |
|---|---|---:|
| **1. Environment Review & Discovery** | ยืนยัน AD Scope, Identity Tools, Permissions, Logging, Account Population และ Initial Inventory | 1 วัน |
| **2. Activity & Security Assessment** | ตรวจ Dependencies, Privileges, Authentication Behaviors และ Risk Findings พร้อมระบุ Evidence Gaps | 2 วัน |
| **3. Security & Remediation Planning** | จัดลำดับบัญชี กำหนด Authorized Paths, Security Controls, Approval และ Rollback Criteria | 1 วัน |
| **4. Selected Remediation & Protection Pilot** | ทดสอบ Approved Hardening/Access Restrictions และ Protection Policies เฉพาะ Accounts/Systems ที่เลือก | 1 วัน |
| **5. Validation & Reporting** | ตรวจสอบ Service Availability, Authentication Results, Exceptions, Residual Risks และส่งมอบรายงาน | 1 วัน |
| **Total** | | **6 Person-Days** |

**Delivery boundary:** 6 Person-Days เป็น Reference Package สำหรับ Assessment และ **Selected Remediation/Pilot Protection** ไม่ใช่การแก้ไขบัญชีทั้งหมดหรือ Enterprise-Wide Enforcement การเก็บ Behavioral Baseline อาจต้องใช้เวลาปฏิทินมากกว่าช่วงทำงาน โดยเฉพาะ Periodic/Monthly Jobs และหากต้องติดตั้ง Identity Platform ใหม่หรือมี Historical Logs ไม่เพียงพอ ต้องปรับ Scope เพิ่มเติม

## 4. Deliverables

| Deliverable | Description |
|---|---|
| **1. Service Account Inventory** | Account Name, Type, Status, Owner (ถ้ายืนยันได้), Privileges, Configurations, Activity Evidence และ Classification |
| **2. Authentication & Dependency Report** | Source/Destination, Protocols, Usage Window, Expected Behavior และ Application/Server Dependencies พร้อม Confidence หรือช่องว่างข้อมูล |
| **3. Security Risk Assessment Report** | Account-Level Findings, Risk Levels, Supporting Evidence และ Prioritized Recommendations |
| **4. Authentication Protection & Remediation Plan** | Authorized Authentication Paths, Proposed Policies, Access Restrictions, Exceptions, Owner Approval และ Implementation Priority |
| **5. Implementation & Validation Report** | Approved Changes ที่ทำจริง, Policy/Configuration State, Test Evidence, Before/After Comparison และ Rollback/Exception Status |
| **6. Operations & Remediation Roadmap** | Monitoring/Review Guidelines, Open Risks, Pending Owner Decisions, Additional Remediation Waves และ Account Lifecycle Improvements |

สถานะ **Proposed / Approved / Applied / Validated / Exception** ต้องแยกจากกันเสมอ เพื่อไม่สื่อว่า Findings ทั้งหมดถูกแก้ไขแล้ว

## 5. Tools & Technologies

### Primary — Microsoft Built-in Tools + Microsoft Defender for Identity

| Microsoft Tool | Typical Usage |
|---|---|
| **AD DS / PowerShell** | Account Discovery, Privilege/Delegation Review, SPN, Group Membership และ Native AD Remediation |
| **Windows Services / Scheduled Tasks / IIS / CIM** | Service Account Configuration Inventory และ Application Dependency Evidence |
| **Windows Security Event Logs** | Logon/Authentication Evidence, Protocol Investigation และ Validation |
| **Group Policy + AD Authentication Policies/Silos** | Logon/Authentication Restrictions สำหรับ Account Types และ Workloads ที่รองรับ |
| **Microsoft Defender for Identity (MDI)** | Service Account Discovery, Identity Posture, Authentication Connections และ Security Alerts |
| **Microsoft Defender for Endpoint (MDE), หากมี** | Device Logon Investigation และ Advanced Hunting |
| **Microsoft Sentinel, หากมี** | Log Correlation, KQL/UEBA, Analytics Rules และ Monitoring Workflows |

**Microsoft Tool Mapping — 10 Capabilities**

| Capability | Microsoft Approach | Coverage |
|---|---|---|
| 1. Discovery | MDI + AD PowerShell + Server Configuration Inventory | รองรับ; ต้องเก็บ Config เพิ่ม |
| 2. Classification & Privileges | AD Group/ACL/Delegation Analysis + MDI Posture | รองรับ |
| 3. Authentication Mapping | MDI Connections + Windows Logs/MDE | รองรับตาม Telemetry |
| 4. Dependency Mapping | MDI Connections + Server/App Inventory + Owner Verification | บางส่วน; ต้องยืนยัน App Dependencies |
| 5. Risk Assessment | MDI Assessments + AD Configuration/Privilege Review | รองรับ; ต้องวิเคราะห์ร่วม |
| 6. Behavioral Baseline | Historical Logs + KQL/Sentinel UEBA (หากมี) | บางส่วน; ต้องกำหนด Baseline |
| 7. Abnormal Detection | MDI Alerts + MDE/Sentinel Rules (หากมี) | บางส่วน; Coverage ตาม Rules/Logs |
| 8. Policy Recommendations | Expert Review + PowerShell/KQL + AD Policy Design | บางส่วน; ไม่ได้ Auto-Generate ทุกกรณี |
| 9. Virtual Fencing / Restrictions | GPO + Authentication Policies/Silos + Network Controls | บางส่วน; ไม่เทียบเท่า Silverfort Dynamic Virtual Fencing |
| 10. Continuous Protection | MDI/MDE/Sentinel Alerts + Native Enforcement & Response | บางส่วน; ไม่ใช่ Universal Per-Authentication Blocking |

### Optional — Silverfort (Paid Enterprise Security Tool)

Silverfort NHI/Service Account Security สามารถเสริม **Automated Discovery & Classification, Behavioral Analysis, Risk Prioritization, Smart Policy Recommendations, Virtual Fencing และ Continuous Authentication Enforcement** ตามความสามารถของ Deployment และ License ที่ได้รับ

Silverfort **ไม่ได้แทนการทำ Native AD Remediation** เช่น Remove Excessive Privileges, Rotate Password, Disable Accounts หรือ Migration ไป gMSA/dMSA ซึ่งทีม In The Cloud ต้องดำเนินการร่วมกับ Application Owner

**Licensing:** MDI, MDE, Sentinel และ Silverfort อาจต้องมี License/ค่าใช้งานเพิ่มเติม; การมี Microsoft Built-in Tools ไม่ได้หมายความว่ามีสิทธิ์ใช้งาน MDI โดยอัตโนมัติ

## 6. Sample Report

> **ข้อมูลสมมติเท่านั้น** — แสดงรูปแบบรายงาน ไม่ใช่ผลการประเมินหรือการเปลี่ยนแปลงในระบบลูกค้าจริง

**[ดูตัวอย่าง Assessment Report ฉบับเต็ม — 50 Service Accounts](../examples/service-account-security-assessment.md)**  
**[ดูตัวอย่าง Account Register (CSV)](../../assets/examples/service-account-register-demo.csv)**

### A. Sample Executive Summary

| Metric | Example |
|---|---:|
| Accounts Assessed | 50 |
| High-Risk Accounts | 8 |
| Owners Verified | 41 / 50 |
| Dependencies Mapped | 38 / 50 |

จำนวนตัวอย่างข้างต้นมาจาก **Fictional 50-Account Dataset** ใน Sample Report เดิม ไม่ใช่ผลการดำเนินงานจริง

### B. Example Authentication & Dependency Findings

| Account (Fictional) | Source | Destination | Protocol | Observation |
|---|---|---|---|---|
| demo_svc_backup | BKP01 | FS01 | Kerberos | Expected path — confirm with owner |
| demo_svc_backup | APP03 | FS01 | NTLM | Unexpected source — investigate |
| demo_svc_erp_batch | APP01 | SQL01 | NTLM | Legacy dependency — review compatibility |

### C. Example Remediation & Protection Decisions

| Account (Fictional) | Finding | Recommended Action | Status |
|---|---|---|---|
| demo_svc_backup | Privileged Group Membership | Confirm Dependencies, Reduce Privileges และ Restrict Approved Authentication Paths | Proposed |
| demo_svc_erp_batch | Static Credential / Legacy Use | Review Rotation และ gMSA Compatibility | Owner Review |
| demo_svc_legacy | Ownership/Usage Unclear | Identify Owner และ Authentication Consumers ก่อนเปลี่ยนบัญชี | Investigation |

### D. Before / After Validation Format

| Control | Before | Proposed Target / Validation |
|---|---|---|
| Privileged Access | Excessive Membership | Remove หลังยืนยัน Required Permissions และตรวจ Effective Access |
| Authentication Sources | Multiple / Unknown | Document Allowed Sources และทดสอบ Approved Restriction |
| Interactive Logon | Allowed | Restrict ตาม Policy ที่รองรับ พร้อมทดสอบ Application |
| Monitoring | Limited Coverage | Configure Supported Alerts และตรวจ Data Coverage |

ตัวอย่างนี้แสดง **Target State** เท่านั้น ไม่ใช่ Completed Remediation; รายงานจริงจะมี Approval, Implementation Evidence และ Functional Test Results แยกต่างหาก

---

### Assumptions & Boundaries

- Scope จริง จำนวน Accounts/Servers และ Acceptance Criteria ต้องยืนยันก่อนเริ่มโครงการ
- การไม่พบ Authentication ในช่วงเวลาที่มีข้อมูล **ไม่ได้หมายความว่าบัญชีเลิกใช้งานแล้ว** ต้องตรวจสอบ Periodic Jobs และ Application Dependencies
- การเปลี่ยน Production Credentials/Permissions/Enforcement ต้องผ่าน Change Approval และมี Recovery Plan
- ไม่รวม Full Enterprise-Wide Remediation, Application Code Changes หรือ Managed Security Monitoring แบบ 24×7 ใน Reference Package
- Silverfort Virtual Fencing และ Automated Smart Policies ใช้งานได้เมื่อมี Platform, Integration, License และ Protocol Coverage ที่รองรับ

**[ดูหน้า Technical Service IP-03](../ip-03-service-account-security.md)** · **[ติดต่อทีม In The Cloud](../../contact.md)**

### References

- [Microsoft — Defender for Identity Service Account Discovery](https://learn.microsoft.com/en-us/defender-for-identity/service-account-discovery)
- [Microsoft — Authentication Policies and Authentication Policy Silos](https://learn.microsoft.com/en-us/windows-server/security/credentials-protection-and-management/authentication-policies-and-authentication-policy-silos)
- [Silverfort — Service Account Security](https://www.silverfort.com/use-cases/service-account-security/)
