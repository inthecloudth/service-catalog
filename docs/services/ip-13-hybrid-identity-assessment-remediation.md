# Hybrid Identity Assessment & Remediation

> **IP-13 | Repeatable Service Package**

**Expected Outcome:** ประเมินความถูกต้อง ความปลอดภัย และความต่อเนื่องของ Identity Flow ระหว่าง Active Directory กับ Microsoft Entra ID แล้วแก้ไขความเสี่ยงที่ตกลง

## When to Engage

- ผู้ใช้มีปัญหา Sign-in หรือ Sync ระหว่าง AD DS กับ Microsoft Entra ID
- Identity Lifecycle และ Source of Authority ไม่ชัดเจน ทำให้ Account Provisioning/Disable มีความเสี่ยง
- กังวล Failure ของ Sync/Federation/Authentication Path

## Decisions & Outcomes

- เห็น Identity Flow, Authentication Dependencies และ Owners อย่างครบถ้วนใน Scope
- มีรายการความเสี่ยงที่จัดลำดับและ Remediation ที่ทดสอบแล้ว
- ตัดสินใจแนวทาง Resilience หรือ Authentication Modernization ได้จาก Evidence

## Scope

ครอบคลุม Entra Connect Sync / Cloud Sync ตามที่ใช้งาน, Sign-in Method (PHS, PTA, Federation), Sync Scope & Attribute Flow, Identity Lifecycle, SSO, Agent/Server Health, Resilience และ Permissions

## Architecture Mental Model

**Question:** How do identities cross the on-premises and cloud trust boundary?

```mermaid
flowchart LR
  HR["Identity source / lifecycle"] --> AD["Active Directory"]
  AD --> Sync["Entra Connect Sync / Cloud Sync"]
  Sync -->|provision and update| Entra["Microsoft Entra ID"]
  User["Workforce sign-in"] --> Entra
  Entra -->|issue tokens / apply access policy| Apps["Microsoft 365 · SaaS"]
  Auth["Chosen authentication path"] -.->|PHS / PTA / federation| Entra
  AD -.->|source credentials or validation dependency| Auth
  Observe["Sync and sign-in health"] -.-> Sync
  Observe -.-> Entra
```

## Standard Delivery

1. **Discover identity topology** — สำรวจ Forests, Source Anchors, Sync Technology, Agent/Server Versions และ Authentication Methods
2. **Review identity lifecycle** — ตรวจสอบ OU/Group/Attribute Scope, Join/Match Rules, Privileges, Provisioning and Deprovisioning
3. **Assess sign-in and resilience** — ตรวจ SSO, Auth Dependencies, Agent Health, Backup/Staging, Monitoring และ Break-glass
4. **Plan & remediate** — จัดลำดับ Findings พร้อม Pilot Changes และ Rollback for scoped controls
5. **Validate** — ทดสอบ Create/Update/Disable, Group & Attribute Sync, Sign-in และ Failure Scenarios

## Deliverables

Hybrid Identity Topology, Identity Flow Matrix, Risk Register, Prioritized Remediation, Pilot Validation และ Handover

## Engineering Assurance

- Source of Authority และ Attribute Ownership ต้องชัดเจน
- การแก้ Sync/Authentication ต้องมี Rollback และทดสอบ Emergency Access

**Failure & Recovery:** หากการปรับ Attribute Flow หรือ Sync Scope กระทบ User Sign-in ให้หยุดการขยายผลและกู้คืน Configuration ตามแผนที่อนุมัติ

### State & Decision Model

```mermaid
stateDiagram-v2
  [*] --> Discovered
  Discovered --> Mapped: source and sync flows known
  Mapped --> RiskAssessed: auth + lifecycle dependencies
  RiskAssessed --> Approved: remediation approved
  Approved --> Piloted: scoped change
  Piloted --> Verified: sync + sign-in tests pass
  Piloted --> Reverted: unexpected identity impact
  Reverted --> RiskAssessed: review mapping
  Verified --> [*]
```

## Assumptions & Boundaries

ไม่รวมการย้าย Authentication Method หรือเปลี่ยน Federation ทั้งองค์กรโดยอัตโนมัติ; ต้องผ่าน Dependency Review และ Change Approval

## Getting Started

เตรียม Topology ของ AD DS และ Entra, Sync/Authentication Method, App Owners และผู้อนุมัติ Change

## Discuss Your Project Scope

หากองค์กรกำลังเผชิญปัญหาข้างต้น สามารถส่งภาพรวมระบบ จำนวน Workloads หรือ Accounts ที่เกี่ยวข้อง และผลลัพธ์ที่ต้องการ เพื่อร่วมกันกำหนด Scope และเกณฑ์รับมอบก่อนเริ่มงาน

**[ติดต่อทีม In the Cloud](mailto:info@inthecloud.co.th?subject=Service%20IP-13)**

## References

- [Hybrid identity authentication methods](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/choose-ad-authn)
- [Hybrid authentication resilience](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-hybrid)

---

*Architecture และ State Models เป็นภาพเชิงแนวคิด ไม่ใช่ Production Topology ของลูกค้ารายใด*

