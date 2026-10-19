# Service Catalog

**Cloud, Infrastructure, Identity, Security และ AI — ออกแบบและส่งมอบโดยเริ่มจากปัญหาจริงของระบบ**

เอกสารนี้ช่วยให้ IT Managers, Architects และผู้รับผิดชอบโครงการประเมินได้ว่า บริการใดเหมาะกับความเสี่ยงหรือแผนงานขององค์กร ก่อนลงรายละเอียดใน Statement of Work

## Start with Your Challenges

| คำถามที่กำลังเจอ | บริการที่เกี่ยวข้อง |
|---|---|
| ต้องย้าย Windows Server แต่ยังไม่รู้ Dependencies และความเสี่ยง | [Migration Assessment](ip-01-windows-server-migration-assessment.md) · [Migration Implementation](ip-02-windows-server-migration-implementation.md) |
| ต้องวางรากฐาน Azure หรือขยาย Cloud อย่างมี Governance | [Azure Landing Zones](ip-11-azure-landing-zones.md) · [Cloud Adoption Framework](ip-12-azure-cloud-adoption-framework.md) |
| Identity มีความเสี่ยงจากสิทธิ์และการเชื่อมต่อหลายระบบ | [Service Account Security](ip-03-service-account-security.md) · [User Account Hygiene](ip-19-user-account-hygiene.md) · [Hybrid Identity](ip-13-hybrid-identity-assessment-remediation.md) · [AD DS Assessment](ip-14-ad-ds-assessment-remediation.md) |
| ต้องการใช้ Microsoft Entra ID, Conditional Access และ MFA กับ AWS SSO/Provisioning | [AWS Workforce Identity Federation](ip-21-aws-workforce-identity-federation.md) · [AWS Identity & Access Baseline](ip-05-aws-identity-access-baseline.md) |
| ต้องย้าย Sign-in จาก AD FS / Federation มาใช้ Microsoft Entra Cloud Authentication | [Federation to Cloud Authentication Migration](ip-20-federation-cloud-authentication-migration.md) · [Hybrid Identity Assessment](ip-13-hybrid-identity-assessment-remediation.md) |
| Microsoft 365 มี Security/Compliance Gaps ที่ยังจัดลำดับไม่ได้ | [Security Baseline](ip-06-m365-security-baseline.md) · [Zero Trust](ip-15-microsoft-365-zero-trust.md) · [Compliance Readiness](ip-07-m365-compliance-readiness.md) |
| ต้องประเมิน Hardening และข้อยกเว้นที่กระทบการทำงาน | [Windows Server CIS](ip-17-windows-server-cis-benchmark.md) · [Microsoft 365 CIS](ip-18-m365-cis-benchmark.md) |
| ต้องการให้ AI/MCP เชื่อม Microsoft 365, Azure และ AWS ภายใต้สิทธิ์และ Audit ที่ตรวจสอบได้ | [Enterprise MCP Server](ip-09-enterprise-mcp-server.md) · [Customer Brochure](brochures/ip-09-enterprise-mcp-server.md) · [Secure AI Apps & Data](ip-08-secure-ai-apps-data.md) |
| ต้องจัดลำดับ Azure Recommendations หรือขอ Engineering Support | [Azure Advisor Remediation](ip-16-azure-advisor-remediation.md) · [Professional Support](ip-10-professional-support.md) |

## What Each Service Package Covers

- **When to engage** — สถานการณ์หรือปัญหาที่บริการเหมาะจะเข้าไปช่วย
- **Decisions & Outcomes** — ข้อมูลและผลลัพธ์ที่ใช้ตัดสินใจต่อ
- **Architecture Mental Model** — องค์ประกอบและ Control Boundaries ของระบบ
- **Standard Delivery** — ขั้นตอนงานและ Deliverables ในระดับที่กำหนด Scope ได้
- **Engineering Assurance** — เงื่อนไขความปลอดภัย, State Transitions, Failure/Recovery และข้อจำกัด

## Sample Outcomes (Fictional Data)

ตัวอย่างนี้ใช้ข้อมูลสมมติเท่านั้น เพื่อแสดงผลลัพธ์และรายงานที่ลูกค้าจะใช้ตัดสินใจได้ก่อนเริ่มงาน

- [Service Account Security — Assessment Dashboard (50 Accounts)](examples/service-account-security-assessment.md)
- [AWS Identity & Access — Findings & Pilot Outcomes](examples/aws-identity-access-baseline-outcome.md)
- [AWS–Entra Workforce Federation — SSO, SCIM & Go/No-Go Pilot](examples/aws-entra-workforce-federation-outcome.md)
- [Enterprise MCP Server — Tool Authorization & Security Tests](examples/enterprise-mcp-server-outcome.md)
- [Enterprise MCP for Microsoft 365, Azure & AWS — 8 Tools / 12 Pilot Tests](examples/enterprise-mcp-m365-azure-aws-outcome.md)
- [User Account Hygiene — Candidate Disposition (1,000 Accounts)](examples/user-account-hygiene-assessment-outcome.md)
- [Federation Migration — Staged Rollout Pilot & Go/No-Go](examples/federation-cloud-auth-migration-outcome.md)

## Browse by Category

เลือกหมวดบริการเพื่อขยายรายการ แล้วคลิก Service IP เพื่อดู Architecture, Scope และ Deliverables โดยตรง

???+ abstract "Azure & Cloud Adoption · 3 services"

    - **IP-11** — [Azure Landing Zones](ip-11-azure-landing-zones.md)
    - **IP-12** — [Azure Cloud Adoption Framework — End-to-End](ip-12-azure-cloud-adoption-framework.md)
    - **IP-16** — [Azure Advisor Assessment & Remediation](ip-16-azure-advisor-remediation.md)

??? abstract "Windows Server & Infrastructure · 5 services"

    - **IP-01** — [Windows Server Migration Assessment & Roadmap](ip-01-windows-server-migration-assessment.md)
    - **IP-02** — [Windows Server Migration Implementation](ip-02-windows-server-migration-implementation.md)
    - **IP-04** — [Linux Platform Standardization & Security](ip-04-linux-standardization-hardening.md)
    - **IP-14** — [AD DS Assessment & Remediation](ip-14-ad-ds-assessment-remediation.md)
    - **IP-17** — [Windows Server CIS Benchmark](ip-17-windows-server-cis-benchmark.md)

??? abstract "Identity & Security · 6 services"

    - **IP-03** — [Service Account Security Assessment & Remediation](ip-03-service-account-security.md)
    - **AR-ID-UAH (IP-19)** — [User Account Hygiene Assessment & Remediation](ip-19-user-account-hygiene.md)
    - **IP-05** — [AWS Identity & Access Baseline](ip-05-aws-identity-access-baseline.md)
    - **IP-21** — [AWS Workforce Identity Federation with Microsoft Entra ID](ip-21-aws-workforce-identity-federation.md)
    - **IP-13** — [Hybrid Identity Assessment & Remediation](ip-13-hybrid-identity-assessment-remediation.md)
    - **IM-ID-FCA (IP-20)** — [Federation to Cloud Authentication Migration](ip-20-federation-cloud-authentication-migration.md)

??? abstract "Microsoft 365 & Zero Trust · 5 services"

    - **IP-06** — [Microsoft 365 Security Baseline](ip-06-m365-security-baseline.md)
    - **IP-07** — [Microsoft 365 Compliance Readiness](ip-07-m365-compliance-readiness.md)
    - **IP-08** — [Secure AI Apps & Data](ip-08-secure-ai-apps-data.md)
    - **IP-15** — [Microsoft 365 Zero Trust](ip-15-microsoft-365-zero-trust.md)
    - **IP-18** — [Microsoft 365 CIS Benchmark](ip-18-m365-cis-benchmark.md)

??? abstract "AI & Technical Support · 2 services"

    - **IP-09** — [Enterprise MCP Server](ip-09-enterprise-mcp-server.md)
    - **IP-10** — [Professional Support](ip-10-professional-support.md)
## Discuss Your Project Scope

ก่อนกำหนดขอบเขตจริง ทีมจะร่วมกันยืนยันเป้าหมาย จำนวน Workloads/Accounts หรือ Tenants ข้อจำกัดด้าน Compatibility และสิ่งที่จะใช้เป็น Acceptance Criteria

**[ติดต่อ In the Cloud](mailto:info@inthecloud.co.th?subject=Service%20Catalog%20Enquiry)**

---

*Architecture Diagrams เป็น Conceptual Models ไม่ใช่ข้อมูลระบบจริงของลูกค้า และเอกสารนี้ไม่ใช่ข้อเสนอผูกพันเรื่องผลลัพธ์หรือระยะเวลาดำเนินการ*
