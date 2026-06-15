# Prompt: Git 0 → Hero Handbook (HTML เดียวจบ)

> **โฟลเดอร์นี้มีอะไร**
> - `index.html` — เอกสารที่สร้างเสร็จแล้วตาม prompt ด้านล่าง ใช้เป็น "ตัวอย่างผลลัพธ์ที่ดี" อ้างอิงได้
> - `PROMPT.md` (ไฟล์นี้) — สเปกสำหรับสั่งสร้างใหม่ หรือดัดแปลงไปทำหัวข้ออื่น
>
> ถ้าจะทำหัวข้ออื่น (Docker / SQL / Linux ฯลฯ): เปลี่ยนคำว่า "Git" บรรทัดแรก แล้วปรับรายชื่อบทในส่วนโครงหลักสูตร ที่เหลือคงเดิมได้

---

สร้างเอกสารสอน Git ฉบับ "0 to Hero" เป็นไฟล์ HTML เดียวจบ (self-contained) ภาษาไทย
สไตล์ตำราเทคนิคที่จัดพิมพ์สวย — ไม่ใช่หน้าเว็บ generic ของ AI

## กลุ่มเป้าหมาย & โทน
- เริ่มจากคนไม่เคยแตะ Git → จนเข้าใจกลไกการทำงานภายในระดับลึก
- เน้นแบบจำลองความคิด (mental model) และ "ทำไม" ไม่ใช่ท่องคำสั่ง
- ภาษาไทยที่อ่านลื่น กระชับแต่คมในความหมาย ไม่แปลสำนวนอังกฤษตรงตัว

## โครงหลักสูตร — 14 บท เรียง 5 ระดับ (แต่ละบทติดป้ายระดับ ไล่เฉดสีจากเย็นไปร้อนตามความยาก)
- **LEVEL 0 · ปูพื้น** — 1) Git คืออะไร+ติดตั้ง  2) แบบจำลองความคิดหลัก (snapshot ไม่ใช่ diff, สามพื้นที่ working/staging/repo, SHA)
- **LEVEL 1 · พื้นฐาน** — 3) Workflow ประจำวัน (status/add/commit/log/.gitignore)  4) Branch & Merge (branch=ป้ายชี้, HEAD, fast-forward vs merge commit)  5) Remote (clone/origin/fetch vs pull/push)
- **LEVEL 2 · กลาง** — 6) ย้อนกลับ&กู้คืน (restore/reset soft-mixed-hard/revert/reflog)  7) Merge vs Rebase + interactive rebase + กฎทองห้าม rebase ของที่แชร์แล้ว  8) Stash/Cherry-pick/Tag
- **LEVEL 3 · สูง** — 9) ทำงานเป็นทีม (PR, แก้ conflict, Git Flow vs Trunk-based, Conventional Commits)  10) เครื่องมือสืบสวน (bisect/blame/log -S,--grep,A..B)
- **LEVEL 4 · เทพ** — 11) กลไกภายในของ Git (.git, 4 objects: blob/tree/commit/tag, content-addressable — ใช้ไขว่าทำไม commit แก้ไม่ได้และ branch ถึงเบา)  12) เครื่องมือทรงพลัง (worktree/hooks/submodule vs subtree/rerere)  13) กู้ของหาย&ซ่อมประวัติ (reflog recovery, filter-repo, เมื่อไหร่ rewrite ได้/ห้าม)  14) Repo ใหญ่ + บทสรุปทั้งเล่ม

## ไดอะแกรม (สำคัญสุด — วาด inline SVG เองทุกภาพ ไม่ใช่รูป external)
อย่างน้อยบทละ 1 ภาพในบทแนวคิด ที่ต้องมี: สามพื้นที่ของ Git, commit graph (วงกลม+เส้น+ป้าย branch+HEAD),
fast-forward vs merge commit, merge vs rebase, fetch vs pull, โครงสร้าง object (commit→tree→blob)
- ทุก `<svg>` ใส่ `role="img"` + `aria-label` สรุปภาพหนึ่งประโยค
- มือถือ: figure เลื่อนแนวนอนได้ (`overflow-x:auto`) + svg `min-width` ~600px กันตัวอักษรเล็กจนอ่านไม่ออก

## ดีไซน์ (เลี่ยง AI slop)
- พื้นกระดาษอุ่น `#faf7f1` + หมึกเข้ม + teal สีหลัก + amber accent — ห้าม dark mode+neon, ห้าม gradient text
- ฟอนต์ Google Fonts: หัวเรื่อง Bai Jamjuree, เนื้อความ Anuphan, โค้ด IBM Plex Mono
- code block สไตล์ terminal พื้นเข้ม + syntax highlight ด้วย `<span>` สี (คำสั่ง/comment/argument/output/prompt $)
- ป้ายระดับเป็น chip 5 สีไล่เฉด โชว์ใต้ชื่อบท + จัดกลุ่มสารบัญตามระดับ
- callout 3 สี: note=teal, warn=แดง, เคล็ดลับ=amber · ตารางหัวเข้ม · spacing มีจังหวะ

## เทคนิค
- ไฟล์ HTML เดียว ทุก CSS/JS ฝังในไฟล์ (ฟอนต์โหลด Google Fonts ได้)
- Sidebar สารบัญ sticky + scrollspy (ไฮไลต์บทที่อ่านอยู่) จัดกลุ่ม 5 ระดับ + ยุบได้บนมือถือ
- แถบ reading progress ด้านบน
- `@media print`: ซ่อน sidebar/progress, ไดอะแกรม/ตาราง/โค้ด `break-inside:avoid`
- ตั้งชื่อไฟล์ `index.html` (เผื่อขึ้น GitHub Pages ได้ทันที)

## เกณฑ์คุณภาพ
- ทุกคำสั่งและพฤติกรรม Git ถูกต้องจริง โดยเฉพาะ reset/rebase/reflog/internals ที่พลาดง่าย
- ผ่าน "AI slop test": ดูแล้วไม่เดาออกทันทีว่า AI ทำ
- ทุกบทจบด้วยกล่องสรุปสั้น ๆ ที่ทวนก่อนสอบ/สัมภาษณ์ได้
- บทที่ 11 ต้องลึกพอให้เข้าใจว่าทำไม commit ถึง immutable และ branch ถึงราคาถูก
- ก่อนส่ง: เปิด preview ตรวจไดอะแกรมไม่ล้นกรอบ, วรรณยุกต์ไทยถูก, มือถือไม่มี scroll หลุด
