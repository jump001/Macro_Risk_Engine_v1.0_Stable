# Macro Risk Engine v1.0 Stable

# Business Project Charter

> กำหนดวิสัยทัศน์ เป้าหมาย และขอบเขตของโครงการ Macro Risk Engine

---
# Business Value

Macro Risk Engine สร้างคุณค่าโดย

- รวมข้อมูลเศรษฐกิจมหภาคไว้ในระบบเดียว
- ลดความซับซ้อนในการติดตามตัวชี้วัดหลายแหล่ง
- ช่วยให้ผู้ใช้งานมองเห็นภาพรวมของความเสี่ยงเชิงระบบ
- สนับสนุนการตัดสินใจด้วยข้อมูลที่อธิบายเหตุผลได้

# Assumptions

Version 1.0 ใช้สมมติฐานดังนี้

- Macro Data Update วันละ 1 ครั้ง
- ใช้ข้อมูลจากแหล่งข้อมูลที่เชื่อถือได้
- ไม่ใช้ AI Prediction
- ไม่ใช้ Machine Learning
- ไม่ทำ Automated Trading

# Document Information

| รายการ        | รายละเอียด                   |
| ------------- | ---------------------------- |
| Document Name | Business Project Charter     |
| Document ID   | BIZ-001                      |
| Version       | 1.0                          |
| Status        | DRAFT                        |
| Owner         | Jirasak KK                   |
| Reviewer      | ChatGPT                      |
| Layer         | Business                     |
| Depends On    | -                            |
| Referenced By | Macro Framework, Risk Engine |
| Last Updated  | 2026-06-26                   |

---

# 1. Background

ในสภาวะเศรษฐกิจโลกปัจจุบัน ความเสี่ยงเชิงระบบ (Systemic Risk) มีความซับซ้อนมากขึ้นจากหลายปัจจัย เช่น

* หนี้สาธารณะ (Public Debt)
* การขาดดุลงบประมาณ (Fiscal Deficit)
* นโยบายการเงินของธนาคารกลาง
* ความตึงตัวของสภาพคล่อง
* ตลาดพันธบัตร
* ความขัดแย้งทางภูมิรัฐศาสตร์
* เงินเฟ้อ
* Capital Flow ระหว่างสินทรัพย์

ข้อมูลเหล่านี้มักถูกวิเคราะห์แยกกัน ทำให้มองภาพรวมของระบบเศรษฐกิจได้ยาก

Macro Risk Engine ถูกออกแบบขึ้นเพื่อรวมข้อมูลเหล่านี้เข้าสู่กรอบการวิเคราะห์เดียวกัน

---

# 2. Problem Statement

ปัจจุบันนักลงทุนและผู้วิเคราะห์ต้องติดตามข้อมูลจากหลายแหล่ง เช่น

* SOFR
* DXY
* US Treasury Yield
* Gold
* Treasury Auction
* Credit Spread
* VIX
* Fiscal Data

แต่ยังไม่มีระบบที่สามารถอธิบายว่า

* ความเสี่ยงกำลังเพิ่มขึ้นหรือไม่
* ความเสี่ยงเริ่มต้นจากส่วนใดของระบบ
* ความเสียหายอยู่ในขั้นตอนไหน
* ระบบกำลังเข้าสู่ภาวะ Deleveraging หรือไม่

---

# 3. Vision

สร้างระบบ Early Warning System สำหรับวิเคราะห์ความเสี่ยงเศรษฐกิจมหภาคที่

* โปร่งใส
* อธิบายเหตุผลได้
* ตรวจสอบย้อนกลับได้
* ขยายต่อได้ในอนาคต

---

# 4. Mission

Macro Risk Engine มีภารกิจหลักดังนี้

1. รวบรวมข้อมูลเศรษฐกิจมหภาคที่สำคัญ
2. วิเคราะห์ความสัมพันธ์ของ Liquidity, Debt และ Market Stress
3. คำนวณ Risk Score ของระบบ
4. จัดประเภท Risk State
5. แจ้งเตือนเมื่อเกิดเหตุการณ์สำคัญ
6. สนับสนุนการตัดสินใจเชิงกลยุทธ์

---

# 5. Business Objectives

Version 1.0 ต้องสามารถ

* วิเคราะห์ Risk Score ของระบบ
* วิเคราะห์ Risk State
* ตรวจจับ Golden Signal
* ตรวจจับ Liquidity Stress
* ตรวจจับ Debt Stress
* สร้าง Alert
* แสดง Dashboard
* เก็บข้อมูลย้อนหลัง

---

# 6. Target Users

ผู้ใช้งานหลัก

* นักลงทุนระยะยาว
* นักวิเคราะห์เศรษฐกิจ
* นักวิจัย
* ผู้จัดการพอร์ต
* ผู้สนใจเศรษฐกิจมหภาค

---

# 7. Project Scope

Version 1.0 ครอบคลุม

* Daily Data Collection
* Indicator Monitoring
* Risk Score Engine
* Risk State Classification
* Alert System
* Historical Analysis
* Dashboard

---

# 8. Out of Scope

Version 1.0 ยังไม่ครอบคลุม

* Algorithmic Trading
* Price Prediction
* Machine Learning
* High Frequency Trading
* Portfolio Optimization
* Realtime Streaming

---

# 9. Core Principles

Macro Risk Engine ยึดหลักการดังต่อไปนี้

## 9.1 Documentation First

Business มาก่อน Code

---

## 9.2 Explainable

ทุก Risk Score ต้องอธิบายที่มาได้

---

## 9.3 Evidence-Based

ทุก Alert ต้องอ้างอิงข้อมูลจริง

---

## 9.4 Layer-Based Analysis

วิเคราะห์ปัญหาเป็นลำดับชั้น

Cause → Stress → Accelerator → Confirmation → Damage → Deleveraging

---

## 9.5 Configurable

Threshold และ Weight ต้องสามารถปรับได้โดยไม่แก้ Business Logic

---

## 9.6 Technology Independent

Business Logic ต้องไม่ผูกกับ Framework หรือ Library ใด

---

# 10. Success Criteria

โครงการถือว่าประสบความสำเร็จเมื่อสามารถตอบคำถามได้ทุกวันว่า

* วันนี้ระบบอยู่ใน Risk State ใด
* Risk Score เท่าใด
* Layer ใดกำลังมีความเสี่ยง
* Golden Signal เกิดขึ้นหรือไม่
* Liquidity กำลังตึงตัวหรือไม่
* ระบบกำลังเข้าสู่ Deleveraging หรือไม่

---

# 11. Future Vision

Macro Risk Engine ถูกออกแบบให้สามารถต่อยอดสู่

* Multi-Country Analysis
* Scenario Analysis
* Stress Testing
* Portfolio Overlay
* AI Assisted Decision Support
* Backtesting

โดยไม่ต้องเปลี่ยน Business Architecture

---

# 12. Dependencies

เอกสารฉบับนี้เป็นพื้นฐานของ

* docs/business/02-macro-framework.md
* docs/business/03-risk-engine.md
* docs/business/04-indicators.md
* docs/business/05-alert-rules.md

---

# 13. Review Checklist

* [ ] Vision ชัดเจน
* [ ] Mission ครบถ้วน
* [ ] Scope ถูกต้อง
* [ ] Out of Scope ชัดเจน
* [ ] Business Objective ครบ
* [ ] Success Criteria วัดผลได้

---

# Document Status

| รายการ        | ค่า                                  |
| ------------- | ----------------------------------- |
| Version       | 1.0                                 |
| Status        | APPROVED                            |
| Review        | PASS                                |
| Next Step     | Business Review                     |
| Next Document | docs/business/02-macro-framework.md |
