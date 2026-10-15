# Microsoft 365 Security Baseline & Secure Score Improvement

> **IP-06 | Repeatable Service Package**

**Expected Outcome:** ประเมิน Security Baseline ของ Microsoft 365 และปรับปรุง Controls ที่มีผลต่อความเสี่ยงและ Secure Score

## When to Engage

- Microsoft 365 มีการตั้งค่าความปลอดภัยหลาย Workloads และยังไม่มี Prioritized Baseline
- Secure Score มีข้อเสนอมาก แต่ยังไม่ทราบว่าอะไรลดความเสี่ยงจริง
- ต้องการทำ Remediation โดยไม่สร้างผลกระทบต่อผู้ใช้

## Decisions & Outcomes

- เห็น Tenant Security Gaps ที่มีลำดับความสำคัญและ Owner
- ได้ผลการแก้ Priority Controls พร้อม Evidence
- เห็น Roadmap และ Exceptions ที่ต้องดำเนินการต่อ

## Scope

ครอบคลุมการตั้งค่า Entra, Exchange Online, SharePoint/Teams และ Defender ตามสิทธิ์ใช้งานที่มี พร้อม Remediation ที่อนุมัติและ Exception Register

## Architecture Mental Model

**System question:** Where are user access decisions made, and how is configuration drift detected?

```mermaid
%%{init: {"theme":"base","themeVariables":{"primaryColor":"#ffffff","primaryTextColor":"#000000","primaryBorderColor":"#000000","secondaryColor":"#ffffff","secondaryTextColor":"#000000","secondaryBorderColor":"#000000","tertiaryColor":"#ffffff","tertiaryTextColor":"#000000","tertiaryBorderColor":"#000000","mainBkg":"#ffffff","nodeBorder":"#000000","lineColor":"#000000","textColor":"#000000","nodeTextColor":"#000000","titleColor":"#000000","background":"#ffffff","clusterBkg":"#ffffff","clusterBorder":"#000000","edgeLabelBackground":"#ffffff","labelColor":"#000000","transitionColor":"#000000","altBackground":"#ffffff","fontFamily":"Inter, Arial, sans-serif"}}}%%
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

## Engineering Assurance

- Secure Score เป็นตัวชี้วัดหนึ่ง ไม่ใช่หลักฐานว่าปลอดภัยครบถ้วน
- ต้องทดสอบผลกระทบต่อการเข้าถึงและการทำงานของผู้ใช้ก่อน Rollout

**Failure & Recovery:** หากนโยบายที่ปรับใหม่กระทบการเข้าถึงหรือ Mail/Collaboration ให้ย้อนกลับการเปลี่ยนที่อนุมัติและปรับขอบเขตทดสอบ

### State & Decision Model

```mermaid
%%{init: {"theme":"base","themeVariables":{"primaryColor":"#ffffff","primaryTextColor":"#000000","primaryBorderColor":"#000000","secondaryColor":"#ffffff","secondaryTextColor":"#000000","secondaryBorderColor":"#000000","tertiaryColor":"#ffffff","tertiaryTextColor":"#000000","tertiaryBorderColor":"#000000","mainBkg":"#ffffff","nodeBorder":"#000000","lineColor":"#000000","textColor":"#000000","nodeTextColor":"#000000","titleColor":"#000000","background":"#ffffff","clusterBkg":"#ffffff","clusterBorder":"#000000","edgeLabelBackground":"#ffffff","labelColor":"#000000","transitionColor":"#000000","altBackground":"#ffffff","fontFamily":"Inter, Arial, sans-serif"}}}%%
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

## Getting Started

เตรียม Tenant/License Scope, Security Score Snapshot, Existing Policies และเจ้าของ Workloads ที่ได้รับผลกระทบ

## Discuss Your Project Scope

หากองค์กรกำลังเผชิญปัญหาข้างต้น สามารถส่งภาพรวมระบบ จำนวน Workloads หรือ Accounts ที่เกี่ยวข้อง และผลลัพธ์ที่ต้องการ เพื่อร่วมกันกำหนด Scope และเกณฑ์รับมอบก่อนเริ่มงาน

**[ติดต่อทีม In the Cloud](mailto:info@inthecloud.co.th?subject=Service%20IP-06)**

---

*Architecture และ State Models เป็นภาพเชิงแนวคิด ไม่ใช่ Production Topology ของลูกค้ารายใด*

