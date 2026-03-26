# IEEE Paper Review Skills — คู่มือการใช้งาน

ชุด skill สำหรับตรวจและปรับปรุงงานวิจัย IEEE ครบ 17 skills ครอบคลุมทุก section ของ paper

---

## วิธีใช้

```
/ชื่อ-skill
```
แล้ว paste ข้อความของ section ที่ต้องการตรวจ หรือใช้แบบ inline:
```
/ชื่อ-skill [วาง text ที่นี่]
```

---

## ตรวจทั้งเปเปอร์

| Skill | คำสั่ง | ทำอะไร |
|-------|--------|--------|
| **ตรวจเปเปอร์ทั้งฉบับ** | `/ieee-reviewer` | ให้คะแนนครบทั้ง 8 เกณฑ์ IEEE (novelty, technical soundness, evaluation, clarity, organization, reproducibility, figures, related work) รวม /100 พร้อมประมาณ acceptance probability, จุดแข็ง, จุดอ่อน, สิ่งที่ต้องแก้ไข |
| **จำลอง 3 Reviewer** | `/ieee-panel-review` | จำลอง reviewer 3 คน: Strict (A), Moderate (B), Positive (C) แต่ละคนให้คะแนนแยกกัน จากนั้นมีการ simulate การประชุม PC เพื่อสรุป final decision, acceptance probability และ action plan ระบุ acceptance rate ของ conference ได้ เช่น 25% |

---

## ตรวจรายส่วน (Section Reviews)

| Section | คำสั่ง | ตรวจอะไร | ผลลัพธ์หลัก |
|---------|--------|----------|------------|
| **Abstract** | `/ieee-abstract-reviewer` | จำนวนคำ (เป้า 150–250), ความชัดเจนของ problem, สรุป method, ผลลัพธ์มีตัวเลข, contribution statement, ตรงมาตรฐาน IEEE (ไม่มี citation, ไม่มี background ฟุ่มเฟือย) | คะแนน /100 · ปัญหาที่พบ · เขียนใหม่ทั้ง abstract |
| **Introduction** | `/ieee-intro-reviewer` | Background & context, problem statement, research gap, รายการ contribution, roadmap ของ paper, โครงสร้าง funnel (broad → narrow → gap → solution) | คะแนน /100 · ปัญหาที่พบ · เขียนใหม่ problem statement + contributions |
| **Background** | `/ieee-background-reviewer` | อธิบาย domain, ความเกี่ยวข้องกับ research problem, ความถูกต้องเชิงเทคนิค, ความลึกที่เหมาะสม (ไม่ตื้นหรือยาวเกินไป), logical flow, tone เชิงวิชาการ, การใช้ citation | คะแนน /100 · ปัญหาที่พบ · เขียนใหม่ paragraph ที่อ่อนที่สุด |
| **Related Work** | `/ieee-related-work-reviewer` | ครอบคลุมงานก่อนหน้า, จัดหมวดหมู่งาน (ไม่ใช่แค่ list), ความลึกของการเปรียบเทียบ (ไม่ใช่แค่อธิบาย), การระบุ gap, การ position งานนี้เทียบกับงานก่อน, รูปแบบ citation | คะแนน /100 · ปัญหาที่พบ · เขียนใหม่ paragraph ที่อ่อนสุด พร้อม comparison + gap |
| **Methodology** | `/ieee-methodology-reviewer` | ความชัดเจนของ approach, ลำดับขั้นตอน, ความถูกต้องเชิงเทคนิค, ความครบถ้วน (กำหนด input/output), reproducibility (ระบุ tools/params), การเชื่อมต่อระหว่าง components, การอ้างอิง figure | คะแนน /100 · ปัญหาที่พบ · เขียนใหม่ paragraph ที่อ่อนสุด พร้อม `[specify: ...]` |
| **Evaluation** | `/ieee-evaluation-reviewer` | การออกแบบ experiment, metrics (มี formula หรือนิยาม), การเปรียบเทียบกับ baseline, คำอธิบาย dataset, การนำเสนอผล (ตาราง/รูป), การวิเคราะห์เชิงลึก (ไม่ใช่แค่รายงานตัวเลข), limitations, reproducibility | คะแนน /100 · ปัญหาที่พบ · เขียนใหม่ passage ที่อ่อนสุด |
| **Threats to Validity** | `/ieee-validity-reviewer` | ครอบคลุมทั้ง 4 ประเภท: Internal / External / Construct / Conclusion validity, ความเฉพาะเจาะจง, mitigation strategies, ความสมดุล (ยอมรับ limitation โดยไม่ทำลายงานตัวเอง) | คะแนน /100 · ตาราง coverage · เขียนใหม่ threat ที่อ่อนสุด ด้วยโครงสร้าง 4 ส่วน |
| **Conclusion** | `/ieee-conclusion-reviewer` | สรุปงานที่ทำ, สะท้อน key results (มีตัวเลข), ย้ำ contributions, ไม่มีข้อมูลใหม่, future work (เฉพาะเจาะจงและเป็นไปได้), ความกระชับและชัดเจน | คะแนน /100 · ปัญหาที่พบ · เขียนใหม่ทั้ง conclusion |
| **References** | `/ieee-bibliography-reviewer` | **2 คะแนนแยกกัน**: (1) รูปแบบ bibliography — IEEE style, consistency, ความครบถ้วน, coverage; (2) การใช้ citation — citation ที่ใส่ support claim จริงหรือเปล่า ตรวจ overclaim, citation ผิดที่, claims ที่ไม่มีหลักฐาน | Format /100 · Usage /100 · ตัวอย่าง before/after |

---

## ตรวจข้ามส่วน (Cross-Section Checks)

| ตรวจเรื่อง | คำสั่ง | ตรวจอะไร | ผลลัพธ์หลัก |
|-----------|--------|----------|------------|
| **Contributions** | `/ieee-contribution-reviewer` | ดึง contribution ที่ระบุและที่แฝงอยู่ ประเมินแต่ละข้อด้านความชัดเจน, specificity, novelty, impact ตรวจ: vague generics, ไม่มีการวัด, contributions ซ้ำกัน, scope ไม่ตรงกับผล | คะแนน /100 · ปัญหา · เขียนใหม่เป็น numbered list แบบ IEEE |
| **Research Gap** | `/ieee-gap-reviewer` | ดึง gap ที่ระบุหรือแฝงอยู่ ประเมิน: ความชัดเจน, หลักฐาน (cite หรือแค่อ้าง?), specificity, significance **Alignment check**: approach ตอบ gap จริงหรือเปล่า? (Full Match / Partial / Mismatch) | คะแนน /100 · Alignment verdict · เขียนใหม่ด้วยโครงสร้าง 4 ส่วน |
| **Claim Validation** | `/ieee-claim-validator` | ดึง claims ทุกประเภท (performance, comparison, effectiveness, novelty, generalization) แต่ละ claim: ตรวจหลักฐาน, ตรวจ overclaim, vague metrics ("significant"), scope inflation, เปรียบเทียบโดยไม่มี baseline | Reliability /100 · ตาราง alignment ต่อ claim · เขียนใหม่แบบ calibrated |
| **Terminology** | `/ieee-terminology-reviewer` | ดึง key terms ตรวจ: synonym ที่ใช้แทนกัน ("test case" vs "test scenario"), semantic drift (คำเดิมแต่ความหมายต่างกันข้ามส่วน), abbreviation ที่ inconsistent | Consistency /100 · Term glossary · ปัญหาพร้อม severity · คำแนะนำมาตรฐาน |
| **Figures & Diagrams** | `/ieee-figure-reviewer` | ทุก figure: referenced ใน text ไหม?, caption ครบสมบูรณ์ในตัวเองหรือเปล่า?, text ตรงกับ diagram ไหม?, ครอบคลุมทุก component ไหม?, terminology บน diagram ตรงกับ text ไหม?, ลำดับขั้นตอนถูกต้องไหม? | Consistency /100 · ตาราง alignment ต่อ figure · เขียนใหม่ captions |
| **AI Writing Detection** | `/ieee-ai-writing-detector` | ตรวจ 6 pattern ของ AI writing: (A) generic/content-free, (B) vague overclaim, (C) rhythmic repetition, (D) hollow hedging, (E) ขาด specificity, (F) throat-clearing filler ตรวจเฉพาะประโยคที่มีปัญหาจริงเท่านั้น | Writing authenticity /100 · ปัญหาแบบ numbered พร้อมเขียนใหม่ต่อประโยค |

---

## เกณฑ์คะแนน

ทุก skill ใช้มาตรฐานเดียวกัน:

| คะแนน | ความหมาย |
|-------|----------|
| 85–100 | แข็งแกร่ง — พร้อม submit |
| 70–84 | ต้องแก้ไขเล็กน้อย |
| 55–69 | ต้องแก้ไขปานกลาง |
| 40–54 | ต้องแก้ไขมาก |
| < 40 | ต้องเขียนใหม่ |

---

## Recommended Workflow

### ก่อน submit ครั้งแรก
1. `/ieee-contribution-reviewer` — กำหนด contributions ให้ชัดก่อนเป็นอันดับแรก
2. `/ieee-gap-reviewer` — ตรวจว่า gap ตรงกับ approach ที่เสนอ
3. `/ieee-abstract-reviewer` — ขัด abstract ให้กระชับและแข็งแกร่ง
4. `/ieee-ai-writing-detector` — รันบนทุก section
5. `/ieee-terminology-reviewer` — paste ทุก section รวมกัน
6. `/ieee-claim-validator` — ตรวจ results และ conclusion
7. `/ieee-bibliography-reviewer` — paste references + paragraph ที่มี citation
8. `/ieee-reviewer` — ตรวจเปเปอร์ทั้งฉบับสุดท้าย

### ก่อน resubmit หลังโดนปฏิเสธ
1. `/ieee-panel-review` — จำลอง reviewer disagreement เพื่อดูจุดที่ถกเถียง
2. ตรวจเฉพาะ section ที่ reviewer ระบุว่าอ่อน
3. `/ieee-validity-reviewer` — มักถูก flag บ่อยใน empirical papers
4. `/ieee-evaluation-reviewer` — สาเหตุที่พบบ่อยที่สุดของการถูกปฏิเสธ

### ตรวจ section เดี่ยวหลังแก้ไข
รัน skill ที่ตรงกับ section ที่เพิ่งแก้ไป

---

## หมายเหตุ

- Skills เก็บไว้ที่: `~/.claude/skills/`
- ใช้ได้กับทุก project (global)
- การเขียนใหม่ใช้ `[specify: ...]` และ `[cite]` เป็น placeholder — ผู้เขียนต้องเติมค่าจริงเอง
- ไม่มี skill ใดที่สร้างผลลัพธ์, citation, หรือข้อมูลเทคนิคขึ้นมาเอง
