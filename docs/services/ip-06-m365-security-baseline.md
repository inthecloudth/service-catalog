# Microsoft 365 Security Baseline & Secure Score Improvement

> **IP-06 | Repeatable Service Package**

**ผลลัพธ์ที่มุ่งหวัง:** ประเมิน Security Baseline ของ Microsoft 365 และปรับปรุง Controls ที่มีผลต่อความเสี่ยงและ Secure Score

## เมื่อใดควรใช้บริการนี้

- Microsoft 365 มีการตั้งค่าความปลอดภัยหลาย Workloads และยังไม่มี Prioritized Baseline
- Secure Score มีข้อเสนอมาก แต่ยังไม่ทราบว่าอะไรลดความเสี่ยงจริง
- ต้องการทำ Remediation โดยไม่สร้างผลกระทบต่อผู้ใช้

## Scope

ครอบคลุมการตั้งค่า Entra, Exchange Online, SharePoint/Teams และ Defender ตามสิทธิ์ใช้งานที่มี พร้อม Remediation ที่อนุมัติและ Exception Register

## Architecture Mental Model

**System question:** Where are user access decisions made, and how is configuration drift detected?

```mermaid
flowchart LR
  People["Workforce + external users"] --> Identity["Microsoft Entra ID"]
  subgraph Services["Microsoft 365 service boundary"]
    Identity -->|authenticated access| Workloads["Exchange · SharePoint · Teams"]
    Workloads -->|events| Telemetry["Audit + Defender signals"]
  end
  subgraph Improvement["Security governance loop"]
    Review["Secure Score + baseline assessment"]
    Prioritize["Risk-ranked controls"]
    Change["Approved configuration update"]
    Evidence["Before / after validation"]
    Review --> Prioritize --> Change --> Evidence
  end
  Identity -.->|review configuration| Review
  Workloads -.->|review configuration| Review
  Telemetry -.->|risk evidence| Review
  Change -.->|apply scoped change| Identity
  Change -.->|apply scoped change| Workloads
  Evidence -.->|track residual gaps| Review
```

## Standard Delivery

1. Assess Tenant Configuration, Licensing และ Secure Score
2. จัดลำดับ Security Gaps และเลือก Priority Controls
3. Implement Remediation ที่ตกลง
4. Validate Configuration และจัดทำ Remaining Roadmap

## Deliverables

Security Gap Assessment, Remediation Record, Secure Score Snapshot และ Exception Register

## Decisions & Outcomes

- เห็น Tenant Security Gaps ที่มีลำดับความสำคัญและ Owner
- ได้ผลการแก้ Priority Controls พร้อม Evidence
- เห็น Roadmap และ Exceptions ที่ต้องดำเนินการต่อ

## Engineering Assurance

- Secure Score เป็นตัวชี้วัดหนึ่ง ไม่ใช่หลักฐานว่าปลอดภัยครบถ้วน
- ต้องทดสอบผลกระทบต่อการเข้าถึงและการทำงานของผู้ใช้ก่อน Rollout

**Failure & Recovery:** หากนโยบายที่ปรับใหม่กระทบการเข้าถึงหรือ Mail/Collaboration ให้ย้อนกลับการเปลี่ยนที่อนุมัติและปรับขอบเขตทดสอบ

### State & Decision Model

```mermaid
stateDiagram-v2
  [*] --> Observed
  Observed --> Prioritized: measure baseline + risk
  Prioritized --> Approved: choose feasible controls
  Approved --> Applied: change configuration
  Applied --> Verified: test expected behavior
  Applied --> Reverted: unexpected user impact
  Reverted --> Prioritized: revise control
  Verified --> Monitored: capture evidence + exceptions
  Monitored --> Observed: new risk / baseline drift
  Monitored --> [*]
```

## Assumptions & Boundaries

เป้าหมายการปรับปรุง Secure Score ขึ้นอยู่กับคะแนนเริ่มต้น สิทธิ์ใช้งาน และการอนุมัติเปลี่ยนแปลง ไม่รับประกันผลภายในระยะเวลาตัวอย่าง

*Conceptual model only; detailed execution and estimates are maintained separately.*

## Preparing for an Assessment

กำหนดระบบและผู้รับผิดชอบที่เกี่ยวข้อง พร้อมข้อกำหนดการเข้าถึงและ Change Window เพื่อยืนยัน Scope, Validation และ Acceptance Criteria ก่อนเริ่มงาน

---
*Architecture และ State Models เป็นแบบจำลองเชิงแนวคิด ไม่ใช่ Production Topology ขององค์กรใดองค์กรหนึ่ง*
