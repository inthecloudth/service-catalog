# Windows Server 2016 Migration Assessment & Roadmap

> **IP-01 | Repeatable Service Package**

**ผลลัพธ์ที่มุ่งหวัง:** ประเมินความพร้อมและจัดทำแผนย้าย Windows Server 2016 ไปยัง Windows Server 2022/2025

## เมื่อใดควรใช้บริการนี้

- ยังไม่มีข้อมูล Server และ Application Dependencies ที่เชื่อถือได้ก่อนย้ายระบบ
- ต้องเลือกระหว่าง Upgrade, Side-by-side และ Rebuild โดยยังไม่เห็นความเสี่ยง
- ต้องวางแผน Migration Waves ให้มีเจ้าของและลำดับความสำคัญ

## Scope

สำรวจ Server, Application และ Dependency ตามรายการที่ตกลง ประเมินความเสี่ยงและความซับซ้อน พร้อมกำหนด Target Baseline, Migration Approach และ Migration Waves; ไม่รวมการย้ายระบบจริง

## Architecture Mental Model

**System question:** What must be understood before deciding how a workload can move?

```mermaid
flowchart LR
  subgraph Current["Current estate"]
    Host["Windows Server 2016"]
    App["Application / Service"]
    Deps["Identity · DNS · Data · Network"]
    Host -->|hosts| App
    App -->|depends on| Deps
  end
  subgraph Assessment["Assessment boundary — read only"]
    Inventory["Inventory + ownership"]
    Graph["Dependency map"]
    Decision["Compatibility + risk decision"]
  end
  subgraph Future["Proposed future — not deployed"]
    Target["Windows Server 2022 / 2025"]
    Plan["Migration waves + roadmap"]
  end
  Host -.->|observe| Inventory
  App -.->|observe| Graph
  Deps -.->|trace| Graph
  Inventory --> Decision
  Graph --> Decision
  Target -.->|evaluate fit| Decision
  Decision -->|document| Plan
```

## Standard Delivery

1. Kickoff และรวบรวม Server Inventory
2. วิเคราะห์ Application, Dependency และ Compatibility
3. กำหนด Target Platform, Baseline และ Migration Approach
4. จัดทำ Risk Register, Migration Waves และ Roadmap

## Deliverables

Server/Workload Inventory, Dependency & Risk Assessment, Migration Strategy และ Roadmap

## Decisions & Outcomes

- Workloads ใดพร้อมย้าย และ Workloads ใดติดข้อจำกัด
- ควรใช้ Target Platform และ Migration Approach แบบใด
- ควรจัดลำดับ Migration Waves อย่างไร

## Engineering Assurance

- ต้องทราบ Owner, Dependencies และความเสี่ยงก่อนให้สถานะว่าพร้อมย้าย
- Assessment นี้ไม่รวมการ Cutover ระบบจริง

**Failure & Recovery:** หากข้อมูล Compatibility หรือ Dependency ยังยืนยันไม่ได้ ให้ระบุ Blocker และเจ้าของข้อมูลก่อนกำหนด Wave

### State & Decision Model

```mermaid
stateDiagram-v2
  [*] --> Unknown
  Unknown --> Discovered: inventory + owner
  Discovered --> Mapped: dependencies verified
  Mapped --> Evaluated: compatibility + risk
  Evaluated --> Planned: target + waves chosen
  Evaluated --> Blocked: unsupported / missing evidence
  Blocked --> Evaluated: resolve uncertainty
  Planned --> [*]
```

## Assumptions & Boundaries

อาศัยข้อมูลจากทีม System/Application Owner; ไม่รวมการทดสอบย้ายระบบจริง

*Conceptual model only; detailed execution and estimates are maintained separately.*

## Preparing for an Assessment

กำหนดระบบและผู้รับผิดชอบที่เกี่ยวข้อง พร้อมข้อกำหนดการเข้าถึงและ Change Window เพื่อยืนยัน Scope, Validation และ Acceptance Criteria ก่อนเริ่มงาน

---
*Architecture และ State Models เป็นแบบจำลองเชิงแนวคิด ไม่ใช่ Production Topology ขององค์กรใดองค์กรหนึ่ง*
