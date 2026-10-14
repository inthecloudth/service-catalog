# AWS Identity & Access Governance and Security Baseline

> **IP-05 | Repeatable Service Package**

**ผลลัพธ์ที่มุ่งหวัง:** ประเมินและยกระดับมาตรฐาน AWS Identity & Access Governance สำหรับบัญชีที่ตกลง

## When to Engage

- สิทธิ์ IAM กระจัดกระจายและขาดภาพรวมของ Users, Roles และ Accounts
- ต้องการมาตรฐาน Federation, Permission Sets, SCP และ Break-glass
- กังวล Guardrails ใหม่กระทบการทำงานของ Workloads

## Decisions & Outcomes

- มี IAM / Federation Architecture ที่สอดคล้องกับการบริหาร AWS Accounts
- ทราบสิทธิ์และ Guardrails ที่ควรปรับตามความเสี่ยง
- ยืนยันผล Priority Controls จากการทดสอบจริง

## Scope

ทบทวน Federation/Identity Center, IAM Role & Permission Set, MFA, SCP, Break-glass และ Access Review พร้อมปรับใช้ Priority Controls ที่อนุมัติ

## Architecture Mental Model

**System question:** Which layers authorize AWS access, and which only restrict it?

```mermaid
flowchart LR
  Human["Workforce user"] --> IdP["Corporate identity provider"]
  IdP --> Center["IAM Identity Center"]
  Center -->|permission set assignment| Role["IAM role session"]
  subgraph Account["AWS account boundary"]
    Role --> Policy["Identity policies"]
    Policy --> API["AWS resource / API"]
  end
  subgraph Org["Organization guardrails"]
    SCP["Service Control Policy"]
  end
  SCP -.->|sets maximum permissions| Role
  Review["Access review + change approval"] -.->|inspect| Center
  Review -.->|inspect| Policy
  Review -.->|inspect| SCP
```

## Standard Delivery

1. Review AWS Organization/Account และ Existing IAM
2. ออกแบบ IAM Standard, Federation, Roles และ Guardrails
3. Implement Priority Controls บน Accounts ที่ตกลง
4. Validate Access และส่งมอบ Governance Runbook

## Deliverables

AWS IAM Baseline, Priority Finding List, Applied Control Evidence และ Governance Guide

## Engineering Assurance

- SCP เป็นขอบเขตจำกัดสิทธิ์ ไม่ใช่กลไกให้สิทธิ์
- ต้องรักษาและทดสอบเส้นทาง Administrative/Emergency Access ก่อนเปลี่ยน Guardrails

**Failure & Recovery:** ถ้าการแก้ Role, Permission Set หรือ SCP ทำให้เกิด Unexpected Deny ให้ใช้เส้นทาง Recovery ที่อนุมัติและคืนค่านโยบายที่ผ่านการทดสอบ

### State & Decision Model

```mermaid
stateDiagram-v2
  [*] --> Discovered
  Discovered --> Evaluated: roles + policy inventory
  Evaluated --> Proposed: map identities to duties
  Proposed --> Approved: impact + break-glass review
  Approved --> Applied: agreed changes only
  Applied --> Verified: allowed and denied actions tested
  Applied --> Recovery: unexpected denied access
  Recovery --> Evaluated: restore / refine policy
  Verified --> [*]
```

## Assumptions & Boundaries

การเปลี่ยน SCP/Role ต้องทดสอบผลกระทบและรับอนุมัติ; ไม่รวมการปรับสิทธิ์ทุก Account

*Conceptual model only; detailed execution and estimates are maintained separately.*

## Getting Started

เตรียม AWS Organization/Account Scope, IAM Identity/Federation Design, Access Owners และ Approved Change Process

## Discuss Your Project Scope

หากองค์กรกำลังเผชิญปัญหาข้างต้น สามารถส่งภาพรวมระบบ จำนวน Workloads หรือ Accounts ที่เกี่ยวข้อง และผลลัพธ์ที่ต้องการ เพื่อร่วมกันกำหนด Scope และเกณฑ์รับมอบก่อนเริ่มงาน

**[ติดต่อทีม In the Cloud](mailto:info@inthecloud.co.th?subject=Service%20IP-05)**

---

*Architecture และ State Models เป็นภาพเชิงแนวคิด ไม่ใช่ Production Topology ของลูกค้ารายใด*

