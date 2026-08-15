---
name: feature-journey
description: ตรวจสอบและสร้าง/อัปเดต feature list (จาก backlog และเอกสาร spec ทั้งหมด) พร้อมจัดลำดับความสำคัญแบบ MoSCoW และสร้าง/อัปเดต user journey ที่เกี่ยวข้องของโปรเจกต์ My Coffee Store ใช้เมื่อผู้ใช้ขอสรุปรายการฟีเจอร์ทั้งหมด, ขอจัดลำดับ MoSCoW, หรือขอ user flow/journey ของแต่ละ role หรือเรียกผ่าน /feature-journey
---

Skill นี้เป็นทางเข้า (entry point) สำหรับผู้ใช้ในการขอตรวจสอบ/สร้าง feature list และ user journey ของโปรเจกต์ My Coffee Store งานจริงทั้งหมดถูก delegate ไปให้ subagent ชื่อ `feature-journey-writer`

## ขั้นตอน

1. **หา scope** — ถ้ามี argument ต่อท้ายคำสั่ง (`args`) ที่ระบุ spec หรือฟีเจอร์เฉพาะเจาะจง ให้ใช้เป็นขอบเขตการทำงาน ถ้าไม่มี ให้ถือว่าทำทั้งโปรเจกต์ (spec ทั้งหมดใน `docs/01-requirements/01-spec/`) โดยไม่ต้องถามผู้ใช้ก่อน

2. **เรียก subagent** — เรียกใช้ Agent tool ด้วย `subagent_type: "feature-journey-writer"` (รันแบบ foreground เพื่อรอผลลัพธ์ก่อนตอบผู้ใช้) โดย prompt ต้องมี:
   - scope ที่ได้จากขั้นตอนที่ 1 (ทั้งโปรเจกต์ หรือ spec เฉพาะที่ระบุ)
   - วันที่ปัจจุบัน (ในรูปแบบ YYYY-MM-DD) เผื่อ subagent ใช้กำหนดชื่อไฟล์ log
   - แจ้งให้ subagent ทำตามกระบวนการทั้งหมดที่กำหนดไว้ในคำสั่งของตัวเอง (อ่าน backlog + spec, กำหนด MoSCoW, เขียน feature-list.md แบบตารางสรุป+รายละเอียดฟีเจอร์, เขียน user-journey.md แบบ Mermaid diagram+คำอธิบาย mapping กลับ requirement, ถามผู้ใช้เมื่อไม่แน่ใจพร้อมอย่างน้อย 3 แนวทางและคำแนะนำ, อัปเดต index, บันทึก log)

3. **รายงานผลกลับผู้ใช้** — เมื่อ subagent ทำงานเสร็จ ให้สรุปให้ผู้ใช้ทราบแบบกระชับ: เอกสารที่สร้าง/แก้ไขทั้งหมด (feature-list.md, user-journey.md, index.md ที่เกี่ยวข้อง, log) พร้อมลิงก์แบบ markdown ที่คลิกได้ และสรุปจำนวนฟีเจอร์แยกตาม MoSCoW

ถ้า subagent ถามคำถามกลับมาระหว่างทาง (ผ่าน AskUserQuestion) ให้ปล่อยให้ผู้ใช้ตอบคำถามนั้นตามปกติ แล้วรอ subagent ทำงานต่อจนจบก่อนสรุปผล
