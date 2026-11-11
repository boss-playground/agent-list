# Agent List — Starter package

Latest Update: 2026-11-08T16:18:59Z
Owner: Dev Lead (to be assigned)
Status: draft

ชุดเริ่มต้นสำหรับ Context Builder, Context Updater, BRD Builder, Technical Specification, Implementation Planner, Implementation Builder, Test Case Generator และ Test Automation ตามข้อกำหนดที่คุยไว้ ใช้ Markdown กลางกับ Codex และ Claude ไม่มีข้อมูล Security/PII ภายในองค์กรจริง และยังไม่ได้ติดตั้งลง Mac หรือ ChatGPT Project

## โครงสร้าง
- `skills/context-builder/` และ `skills/context-updater/`: คำสั่งสกิลที่ติดตั้งได้แยกกัน
- `skills/brd-builder/`: สร้าง BRD จาก BA notes/prompt หรือ source code พร้อม acceptance criteria และตัวอย่าง test cases ที่อ้างอิง requirement; ส่งออก Markdown และ Word จากเนื้อหาเดียวกันเมื่อ runtime รองรับ
- `skills/technical-specification/`: จาก BRD + context สร้าง technical spec และ HTML prototype ที่กดใช้งานได้ โดยเชื่อมหน้าจอ/interaction กับ logic, data, API, validation, Security/PII และ requirement; prototype ใช้ข้อมูลจำลองเท่านั้น
- `skills/implementation-planner/`: วางลำดับงานและ dependencies พร้อมร่าง Jira stories/tasks ที่ trace กลับ BRD/spec ได้ ต้องอนุมัติ batch ที่ชัดเจนก่อนสร้าง Jira ทุกครั้ง และป้องกันสร้างซ้ำเมื่อ retry
- `skills/implementation-builder/`: รับ story หรือหลาย story ที่เกี่ยวข้อง อ่าน tasks/BRD/spec/context แล้วทำงานใน local ตรวจ high-level และ unit tests ที่เหมาะสมตาม AC พร้อมสรุปสิ่งที่เสร็จ/ค้างและความเสี่ยง ไม่บังคับ browser E2E ซึ่งแยกเป็นสกิลภายหลัง และไม่ push/เปิด PR
- `skills/test-case-generator/`: สร้าง cases สำหรับ QA review ครอบคลุม UI E2E/API/security-auth-PII/edge-negative/regression พร้อม prerequisites, ข้อมูลจำลอง, ขั้นตอน, expected result, priority และ traceability โดยไม่ execute tests
- `skills/test-automation/`: แปลง cases ที่ QA review แล้วเป็น automation โดยใช้ Playwright เป็นค่าเริ่มต้นสำหรับ UI/API รันเฉพาะ test environment และข้อมูลจำลองที่ได้รับอนุญาต รายงาน pass/fail/blocked/manual พร้อมหลักฐาน; ZAP เป็นทางเลือกที่ต้องอนุมัติ scope โดยชัดแจ้ง
- `context/enterprise/`: มาตรฐาน Security และ PII กลางร่วมทุกแอป พร้อมทะเบียนแหล่งอ้างอิง
- `context/applications/_template/`: คัดลอกเป็นชื่อแอป เช่น `crm` แล้วเติมข้อมูลที่ Dev Lead ยืนยัน
- `templates/change-report.md`: ผลเปรียบเทียบก่อน/หลังและผลกระทบ

## ใช้งานแบบมีผู้ช่วยถามนำ
ทุกสกิลอ่านข้อมูลที่มีอยู่ก่อน แล้วถามเฉพาะสิ่งจำเป็นที่ยังขาดเป็นชุดสั้น ๆ พร้อมตัวอย่าง/ตัวเลือก สรุปให้ยืนยันก่อนตัดสินใจ และแยกข้อสมมติ/สิ่งที่ยังไม่รู้ชัดเจน ดู [GUIDED-INTAKE.md](GUIDED-INTAKE.md) เป็น workflow แบบ guided ไม่ได้รันสกิลถัดไปอัตโนมัติ

## ตำแหน่งไฟล์และการส่งต่องาน
อ่าน [PATHS.md](PATHS.md) ก่อนรันสกิลทุกตัว: context เดิมแยก enterprise/application ส่วนผลลัพธ์อยู่ใต้ `artifacts/applications/<app-id>/<work-id>/` มี index เชื่อมเวอร์ชันและสถานะ ห้ามใช้โฟลเดอร์ติดตั้งสกิลเป็น project root โดยอัตโนมัติ

## Knowledge graph (ทางเลือก)
อ่าน [GRAPHIFY.md](GRAPHIFY.md): candidate คือ Graphify-Labs Graphify ต้องยืนยันตัวผลิตภัณฑ์และอนุมัติ corpus/provider ก่อนเปิดใช้ ทุกสกิลตรวจต้นฉบับเสมอและแยก code refresh จาก semantic refresh ของเอกสาร ยังไม่ได้ติดตั้ง/สร้าง graph หากใช้ไม่ได้อ่านไฟล์ตรงได้ตามเดิม

## การเชื่อมต่อ Jira และ SharePoint
อ่าน [INTEGRATIONS.md](INTEGRATIONS.md) สำหรับ capability ของแต่ละสกิล การตั้งสิทธิ์ขั้นต่ำ วิธีตรวจการเชื่อมต่อและ fallback เมื่อใช้ไฟล์/export แทน ผู้ใช้ยืนยัน Jira Cloud แล้ว จึงแนะนำ Atlassian official remote MCP เป็นตัวเลือกหลัก ส่วน deployment ของ SharePoint ยังไม่ทราบ เอกสารนี้ยังไม่ได้เชื่อมระบบใดให้

## เริ่มใช้งาน
1. วางโฟลเดอร์ `context` ใน repository กลางที่ทีมได้รับอนุญาตให้อ่าน อย่าใช้ข้อมูล PII จริงในไฟล์
2. ติดตั้งโฟลเดอร์สกิลที่เลือกใช้ หรือทั้ง 8 สกิล ในตำแหน่ง skill ของเครื่องมือที่ใช้งาน โดยคัดลอกทั้งโฟลเดอร์และเก็บ `SKILL.md`, `references/` และ `assets/` (ถ้ามี) ไว้ด้วยกัน ตัวอย่าง repository scope ที่ใช้กัน: Codex `.agents/skills/`, Claude Code `.claude/skills/`. ตรวจการค้นพบสกิลในเวอร์ชันที่องค์กรใช้ก่อนแจกทีม
3. เรียก Context Builder แล้วระบุ root ของ context, ชื่อแอป, greenfield/brownfield, scope, foundation, design และลิงก์ภายในที่ได้รับอนุญาต
4. ตรวจ draft กับ Dev Lead และเจ้าของนโยบายก่อนถือเป็น baseline ที่อนุมัติแล้ว
5. เรียก Context Updater เมื่อจะเปลี่ยนข้อมูลหรืออยากเช็กแหล่งมาตรฐาน เป็นการตรวจตามสั่ง ไม่ได้ตั้งเวลาเฝ้าตรวจอัตโนมัติ

Markdown อ่านได้ทั้งสองเครื่องมือ แต่การอ่านไฟล์อัตโนมัติไม่ได้เกิดขึ้นเพียงเพราะมีไฟล์อยู่ เพิ่มคำสั่งอ่าน context ใน repo ของแอปหรือระบุในการเรียกสกิล ตัวอย่างอยู่ใน `ADAPTERS.md`.

## ตัวอย่างคำสั่ง
- “ใช้ context-builder สร้าง context ของ CRM แบบ brownfield โดยใช้ context root นี้ เริ่มถามเฉพาะข้อมูลที่ยังขาดจาก Dev Lead”
- “ใช้ context-updater ตรวจ Security และ PII sources ที่บันทึกไว้ เทียบกับ baseline ของ CRM และเสนอ diff ก่อนแก้ไฟล์ที่ approved แล้ว”

## วันที่และเวอร์ชัน
ทุก context มี Latest Update; วันตรวจต้นฉบับแยกต่างหากใน source register ใช้ Git เก็บประวัติ ไม่สร้างเลขเวอร์ชันใหม่ทุกครั้งที่แก้ถ้อยคำ และไม่ commit/push อัตโนมัติ

## สิ่งที่ยังต้องมี
ชื่อแอปจริง ผู้รับผิดชอบ repository กลาง ลิงก์นโยบายที่เข้าถึงได้ และผู้อนุมัติ enterprise baseline. ยังไม่ผ่าน live test กับ Codex/Claude ขององค์กรและยังไม่มีการตรวจ compliance.
